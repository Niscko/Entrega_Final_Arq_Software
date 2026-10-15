# CampoAlto — mantenimiento de la flota

Diseño de la arquitectura de la aplicación de mantenimiento de CampoAlto S.A.S. El taller está en Palmira desde 2021. Fumiga caña en el Valle y arroz en Tolima. La flota es propia: 16 Agras T50 y 8 Agras T40. El cliente paga la hectárea. No contrata el mantenimiento y no se reparan drones ajenos.

Integrantes: Nicolás Agudelo, Nicolás Buitrago, Esteban Alvarez, Sebastian Bedoya. El diseño no está partido por persona. Cualquiera de los cuatro tiene que poder explicar la entrevista, cada vista y el porqué de lo que quedó fuera.

El modelo se abre en Archi con **Archivo → Abrir** sobre [modelo/CampoAlto-Mantenimiento.archimate](modelo/CampoAlto-Mantenimiento.archimate). Las vistas están dentro del modelo. Las imágenes de este documento están en [vistas](vistas).

La decisión que no puede fallar es soltar el vuelo. Motor, bomba, batería y electrónica no salen porque el técnico firmó, porque el lote ya está prometido o porque el piloto quiere terminar. Si el jefe no da el visto bueno, el dron se queda en tierra.

## Índice

