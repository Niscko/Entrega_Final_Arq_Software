# Análisis de la entrevista

Fuente: la conversación con el jefe de mantenimiento de CampoAlto S.A.S., en [conversacion.md](conversacion.md). No hubo una segunda fuente externa. Lo que se contrastó fue la misma entrevista: la respuesta de reglas contra la de excepciones, y la de sistemas contra la de interoperabilidad. Cuando esas respuestas se repetían, el dato se aceptó. Cuando el jefe dijo que algo no lo ve, se dejó fuera.

## Qué se aceptó

CampoAlto fumiga caña en el Valle y arroz en Tolima. La flota es propia: 16 Agras T50 y 8 Agras T40. El cliente paga la hectárea. No contrata el mantenimiento y el taller no recibe drones ajenos.

Hoy no hay un sistema de mantenimiento. Hay una hoja «Control de flota», la orden en papel, la foto en OneDrive, dos grupos de WhatsApp («Novedades campo» y «Programa»), la app del Agras, FlightHub para la ubicación que mira operaciones, y Siigo para la factura de compra y la de hectáreas.

De ahí salió el alcance del software:

- Un solo total de horas. Si alguien leyó la pantalla del control, esa cifra manda y el mensaje del piloto no se suma. Si la app trae diez horas o más por encima de la hoja, se corrige la hoja. Si trae menos porque no cerraron la misión, se queda la hoja. FlightHub no entra en la cuenta.
- El repuesto no se cruza entre T40 y T50. El pedido se hace por nombre y modelo, no por código de bodega.
- El hallazgo del preventivo se anota en la misma orden. No se abre otro papel ni una bandeja de correctivo.
- La revisión de 50 h se hace al cerrar la jornada en que se cumple. No se corta el lote ya empezado y no se arma jornada nueva con esa revisión pendiente. La visita de motor es a las 200 h o a los seis meses, lo que ocurra primero.
- Estados que el jefe usa: en OT, pendiente de visto bueno, verde, sale condicionado, frenado.
- La lista de las 17:00 lleva número, si sale, el límite si es condicionado y el motivo si se queda.
- La baja de batería la decide el jefe. Para publicar hacen falta al menos dos baterías sanas del modelo.
- Los indicadores del día son los que él mira: disponibles a las cinco, lotes corridos por el taller, fallo crítico en el pre-vuelo, verdes con las 50 h vencidas y espera de Bogotá. Si falta el costo o no se contaron las fallas, el indicador queda vacío. No se publica cero.
- Un boletín o un mensaje de seguridad frena el dron aunque las horas no se hayan cumplido.

La decisión que no puede fallar es soltar el vuelo. Motor, bomba, batería y electrónica no salen porque el técnico firmó, porque el lote ya está prometido o porque el piloto quiere terminar. Sin el visto bueno del jefe, el dron se queda en tierra. Esa frase fija el dominio central y la meta de la vista de motivación.

## Qué se descartó

| Dicho en la entrevista | Decisión | Por qué |
|---|---|---|
| Programar la finca, prometer el lote, facturar hectáreas | Fuera | Lo hacen el coordinador y comercial. Al taller le basta el número, si sale y el límite |
| Reemplazar la app del Agras, FlightHub, Siigo o la estantería | Fuera | El software no inventa horas, ubicación, existencia, costo ni fecha de llegada |
| Pedir por código de bodega o recibir la existencia sola | Fuera | Se pide «bomba de T50». La existencia se ve en Palmira o la dice la base |
| Portal de la Aeronáutica y radicar la orden | Fuera | Cerrar la orden no radica nada. Seguridad arma el expediente, aparte. No hay API |
| ICA, dosis y etiqueta | Fuera | Las pone el agrónomo. No definen el verde |
| Habilitación del técnico | Fuera | No existe ese registro. El alcance es el puesto |
| Pre-vuelo como paso de dejar el dron disponible | Fuera del camino | Es a la madrugada, ya asignado. Si falla lo crítico, el dron vuelve a orden |
| Firmware, garantía, baja automática, cruce de modelo | Fuera de lo que el software ejecuta | El preventivo no abre la garantía. El trámite no suelta el vuelo |
| Drones de afuera | Fuera | Comercial dice que no |
| Tiempo medio entre fallas y costo por hora como número del mes | No se calcula | El jefe no los lleva. Pedirlos y publicarlos en cero diría una cosa falsa |
| FlightHub como fuente de horas o de disponibilidad | No se usa | Operaciones lo mira para saber dónde está el equipo |

## Cómo cambió el diseño

La lista de las 17:00, el visto bueno y el total único de horas pasaron a metas de V1. El mapa de V2 no se dibujó solo con el taller: comercial, la finca, el pre-vuelo, Siigo y la póliza aparecen marcados como «fuera» o «colinda», porque el jefe los nombró y dijo que no son suyos.

El proceso de V3 termina cuando el dron queda en verde y se publica la lista. Pre-vuelo y asignación de finca se dibujan aparte. El evento de pre-vuelo fallido devuelve el dron a la decisión, que es lo que él describió para las cinco de la mañana.

Las cinco capas de servicio salen de lo que sí entra. Los servicios de abajo en V4 son los que él dejó por fuera, para que la exclusión quede en el modelo y no solo en una tabla.

Los dominios no se partieron por pieza. Se partieron por quién puede soltar el vuelo. Intervención, horas y baterías le entregan datos a ese contexto y no lo ponen en verde. Ese es el cliente-proveedor de V8. La app y la novedad entran por anticorrupción porque la telemetría no se copia sola. El «este dron no sale» de seguridad no se reinterpreta: es conformista. FlightHub, el portal, el ICA y la habilitación no tienen flecha en V9, porque en la práctica ese cruce no existe.

Los agregados protegen las reglas que se repetían: una sola cifra de horas, una sola orden, la baja que no es automática, el indicador que no se publica en cero, y el pedido que no suelta el dron si la pieza no llegó.