1. [Contexto y entrevista](#1-contexto-y-entrevista)
2. [Motivación](#2-motivacion)
   - [V1 Motivación](#v1-motivacion)
3. [Mapa de capacidades y proceso E2E](#3-mapa-de-capacidades-y-proceso-e2e)
   - [V2 Mapa de capacidades](#v2-mapa-de-capacidades)
   - [V3 Cadena de valor y proceso E2E](#v3-cadena-de-valor-y-proceso-e2e)
4. [Descomposición de servicios](#4-descomposicion-de-servicios)
   - [V4 Descomposición de servicios](#v4-descomposicion-de-servicios)
   - [V4b Contratos](#v4b-contratos)
5. [Dominios y lenguaje ubicuo](#5-dominios-y-lenguaje-ubicuo)
   - [V5 Dominios](#v5-dominios)
   - [V7 Lenguaje ubicuo](#v7-lenguaje-ubicuo)
6. [Agregados, comandos y eventos](#6-agregados-comandos-y-eventos)
   - [V6a Disponibilidad del dron](#v6a-disponibilidad-del-dron)
   - [V6b Orden de trabajo](#v6b-orden-de-trabajo)
   - [V6c Horas](#v6c-horas)
   - [V6d Batería](#v6d-bateria)
   - [V6e Indicador del día](#v6e-indicador-del-dia)
   - [V6f Retención](#v6f-retencion)
   - [V6g Pedido](#v6g-pedido)
7. [Mapa de contextos e interoperabilidad](#7-mapa-de-contextos-e-interoperabilidad)
   - [V8 Mapa de contextos](#v8-mapa-de-contextos)
   - [V9 Interoperabilidad y anticorrupción](#v9-interoperabilidad-y-anticorrupcion)
8. [Bounded Context Canvas](#8-bounded-context-canvas)
   - [V11 Canvas](#v11-canvas)
9. [Decisiones y supuestos](#9-decisiones-y-supuestos)
   - [V10 Trazabilidad vertical](#v10-trazabilidad-vertical)
   - [Aportes](#aportes)

<a id="1-contexto-y-entrevista"></a>

## 1. Contexto y entrevista

El guion, la instrucción de rol, la conversación y el análisis de hallazgos están en [entrevista](entrevista).

| Pieza | Archivo |
|---|---|
| Instrucción de rol | [entrevista/instruccion-de-rol.md](entrevista/instruccion-de-rol.md) |
| Guion, con el bloque de interoperabilidad | [entrevista/guion.md](entrevista/guion.md) |
| Conversación exportada | [entrevista/conversacion.md](entrevista/conversacion.md) |
| Qué se aceptó, qué se descartó y cómo cambió el diseño | [entrevista/analisis.md](entrevista/analisis.md) |

CampoAlto no tiene un sistema de mantenimiento. Lleva las horas en la hoja «Control de flota», la orden en papel, la foto en OneDrive, la novedad en el grupo «Novedades campo» y la lista en el grupo «Programa». La app del Agras es el origen de las horas, el caudal y la alerta de batería. Operaciones mira FlightHub para saber dónde está el equipo. Siigo guarda la factura. El software nuevo no reemplaza ninguno de esos.

Se aceptó diseñar el software del taller alrededor de una sola decisión: soltar el vuelo. Se descartó programar fincas, facturar hectáreas, inventar existencia o costo, hablar con el portal de la Aeronáutica, revisar la dosis del ICA, llevar una habilitación que no existe y publicar un indicador en cero cuando el dato no está. El detalle de cada descarte está en el análisis.

<a id="2-motivacion"></a>

## 2. Motivación

<a id="v1-motivacion"></a>

### V1 Motivación

![V1 Motivación](vistas/V1-motivacion.png)

La vista responde por qué existe la aplicación. Arriba está lo que el jefe usa para decidir si el día salió bien. Abajo están los principios, los requisitos y las restricciones que salieron cuando se le preguntó qué no debe hacer el software.

Cada fila es una cadena corta, para que la relación no cruce el dibujo:

- El jefe y el coordinador empujan la flota lista para mañana. La evaluación es concreta: de 16 disponibles para abajo, con caña y arroz abiertos, se corren lotes. La meta es la lista confiable antes de las 17:00. El resultado es que operaciones programa solo lo que esa lista publicó.
- Pilotos, técnicos y el jefe comparten el impulsor de no soltar un dron inseguro. Seguridad agrega el manual de operaciones. La evaluación de los dos es la misma: cero drones en verde con las 50 h ya vencidas. La meta es la visita de motor y la revisión de 50 h al día.
- El jefe y comercial empujan el otro lado: no volar si falta la pieza. La evaluación es que, sin el dato, el indicador no existe. La meta es publicarlo solo cuando el dato está. El principio «no se publica un indicador en cero» realiza esa misma meta.
- «No salir si falta el repuesto» queda como meta visible. No tiene una flecha propia porque el jefe no la separó de «no volar si falta la pieza»: es la misma regla, dicha para el dron y no para el número.

La segunda mitad baja de principio o restricción a requisito y de ahí a la meta. La firma del técnico no es el visto bueno. El cruce T40/T50 y el dron ajeno tampoco lo son. Los tres apuntan al requisito de los estados: verde, pendiente, condicionado y en OT, y ese requisito realiza la meta del visto bueno. La baja de la batería y el «sin respuesta se queda en tierra» realizan la misma meta, porque las dos son formas de no soltar el vuelo.

Horas y calendario mandan los dos. Ese principio empuja el requisito de no armar jornada con la revisión pendiente, y ese requisito realiza la meta del plan. El portal y el ICA no se consultan: la restricción empuja el freno por boletín o por papeles, que también realiza el plan, porque un papel puede parar el dron antes de las horas. No reemplazar el Agras ni sumar el mensaje del piloto realizan la meta de un solo total de horas. Que el taller no programe ni facture realiza la lista: número, si sale, límite y motivo.

<a id="3-mapa-de-capacidades-y-proceso-e2e"></a>

## 3. Mapa de capacidades y proceso E2E

<a id="v2-mapa-de-capacidades"></a>

### V2 Mapa de capacidades

![V2 Mapa de capacidades](vistas/V2-capacidades.png)

El mapa es el negocio, no solo el taller. Cada capacidad de arriba se descompone hacia abajo. La composición baja por el costado del grupo para no atravesar los cuadros de en medio.

| Capacidad | Marca | Qué hace en CampoAlto |
|---|---|---|
| Comercializar la fumigación | Fuera | El cliente paga la hectárea. El mantenimiento no va en esa factura |
| Programar la operación | Colinda | El coordinador arma finca, piloto y dron. Recibir la lista sí colinda con el taller |
| Ejecutar la fumigación | Colinda | El vuelo es de operaciones. El pre-vuelo queda fuera de este proceso. Reportar la novedad sí entra al taller |
| Mantener la flota para salir | Entra | Horas, intervención, soltar el vuelo y publicar la lista |
| Abastecer el repuesto | Colinda | Pedir por nombre y modelo entra. La existencia y la factura de Siigo quedan fuera |
| Sostener el permiso de volar | Colinda | Registro y póliza los lleva seguridad. Frenar si seguridad avisa sí entra. La dosis y el ICA están al lado y no componen esta capacidad |

Los recursos y los cursos de acción se dibujaron al lado de la capacidad que alimentan, no en una fila suelta al otro extremo del mapa. La flota y las bases se asignan a mantener la flota. La app del Agras y la estantería se asignan a llevar las horas, porque de ahí sale la cifra y porque la existencia se ve, no se consulta. El visto bueno del jefe realiza soltar el vuelo. «200 h o seis meses, lo que ocurra primero» realiza la intervención. Dejar el indicador en blanco si falta el dato realiza publicar la lista.

<a id="v3-cadena-de-valor-y-proceso-e2e"></a>

### V3 Cadena de valor y proceso E2E

![V3 Cadena de valor y proceso E2E](vistas/V3-proceso.png)

El flujo de valor es devolver el dron a disponible. Se parte en cuatro etapas, alineadas con el proceso de abajo: regreso a la base, horas y decisión, intervención y visto bueno, lista antes de las cinco.

El camino de la tarde es una fila: recibir el dron, anotar un solo total de horas, decidir verde u orden, intervenir, cerrar el trabajo del técnico, dar el visto bueno y publicar la lista. De decidir a publicar hay un atajo por debajo de la fila. Es el día limpio: no hubo síntoma y no se cumplieron las 50 h, así que no se abre orden. El atajo no pasa por encima de los eventos.

Cada evento queda debajo del paso que dispara. La jornada cerrada abre la recepción. El síntoma o el daño, y el pre-vuelo fallido, vuelven a la decisión. Las 50 h, las 200 h o los seis meses abren la intervención. El boletín abre la retención. Publicar la lista produce el evento de lista publicada.

El pre-vuelo y la asignación de la finca están en otra fila, abajo. No son pasos de dejar el dron disponible. El piloto hace el pre-vuelo. El coordinador asigna la finca. El técnico de línea recibe e interviene. El jefe da el visto bueno y publica. Seguridad retiene. Esos actores no se apilan en una columna a la izquierda, porque desde ahí todas las flechas cruzaban el proceso.

Cerrar el trabajo y soltar el vuelo siguen siendo dos pasos. En hélice, boquilla, filtro y lavado el de línea cierra y puede dejar el verde. Si hubo golpe, antes va el minuto estacionario sin producto. En motor, bomba, batería y electrónica el cierre deja el dron pendiente hasta el visto bueno.

<a id="4-descomposicion-de-servicios"></a>

## 4. Descomposición de servicios

El proceso E2E se bajó en cinco capas. El enunciado pide al menos cuatro. La quinta es la anticorrupción, porque sin ella el taller volvería a copiar a mano lo que ya vive en otro sistema.

| Capa | Servicios | Por qué ese corte |
|---|---|---|
| Proceso | Cerrar la jornada. Publicar disponibilidad | Son los dos resultados del día. El primero deja el dron listo o en orden. El segundo le dice a operaciones quién entra mañana |
| Tarea | Registrar las horas. Llevar la orden. Cumplir 50 h y visita de motor. Emitir el visto bueno. Retener el dron. Decidir la baja de la batería | Cada uno es un trabajo que hoy hace una persona y que el software tiene que sostener sin juntarlos |
| Entidad | Dron y despiece. Orden de trabajo. Lista del día | Son los tres papeles que el jefe reconoce. El despiece no es un cuarto papel: vive con el dron y con la orden |
| Utilidad | No publicar cero. Reloj de horas y de seis meses | No son un proceso del taller. Son reglas que varios servicios consultan para no mentir el número ni dejar pasar la fecha |
| Anticorrupción | Traducir la lectura del Agras. Entregar la lista a operaciones. Pedir pieza por nombre y modelo. Recibir freno de seguridad o boletín | Traducen el dato de afuera al idioma del taller, y el dato del taller al idioma de afuera. No copian el sistema vecino |

Hélice, boquilla, filtro y lavado los cierra el técnico de línea y él mismo puede dejar el dron en verde. Motor, bomba, batería y electrónica quedan pendientes hasta el visto bueno. Esa diferencia no abre otro servicio: es una regla del servicio de visto bueno.

<a id="v4-descomposicion-de-servicios"></a>

### V4 Descomposición de servicios

![V4 Descomposición de servicios](vistas/V4-servicios.png)

Arriba, de izquierda a derecha, están las cinco capas con el elemento de servicio de negocio. Abajo están los servicios que la entrevista dejó fuera. No tienen flecha hacia los de arriba a propósito: dibujar una relación de «no se implementa» ensuciaba la vista y parecía un flujo. La nota de la vista lo dice. La justificación de cada exclusión está en la tabla.

| No se implementa | Por qué |
|---|---|
| Programar la finca | Lo hace el coordinador. A él le basta número, si sale y el límite |
| Facturar hectáreas | Comercial, en Siigo, después del vuelo. La factura no suelta el dron |
| Consultar FlightHub | Operaciones mira la ubicación. El taller no lo usa para horas ni disponibilidad |
| Radicar en el portal | Cerrar la orden no radica nada. Lo arma seguridad, aparte |
| Revisar dosis e ICA | La dosis la pone el agrónomo. No entra al verde |
| Consultar habilitación | No existe ese registro. El alcance es el puesto |
| Existencia automática | Se ve en la estantería o la dice la base. Siigo no la devuelve |
| Actualizar firmware | Lo hace el técnico si el jefe lo autorizó. El software no lo instala |
| Abrir la garantía | El preventivo no abre ese trámite. El trámite no suelta el vuelo |
| Baja automática de batería | A los 500 ciclos se propone. La baja la firma el jefe |
| Cruzar pieza T40/T50 | El repuesto no se cruza. El T50 no sale con una sola bomba |
| Hacer el pre-vuelo | Es de la madrugada, ya asignado. Si falla lo crítico, el dron vuelve a orden |

Los actores, el proceso y los eventos no se repiten en esta vista. Están en V3. Aquí el corte es el servicio.

<a id="v4b-contratos"></a>

### V4b Contratos

![V4b Contratos](vistas/V4b-contratos.png)

Cada servicio que sí entra tiene un contrato, elemento pasivo de negocio, al lado. La asociación es el contrato de ese servicio. No se contrató lo que quedó fuera: no hay contrato de FlightHub, de portal ni de habilitación.

El contrato no es una API inventada. Es el dato que el jefe ya intercambia, escrito antes de construir la aplicación.

| Servicio | Entra | Sale |
|---|---|---|
| Cierre de jornada | Número, horas de la pantalla o de la hoja ya corregida, síntoma y foto si hay | Verde o en OT |
| Publicar disponibilidad | Quién puede entrar mañana | Número, si sale, límite o motivo. Nada después de las cinco se mete solo al programa de esa madrugada |
| Registrar las horas | Pantalla, app o mensaje | Un solo total. El mensaje no se suma |
| Llevar la orden | Hallazgo, serial, motivo de entrada | La misma orden. Sin papel ni foto el servicio se vuelve a hacer |
| Plan de 50 h y de motor | Horas y fecha de la última visita | Entra al cerrar la jornada. Gana lo que se cumpla primero |
| Visto bueno | Cierre de motor, bomba, batería o electrónica | Verde, condicionado con límite, o se queda |
| Retener | Mensaje de seguridad o boletín con serial | Frenado. No hay radicación |
| Baja de batería | Alerta, hinchazón o ciclos | La baja firmada, o la propuesta que el jefe todavía no firmó |
| Dron y despiece | Número, modelo, serial | Ninguna pieza del otro modelo |
| Orden de trabajo | Líneas, seriales, horas | Un papel |
| Lista del día | El corte de las cinco | Lo que operaciones puede leer |
| No publicar cero | Costo o conteo de fallas, si existen | Vacío si no existen. Nunca cero |
| Reloj | Horas y fecha | 50 h, 200 h o seis meses |
| Lectura del Agras | Horas, caudal, alerta, ciclos | La cifra ya reconciliada. La telemetría no entra sola |
| Lista hacia operaciones | La lista | Número, si sale, límite, motivo. Sin despiece y sin póliza |
| Pedido | Nombre y modelo | Aviso de llegada, si alguien avisa. El costo solo si administración lo pasa |
| Freno | «Este dron no sale» o el boletín | Se obedece. No se reinterpreta |

<a id="5-dominios-y-lenguaje-ubicuo"></a>

## 5. Dominios y lenguaje ubicuo

Los dominios no se cortaron por pieza. Se cortaron por la decisión. El jefe tiene varios oficios en el mismo día, pero solo uno no puede fallar.

<a id="v5-dominios"></a>

### V5 Dominios

![V5 Dominios](vistas/V5-dominios.png)

Los contextos son componentes de aplicación. La flecha dice qué le entrega cada uno al central. Indicadores, pedido y Siigo están en la vista y no tienen flecha: alimentan otras decisiones y no ponen el verde.

| Dominio | Clase | Argumento |
|---|---|---|
| Soltar el vuelo | Central | Es la decisión que no puede fallar aunque fallen la foto, el costo o el papel que se quedó en Espinal |
| Intervención y orden | Soporte | Cierra el trabajo. Entrega el cierre, sin verde. No pone el verde crítico |
| Horas de vuelo | Soporte | Entrega un solo total. No decide si el dron sale |
| Baterías | Soporte | Entrega que hay dos sanas del modelo. La baja la firma el jefe, dentro de soltar el vuelo |
| Indicadores del día | Soporte | Mira el resultado. No suelta el vuelo |
| Retención y expediente | Soporte | Entrega el freno. No negocia el mensaje |
| Pedido de repuesto | Soporte | Si la pieza no llegó, el central no suelta. El pedido no marca el verde |
| Identidad T40/T50 | Genérico | Número, modelo y serial. Lo usan el central y la orden para que no se cruce pieza |
| Siigo | Genérico y externo | Factura y, si la piden, el costo. No devuelve existencia |

<a id="v7-lenguaje-ubicuo"></a>

### V7 Lenguaje ubicuo

![V7 Lenguaje ubicuo](vistas/V7-lenguaje.png)

Cada fila es la misma palabra en dos oficios. A la izquierda, la representación: cómo se dice en el papel, en el grupo o en la pantalla. A la derecha, el significado que el software va a usar. Cuando la palabra también nombra un objeto del taller, la representación queda asociada a ese objeto en el modelo.

| Se dice | En el taller significa | No significa |
|---|---|---|
| Disponible | Puede entrar al programa de mañana, vuele o sobre en tierra | La ubicación que operaciones ve en FlightHub a mediodía |
| Horas | El total de la hoja, ya reconciliado | El mensaje del piloto sumado otra vez a la app |
| Firma | El técnico terminó esa línea | El visto bueno del jefe |
| Visto bueno | El mensaje del jefe en «Programa» para motor, bomba, batería o electrónica | La firma del papel |
| Preventivo | Orden encabezada «50 h» o «visita de motor», dentro de los límites | Una falla |
| Falla | El hallazgo que retiene el dron dentro de esa misma orden | El preventivo hecho a tiempo |
| Baja | La decide el jefe | La media carga de una batería quieta más de siete días |
| Registro | El de la Aeronáutica, que lleva seguridad | La carpeta física del dron |
| Prometida | El coordinador ya le dijo al cliente que se entra al lote | La factura de hectáreas en Siigo |

<a id="6-agregados-comandos-y-eventos"></a>

## 6. Agregados, comandos y eventos

Hay un agregado por decisión que el software tiene que proteger, no uno por cada pieza del dron. La hélice, la boquilla y el filtro viven como líneas de la orden. El motor, la bomba, la batería y la electrónica cambian quién puede poner el verde, y eso lo protege Disponibilidad, no un agregado por subsistema.

En cada vista V6 la raíz es el objeto de datos. A la izquierda están los conceptos que componen el agregado. A la derecha, el comando (proceso de aplicación) dispara el evento. La invariante está en la documentación del objeto, no en una flecha extra: una flecha no puede decir «esto no puede pasar».

<a id="v6a-disponibilidad-del-dron"></a>

### V6a Disponibilidad del dron

![V6a Disponibilidad del dron](vistas/V6a-disponibilidad.png)

Raíz: disponibilidad del dron. Adentro: estado, horas desde la 50, fecha de visita de motor, baterías sanas del modelo y límite condicionado.

No queda en verde con orden crítica abierta. Con las 50 h cumplidas no hay jornada nueva. Hacen falta dos baterías sanas. Condicionado solo el carenado que no toca hélice ni tanque, y lo escribe el jefe.

| Comando | Evento |
|---|---|
| Recibir cierre de línea | Dron en verde |
| Otorgar visto bueno | Visto bueno otorgado |
| Marcar sale condicionado | Salida condicionada |
| Publicar en la lista | Incluido en la lista |
| Devolver por pre-vuelo | Devuelto a orden |

<a id="v6b-orden-de-trabajo"></a>

### V6b Orden de trabajo

![V6b Orden de trabajo](vistas/V6b-orden.png)

Raíz: la orden. Adentro: la línea de intervención, el serial, el motivo de entrada, las horas anotadas y el par de hélice o boquilla.

Una entrada, un papel. Un solo número de horas. La firma crítica no pone verde. El de línea no firma motor, baja ni electrónica. Canibalizar solo desde un dron que ya está en orden, autorizado por el jefe y anotado en las dos órdenes. Sin papel ni foto, el servicio se vuelve a hacer.

| Comando | Evento |
|---|---|
| Abrir orden | Orden abierta |
| Agregar hallazgo | Hallazgo en la misma orden |
| Firmar línea | Línea firmada |
| Cerrar trabajo crítico | Quedó pendiente de visto bueno |
| Registrar canibalización | Pieza pasada del donante |

<a id="v6c-horas"></a>

### V6c Horas

![V6c Horas](vistas/V6c-horas.png)

Raíz: el total de horas. Adentro: la lectura de pantalla, la lectura de la app y el mensaje del piloto. Los tres entran. Sale uno.

No se suman piloto y app. Diez horas o más por encima: manda la app. App por debajo porque no cerraron la misión: manda la hoja. FlightHub no entra.

| Comando | Evento |
|---|---|
| Registrar la pantalla | Horas fijadas por la pantalla |
| Corregir con la app | Hoja corregida |
| Conservar la hoja | Misión abierta, hoja conservada |
| Descartar el mensaje | Mensaje no sumado |

<a id="v6d-bateria"></a>

### V6d Batería

![V6d Batería](vistas/V6d-bateria.png)

Raíz: la batería. Adentro: modelo, ciclos, alerta o hinchazón.

No se da de baja sola. La del T50 no entra en el T40. Quieta más de siete días, a media carga, no es baja. Pasada de 500 ciclos solo con autorización, sin hinchazón, celdas parejas y lote cerca de carretera, en el pico de arroz.

| Comando | Evento |
|---|---|
| Apartar | Batería apartada |
| Proponer baja | Baja propuesta |
| Dar de baja | Baja decidida por el jefe |
| Autorizar sobre 500 | Excepción de pico de arroz |
| Guardar a media carga | Quedó a media carga |

<a id="v6e-indicador-del-dia"></a>

### V6e Indicador del día

![V6e Indicador del día](vistas/V6e-indicador.png)

Raíz: la observación de las cinco. Adentro: disponibles, lotes corridos por el taller, fallos de pre-vuelo y espera de Bogotá.

Disponible es quien puede entrar mañana, en el aire o sobrando en tierra. No es el mediodía en FlightHub. El preventivo a tiempo no es una falla. Si falta el costo o no se contaron las fallas, no se escribe cero. Pedir el tiempo medio se rechaza: el jefe no lo calcula y un cero diría que no hubo fallas.

| Comando | Evento |
|---|---|
| Cerrar el conteo | Lista del día guardada |
| Anotar lote del taller | Lote corrido contado |
| Pedir el costo | Costo publicado o dejado vacío |
| Pedir el tiempo medio | Tiempo medio rechazado |

<a id="v6f-retencion"></a>

### V6f Retención

![V6f Retención](vistas/V6f-retencion.png)

Raíz: la retención. Adentro: el mensaje de seguridad, el boletín con sus seriales y la carpeta.

El taller no radica y no entra al portal. Un comentario de otro operador no para la flota. Si el boletín dice «en la próxima revisión de 50 h», no se saca el dron antes. Si dice que no vuele hasta cambiar la pieza, se frena ese día. Si no hay papel ni foto, no se inventa el servicio: se vuelve a hacer.

| Comando | Evento |
|---|---|
| Recibir mensaje | Dron frenado por papeles |
| Comparar seriales | Coincidencia de serial |
| Frenar ya | Dron frenado por boletín |
| Diferir a las 50 h | Boletín dejado para la revisión |
| Entregar carpeta | Carpeta entregada a seguridad |

<a id="v6g-pedido"></a>

### V6g Pedido

![V6g Pedido](vistas/V6g-pedido.png)

Raíz: el pedido. Adentro: nombre y modelo, aviso de llegada y costo si lo pasan.

Sin código de bodega. Siigo no devuelve existencia. Si la pieza no está, el dron no sale aunque el lote esté prometido. La garantía no suelta el vuelo: si hay pieza en la estantería se monta la nuestra y la mala queda apartada.

| Comando | Evento |
|---|---|
| Pedir por nombre y modelo | Pieza pedida |
| Registrar llegada | Llegada avisada |
| Adjuntar costo | Costo adjuntado |
| Negar la suelta | Dron sigue en orden |

<a id="7-mapa-de-contextos-e-interoperabilidad"></a>

## 7. Mapa de contextos e interoperabilidad

<a id="v8-mapa-de-contextos"></a>

### V8 Mapa de contextos

![V8 Mapa de contextos](vistas/V8-contextos.png)

Soltar el vuelo está al centro. Los de la izquierda le entregan lo que él pidió. Los de la derecha comparten el número y el modelo, o no deciden el verde.

| Relación | Entre quiénes | Patrón | Por qué ese patrón |
|---|---|---|---|
| Un solo total | Horas → Soltar el vuelo | Cliente-proveedor | El central dice qué necesita: una cifra. Horas no marca el verde |
| Cierre, sin verde | Intervención → Soltar el vuelo | Cliente-proveedor | El central dice que el cierre crítico no basta. Intervención no lo discute |
| Dos baterías sanas | Baterías → Soltar el vuelo | Cliente-proveedor | El central publica solo si hay dos del modelo |
| Freno | Retención → Soltar el vuelo | Conformista | «Este dron no sale» no se reinterpreta |
| Número y modelo | Identidad → Soltar el vuelo, y también hacia la orden | Núcleo compartido | Si cada contexto tuviera su propio modelo, la pieza se cruzaría |

Indicadores y pedido están en el mapa y no sueltan el vuelo. Los sistemas de afuera están en V9, para no mezclar el patrón entre contextos propios con el cruce hacia otro sistema.

<a id="v9-interoperabilidad-y-anticorrupcion"></a>

### V9 Interoperabilidad y anticorrupción

![V9 Interoperabilidad y anticorrupción](vistas/V9-interoperabilidad.png)

Cada intercambio es una fila. La flecha es corta y el nombre es el dato, no el sistema.

| De | A | Dato | Ritmo | Patrón |
|---|---|---|---|---|
| App del Agras | Horas de vuelo | Lectura de pantalla | Diario, cuando alguien la copió | Anticorrupción. No se suma sola |
| Novedades de campo | Intervención y orden | Novedad y foto | Diario, los días que se vuela | Anticorrupción. El mensaje no es el total de horas |
| Soltar el vuelo | Canal de programación | Lista: número, si sale, límite, motivo | Diario, antes de las cinco | Lenguaje publicado |
| Canal de programación | Indicadores | Lote corrido | Diario, cuando el coordinador lo dice | El indicador no lee FlightHub |
| Siigo | Pedido | Costo, si lo pasan | Eventual | No vuelve existencia ni fecha |
| Pedido | Distribuidor de Bogotá | Nombre y modelo | Eventual | No hay código de bodega |
| Distribuidor | Retención | Boletín | Eventual | Se compara el serial. No se obedece un comentario de otro operador |
| Seguridad | Retención | No sale | Eventual | Conformista |
| Retención | Seguridad | Carpeta | Eventual, una vez al año o si hubo incidente | El taller ordena la carpeta. Seguridad la manda. No hay API |

FlightHub, el portal de la Aeronáutica, el ICA y la habilitación del técnico no están en esta vista. En la entrevista ese cruce no existe. Dibujarlos con una línea de «no hay flujo» hacía parecer que sí había intercambio.

<a id="8-bounded-context-canvas"></a>

## 8. Bounded Context Canvas

<a id="v11-canvas"></a>

### V11 Canvas

![V11 Canvas de Soltar el vuelo](vistas/V11-canvas.png)

El canvas es una vista de Archi, no un tablero aparte. Arriba están el componente del contexto, la meta que realiza y el principio que la sostiene. El resto son notas, porque el canvas pide frases y no más cajas de aplicación. Se usó nota para propósito, clasificación, rol, lenguaje, entrada, salida, decisiones y supuestos. Así cabe en una página y se puede leer sin seguir flechas.

| Bloque | Qué dice |
|---|---|
| Propósito | Decidir si el dron entra al programa de mañana y publicarlo antes de las 17:00. No arma la finca ni promete el lote |
| Clasificación | Dominio central. Es la decisión que no puede fallar aunque fallen la foto, el costo o el papel de Espinal |
| Rol | Motor, bomba, batería y electrónica no salen porque el técnico firmó, porque el lote está vendido o porque el piloto quiere terminar |
| Lenguaje | Verde, en OT, pendiente de visto bueno, sale condicionado, lista de las cinco, visto bueno |
| Entrante | Cierre de línea o cierre crítico, horas ya reconciliadas, dos baterías sanas, freno ya comparado |
| Saliente | Número, sale, condicionado con límite, o no sale con el motivo. Sin despiece, sin regla de 50 h y sin póliza |
| Decisiones | Sin visto bueno se queda en tierra. El lote empezado no se corta. 200 h o seis meses, lo primero. Condicionado solo el carenado que no toca hélice ni tanque. Una sola batería no entra. Lo cerrado después de las cinco puede quedar en verde y aun así no se mete solo al programa de esa madrugada |
| Supuestos | El coordinador no programa un dron en OT. La app sigue siendo el origen de las horas. No hay portal. Si falta la pieza, este contexto no suelta el vuelo. El pre-vuelo no pone el verde |

<a id="9-decisiones-y-supuestos"></a>

## 9. Decisiones y supuestos

<a id="v10-trazabilidad-vertical"></a>

### V10 Trazabilidad vertical

![V10 Trazabilidad vertical](vistas/V10-trazabilidad.png)

La vista muestra dos cadenas, de arriba abajo, para que la relación vertical se lea sin cruzar el dibujo.

La de la izquierda es el visto bueno. La meta la realizan el resultado «sin respuesta, el dron se queda en tierra» y el requisito de los estados. El proceso de negocio «dar el visto bueno» realiza la capacidad «soltar el vuelo». Ese mismo proceso realiza el servicio de negocio «emitir el visto bueno». En la capa de aplicación, el componente se asigna al proceso de aplicación «otorgar visto bueno», ese proceso realiza el servicio de aplicación «emitir visto bueno», y ese servicio realiza el servicio de negocio. Así se baja de la meta al componente.

La de la derecha es la regla de las horas. El requisito «un solo total» realiza la meta. La restricción «no se suma el mensaje del piloto con la app» influye en contra de saltarse ese requisito. Abajo, el servicio de aplicación «registrar horas» realiza el servicio de negocio «registrar las horas».

Reglas que el modelo no afloja, aunque no quepan como una flecha:

- Horas y calendario mandan los dos. En el motor gana lo que se cumpla primero.
- En el banco, el T40 se abre si la bomba baja de 10 L/min. El T50, si baja de 13. Hélice y atomizador se cambian de a par.
- El de línea no abre motor, no da de baja una batería y no toca electrónica. En campaña puede cambiar la bomba completa en el portalón, sin abrir el cuerpo, y el verde espera al jefe.
- La lista de las cinco no mete sola, a la madrugada, un dron que quedó en verde después de esa hora.
- Seis T50 entregados desde noviembre de 2025 siguen en garantía de un año. Los otros diez y los ocho T40 no. El preventivo no abre ese trámite. Si hay pieza en la estantería, se monta la nuestra y la mala queda apartada. Si se sospecha garantía de motor, sale entero, sin abrir.

Supuestos que el jefe dio por ciertos y el diseño no discute:

- El coordinador no programa un dron que siga en orden o pendiente de visto bueno.
- La app del Agras sigue siendo el origen de las horas. El software no las inventa.
- No hay API con la Aeronáutica. El expediente lo sigue sacando seguridad.
- La existencia se ve en la estantería o la confirma la base.
- El alcance del técnico es el puesto, no una licencia que venza en un registro.

<a id="aportes"></a>

### Aportes

Nicolás Agudelo, Nicolás Buitrago, Esteban Alvarez y Sebastian Bedoya responden por el diseño completo. No hay una vista asignada a una persona. La entrevista, la motivación, las capacidades, el proceso, los servicios, los dominios, los agregados, los contextos, la interoperabilidad y el canvas los tiene que poder explicar cualquiera.

El repositorio se publica desde la cuenta de Nicolás Agudelo. Ese dato del historial no reparte el trabajo.
