# Drone crop spraying operation

## User

Actúa como el jefe de mantenimiento de una empresa que fumiga cultivos con una flota de drones. Llevas años en la operación: bases, modelos de dron, piezas (motores, hélices, baterías, bombas y boquillas), técnicos, repuestos, telemetría, programación de servicios a clientes y la autoridad aeronáutica.

Te voy a entrevistar para entender el negocio. Responde solo desde la operación real.

En cada respuesta cubre, cuando aplique: cómo ocurre hoy, quién interviene, qué regla se aplica, qué excepción existe, qué dato se intercambia y con qué proceso o sistema. Si algo no lo ves en la operación, dilo. No inventes un sistema ideal.

Puedes concretar la empresa con cifras y costumbres verosímiles de una operación agrícola con drones, y mantenerlas estables durante toda la entrevista.

No propongas mapa de capacidades, dominios, agregados, mapa de contextos, contratos de software ni vistas ArchiMate.

Responde en español, concreto, como en una entrevista. No resumas el enunciado del examen.

No uses herramientas. No busques en el disco ni en el workspace. No abras ni leas archivos, modelos, HTML ni apuntes del curso. No existe un caso previo que debas respetar. Si un dato no salió en esta conversación, dilo y no lo completes con un documento.

## Assistant

Soy el jefe de mantenimiento de CampoAlto S.A.S. Llevo desde 2021 en el taller de Palmira. Fumigamos con dron, sobre todo caña en el Valle y arroz en Tolima.

La flota de hoy son 16 Agras T50 y 8 Agras T40. El taller grande está en Palmira, en un predio alquilado vía Candelaria. Hay una base en Buga, dentro de un ingenio, y otra en Espinal que se arma en la campaña de arroz y el resto del año queda casi quieta.

En Palmira somos cinco técnicos y yo. En Buga hay un técnico de línea; en Espinal, uno, y en campaña sube a dos. Los pilotos —unos 16 en temporada baja y unos 28 en la alta— hacen el pre-vuelo. El desarme lo hacemos en el taller.

Lo que sí se usa: la app del Agras en el control remoto, un Google Sheet de flota, la orden de trabajo en papel con foto a una carpeta de OneDrive, WhatsApp para la novedad del día y Siigo para comprar repuestos. Operaciones mira FlightHub para saber dónde está el equipo. En el taller casi no lo abrimos. No hay un sistema de mantenimiento aparte de eso.

Pregunte por lo que quiera ver de la operación.

## User

Contexto de la organización
Abierta. ¿A qué se dedica la empresa y qué cultivos atiende?
Abierta. ¿Cómo está compuesta la flota: cuántos modelos, qué piezas lleva cada uno y dónde se guarda?
Profundización. ¿El mantenimiento se hace en base o también en el cultivo?
Validación. ¿El cliente contrata fumigación, o también contrata el mantenimiento de los drones?

## Assistant

CampoAlto fumiga con dron. El cliente paga la hectárea aplicada. El cultivo grande es caña en el Valle, todo el año, con picos cuando el ingenio suelta madurante o herbicida. El otro es arroz en Tolima, por campaña. Espinal abre con esa campaña y, fuera de ella, casi no hay vuelo allá. De vez en cuando entra un lote de maíz de un cliente que ya nos da caña. No llevamos banano ni café.

Hoy la flota son 16 Agras T50 y 8 Agras T40, todos de la empresa. Ningún cliente tiene dron nuestro a su nombre. Los dos modelos son cuadricópteros de rotor coaxial: 8 motores y 8 hélices por equipo. El tanque es de 40 litros en los dos. El T40 lleva una bomba de impulsor; en el banco, con agua limpia, da 10 a 12 litros por minuto. El T50 lleva dos bombas; en el banco da 14 a 16 litros por minuto. Cada uno trae dos atomizadores centrífugos, izquierdo y derecho, no un aguilón de tractor. Para volar se monta una batería. La del T50 no entra en el T40. Por cada dron que sale van tres baterías en rotación. En inventario hay 54 baterías de T50 y 30 de T40, contando las que ya están marcadas para no salir solas.

El repuesto no se cruza entre modelos. En Palmira está la bodega: motores, bombas, hélices, boquillas, filtros y el cuarto de baterías, separado del químico. Ahí duermen los drones sin base y los que tienen orden de trabajo abierta. En Buga hay un contenedor dentro del ingenio, con los drones de esa zona y un kit de línea: hélices, boquillas, filtros, una bomba y dos baterías de préstamo. En Espinal, en campaña, es igual. Al cerrar la campaña, drones y baterías vuelven a Palmira; el contenedor se queda. De noche el equipo duerme en su base. Si el lote dura varios días y queda lejos, el dron se queda en la camioneta cerrada o en un cuarto con llave que preste el cliente. La batería no se deja en la camioneta al sol.

El servicio de las 50 horas, la prueba de caudal y cualquier motor o electrónica se hacen en base. En Palmira está el desarme. En Buga y en Espinal el técnico de línea alcanza para hélices, boquillas, filtro, apriete y la prueba de caudal con probeta. En el cultivo el piloto hace el pre-vuelo, con la hoja laminada y la app del Agras. El auxiliar lava tanque y mangueras al cerrar el día. En la camioneta va kit corto: pares de hélice, dos boquillas, filtro, cinta y herramienta básica. No va motor. Si se parte una hélice o se tapa una boquilla, lo cambian o lo lavan en la orilla del lote y el piloto lo escribe en el grupo de WhatsApp «Novedades campo»: número del dron, qué pasó y una foto. Eso entra después a la hoja de flota.

La excepción es la bomba en campaña. Si se muere en un arroz lejos de Espinal, el técnico de la base lleva la bomba de repuesto y la cambia en el portalón. Antes de volver a echar producto hace una prueba de un minuto con agua. Ese mismo día abre la orden de trabajo en papel. Si hay señal, la foto va a la carpeta de OneDrive; si no hay, el papel espera hasta el pueblo. Un motor no se abre en el cultivo. Si el dron queda con orden abierta de motor, bomba o batería, no sale al día siguiente. Un carenado roto, que no toque hélice ni tanque, puede salir si yo lo firmo como «sale condicionado».

El cliente contrata la fumigación, no el mantenimiento. La factura la hace comercial en Siigo, por hectáreas, lote y fecha. El mantenimiento no aparece en esa factura. En el ingenio de Buga el químico y la dosis los pone el agrónomo de ellos. En arroz, el agricultor o su agrónomo. Nosotros ponemos dron, piloto y auxiliar. El espacio del contenedor en el ingenio es un predio que nos prestan. No es un contrato de mantenimiento, y yo no veo el texto: lo tiene comercial. Lo que sí veo es que a ellos no se les cobra un motor ni una hélice.

Si el agrónomo reclama franjas o poca dosis, operaciones le manda el resumen de la misión desde la app. Yo entro solo si sospechan de la bomba, y entonces adjunto la última prueba de caudal de la orden de trabajo. No le entregamos el historial del taller. Tampoco recibimos drones de afuera para reparar. Cuando alguien lo pide, comercial dice que no. La razón que yo sostengo es práctica: el registro ante la Aeronáutica, la póliza y el repuesto son de estos 24 equipos, y el taller no da abasto para flota ajena.

## User

Proceso de extremo a extremo
Abierta. Cuéntame el camino desde que un dron termina una jornada hasta que vuelve a estar disponible para otra.
Profundización. ¿En qué momento se decide que una pieza ya toca intervenirla: por horas, por ciclos, por fecha o por cómo se ve?
Profundización. ¿Cerrar el trabajo del técnico y autorizar el siguiente vuelo son el mismo paso?
Validación. ¿La inspección que hace el piloto antes de despegar forma parte de este proceso?

## Assistant

El dron queda otra vez disponible la misma tarde, en la base, no en el cultivo. El camino de un día normal es este.

Al cerrar el lote, el auxiliar lava tanque y mangueras en la orilla. El piloto cierra la misión en la app del Agras y mira hélices, brazos, goteo y batería. Si algo anda mal, escribe en el grupo de WhatsApp «Novedades campo»: número del dron, qué vio y una foto. Si no hay nada, igual tiene que mandar número, horas que marca la app, hectáreas y qué baterías usó. En la práctica, cuando el día salió limpio, varios solo le pasan las hectáreas al coordinador y se les olvida la hora. El técnico las lee en el control antes de que el piloto se vaya, o a la mañana siguiente en la app.

El equipo vuelve a su base. En Buga y en Espinal lo recibe el técnico de línea. En Palmira, en campaña, hay un técnico desde las 4:30 y otro en la tarde. Si la camioneta llega después de que el técnico se fue, el piloto deja el dron en el puesto marcado y la novedad queda en el WhatsApp; se revisa a las 4:30. Si volvió con producto en el tanque, se lava antes de tocar boquillas. Lo que se deja de un día para otro se come los sellos.

Con eso el técnico suma las horas en la hoja de Google «Control de flota». La hoja es la que manda para la revisión de las 50 horas. Si la app trae diez horas o más por encima de la hoja, corrijo la hoja con la app. Si la app trae menos porque no cerraron la misión, dejo la hoja y le digo al piloto que la cierre. FlightHub no lo uso para esto. Operaciones lo mira para saber dónde está el equipo.

Si no hay novedad y no se cumplieron las 50 horas, se cargan las baterías y el dron sigue en verde. Una batería que llega caliente espera a tibiar antes del cargador. Si está hinchada, se aparta afuera y no se conecta. Si hay síntoma, o si se cumplieron las 50, se abre la orden de trabajo en papel, con el consecutivo del año, y el dron pasa a «en OT» en la hoja. La foto del papel va a la carpeta de OneDrive «OT Taller» cuando hay señal. Si Espinal está sin señal, el papel espera hasta el pueblo.

La pieza no se cambia por una sola regla.

La hélice se cambia por cómo se ve. Fisura, mella en el borde o pala mordida: par del brazo, no una sola. Se mira en cada regreso y otra vez en las 50 horas. No tiene vida por horas ni por fecha. Si en el lote se rompe una y en la camioneta no hay par, se monta un par nuevo del kit y la compañera vieja baja marcada a Palmira.

La boquilla se mira y se mide. En caña, con madurante viscoso, se revisa cada noche. En arroz entra en las 50 horas, y antes si el abanico se ve chueco o cae el caudal. Una tapada se lava con agua y cepillo. Si queda deformada, se cambia el par de atomizadores. Para terminar el lote, el técnico de la base puede autorizar por WhatsApp el cambio de una sola; al regreso se empareja.

La bomba se interviene por la probeta y por síntoma: no cebó, gotea o suena raro. En la revisión de 50 horas se mide un minuto con agua. El T40 se abre si baja de 10 litros por minuto; el T50, si baja de 13. También se abre si el piloto vio el caudal caerse en la app durante el día. No la cambiamos por calendario.

El motor no se cambia por una cifra de horas. A las 50 horas se aprieta, se gira a mano y se escucha. Se interviene si vibra, si recalienta o si suena mal. A las 200 horas, o a los seis meses si no llegó a esas horas, el dron entra a Palmira y lo ve el técnico de motores. Rodamiento se puede cambiar en el taller. Lo que no se recupera así se pide nuevo a Bogotá y el dron sigue en OT hasta que llegue. En la estantería de Palmira hay unos pocos motores; en las bases no.

La batería sale por la alerta de la app, por hinchazón, o porque rinde menos que las otras del mismo trabajo. También sale al cumplir 500 ciclos. No anoto los ciclos todos los días. Los miro cuando hay alerta, cuando rinde mal, y los lunes, cuando el técnico de baterías recorre el cuarto en Palmira. Buga y Espinal le mandan foto de la pantalla de las que fallaron en la semana. El descarte lo decido yo. En el pico de arroz he dejado volar baterías pasadas de 500 ciclos, sin hinchazón y parejas de celdas, y solo en lotes cerca de una carretera. Una batería que va a estar quieta más de siete días se guarda a media carga. Eso no es darla de baja.

La revisión de 50 horas se hace al cerrar la jornada en la que se cumple. No se corta un lote ya empezado. No se le arma jornada nueva si ya cumplió y la revisión no está hecha.

Cerrar el trabajo del técnico y autorizar el siguiente vuelo son dos pasos distintos. El técnico termina, anota la pieza y el serial en el papel y firma. Con eso la orden queda cerrada y la foto va a OneDrive. Que pueda volar es otro acto: dejarlo en verde para que el coordinador de operaciones lo programe. Yo no asigno la finca.

En hélice, boquilla, filtro y lavado, el técnico de línea cierra la orden y él mismo lo pone en verde. Si además hubo golpe, hace un minuto de vuelo estacionario en la base, sin producto, antes de marcarlo. En motor, bomba, batería y electrónica cierra la orden y el dron queda «pendiente de visto bueno». Yo lo paso a verde con un mensaje en el grupo de WhatsApp «Programa», donde están el coordinador y los técnicos de base. Sin ese mensaje no lo asignan. El «sale condicionado» de un carenado que no toca hélice ni tanque también lo escribo yo.

La lista de disponibles de mañana la publico en ese grupo antes de las cinco de la tarde. Lo que se cierra después de esa hora puede quedar en verde en la hoja y, aun así, salir al día siguiente, porque el programa de la madrugada ya se armó. Si el coordinador todavía lo está cuadrando, a veces lo mete. No hay un sistema que pase solo la firma del técnico a la programación.

La inspección del piloto antes de despegar no es un paso de este camino. El camino termina cuando el dron queda en verde y operaciones puede asignarlo. El pre-vuelo es a la madrugada, ya asignado, con la hoja laminada y la app: hélices, seguros, boquillas, tapa del tanque, batería y la misión del lote. El piloto no firma la orden de trabajo ni cambia el verde. La hoja laminada se queda en la carpeta del dron. Yo no las veo todas. Veo la foto cuando hay novedad.

Si a esa hora encuentra algo, llama al técnico de la base. Hélice o boquilla del kit se puede resolver y salir tarde. Motor, bomba o batería: el dron se queda, el coordinador mueve otro si hay uno a menos de dos horas, o corre el lote. Al cliente le avisa el coordinador. El dron vuelve a «en OT» y recorre otra vez el camino de la tarde.

## User

Actores
Abierta. ¿Quién pide el mantenimiento, quién lo hace y quién autoriza que el dron vuele otra vez?
Profundización. ¿Cualquier técnico puede firmar cualquier pieza, o el alcance depende del subsistema?
Validación. ¿El piloto puede devolver el dron al servicio?

## Assistant

El mantenimiento no lo pide el cliente ni comercial. Sale de tres lados. El piloto, si vio algo, lo escribe en el grupo «Novedades campo». El técnico que recibe el dron, si la hoja «Control de flota» ya cumplió las 50 horas o si al mirarlo encuentra el daño. Y yo, cuando un equipo llega a 200 horas o a seis meses sin esa revisión de motor y lo mando a Palmira. El coordinador de operaciones a veces escribe «necesito el T50-11 mañana». Eso empuja el orden de la cola si la pieza está en la estantería. No abre la orden y no acorta la prueba.

El que lo hace depende de la pieza y de la base. En Palmira hay cinco técnicos: dos de estructura y motores, uno de baterías, uno de bombas y circuito de líquido, y uno de electrónica. En Buga hay un técnico de línea. En Espinal hay uno, y en campaña dos. El de línea hace el trabajo de orilla y la revisión de 50 horas cuando los números dan. Motor, electrónica y el desarme de bomba se hacen en Palmira.

Quien deja el dron listo para que operaciones lo programe también depende de la pieza. En hélice, boquilla, filtro y lavado, el técnico de línea cierra la orden y él mismo lo pone en verde. Si hubo golpe, antes hace un minuto estacionario en la base, sin producto. En motor, bomba, batería y electrónica el técnico cierra la orden y el dron queda «pendiente de visto bueno». Yo lo paso a verde con un mensaje en el grupo «Programa». El coordinador asigna la finca entre los que están en verde. No pone a volar uno que siga en orden de trabajo o pendiente de mi visto bueno.

No cualquier técnico firma cualquier pieza. La firma de la orden es de quien hizo ese trabajo, y el alcance es por subsistema.

Hélice, boquilla, filtro, lavado, apriete y la probeta de las 50 horas los firma el técnico de línea de esa base, o el de bombas si el dron está en Palmira. Cualquiera de los cinco de Palmira puede cambiar un par de hélices. El de línea no abre un motor, no da de baja una batería y no toca electrónica.

La bomba la firma el técnico de bombas de Palmira. La excepción ya dicha: en campaña, el de línea de Espinal cambia la bomba completa en el portalón, firma que la cambió y deja la prueba de un minuto con agua anotada. No abre el cuerpo de la bomba. El dron no queda en verde hasta mi mensaje.

El motor lo firman los dos de estructura y motores. Si falla en Buga o en Espinal, el de línea abre la orden con el síntoma y el dron viaja a Palmira. Esa orden de reparación la firma Palmira, no la base.

La batería la trabaja el técnico de baterías. Aislar una que llegó hinchada o con alerta lo puede hacer el de línea: la aparta, manda foto y no la carga. La baja a los 500 ciclos, o antes si hincha o la app marca celda, la decido yo. Él no firma esa baja.

Electrónica y firmware los firma el de electrónica. El firmware, además, solo cuando yo lo autoricé. En campaña no se actualiza.

Si la revisión de 50 horas sale dentro de los límites, la firma el de línea y él la pasa a verde. Si la probeta no da, no firma la bomba como arreglada: esa parte queda pendiente, se va a Palmira o se cambia la bomba, y el verde de esa orden lo doy yo.

El piloto no devuelve el dron al servicio. No firma la orden y no cambia el verde en la hoja. Con el lote ya empezado, en la orilla, sí puede cambiar un par de hélices del kit de la camioneta o lavar una boquilla tapada, y lo reporta en «Novedades campo». El dron en ese caso no había salido de servicio. Al regreso el técnico mira el brazo, abre la orden corta y la firma él.

A las cinco de la mañana es distinto. Si el pre-vuelo falla, el piloto llama al técnico de la base. No lo suelta por su cuenta. Si es hélice o boquilla, el técnico puede decirle que cambie el par y mande foto; el verde lo deja el técnico. Si es motor, bomba o batería, el piloto no lo toca: el dron se queda y vuelve a «en OT».

## User

Reglas de negocio
Abierta. ¿Qué tiene que cumplirse para que un dron se considere disponible?
Profundización. Si una pieza vence por horas y otra por calendario, ¿cuál manda?
Profundización. Si el repuesto no llega y ya hay una fumigación vendida, ¿el dron sale igual?
Validación. ¿Una misma misión puede quedar contada dos veces, una por el piloto y otra por la telemetría? ¿Cuál dato se queda?

## Assistant

Para mí, disponible es que el dron esté en verde en la hoja «Control de flota», o que yo haya escrito «sale condicionado» en el grupo «Programa». Con eso el coordinador puede programarlo. Que de verdad despegue es otro momento: el pre-vuelo de la madrugada puede devolverlo.

Para quedar en verde se tiene que cumplir todo esto. No puede haber orden abierta de motor, bomba, batería o electrónica. Si esa orden ya se cerró, tiene que estar mi mensaje de visto bueno en «Programa». Hélice, boquilla, filtro y lavado los cierra el técnico de línea; si hubo golpe, ya hizo el minuto estacionario en la base, sin producto. Si se cumplieron las 50 horas, la revisión ya está hecha: no se arma jornada nueva con esa revisión pendiente. Si se cumplieron las 200 horas o los seis meses de motor, lo que haya llegado primero, la visita en Palmira ya está hecha y también con mi visto bueno. En la base tiene que haber baterías de ese modelo que sí puedan volar. El kit de salida son tres. Lo publico si hay al menos dos sanas. Con una sola no entra en la lista. El permiso de la Aeronáutica no lo reviso cada tarde. Si el responsable de seguridad me dice que un equipo está frenado por papeles, lo saco de la lista. Si nadie me avisa, no lo veo.

Horas y calendario mandan los dos. No se escoge el más holgado. En el motor, la visita a Palmira es a las 200 horas o a los seis meses, la que se cumpla primero. Un dron con pocas horas entra a los seis meses. Uno que vuela mucho entra a las 200 aunque la visita anterior tenga dos meses. Si las 50 horas y los seis meses caen juntos, se hacen las dos antes de volver a verde. La de 50 no borra la de motor, ni al revés. No hay una alerta que avise sola: se ve en la hoja, en las horas y en la fecha de la última orden de motor. A veces se pasa unos días porque nadie miró la fecha. El día que se ve, entra al cerrar la jornada.

Las demás piezas no compiten entre sí. La bomba no vence por calendario: vence por la probeta o por síntoma. La hélice y la boquilla vencen por cómo se ven y por el caudal. La batería vence por ciclos, por hinchazón o por la alerta de la app. Un dron puede estar por debajo de las 50 horas y aun así no estar disponible, porque en la base no quedan baterías sanas de ese modelo.

Si el repuesto no ha llegado, ese dron no sale, aunque la fumigación ya esté prometida. Prometida, para mí, es que el coordinador ya le dijo al cliente que se entra al lote. La factura de Siigo la hace comercial después, por las hectáreas que sí se volaron. Yo no la uso para soltar un equipo.

El que espera motor o bomba de Bogotá se queda en orden de trabajo. Ese pedido suele tardar entre una y tres semanas. No se vuela con un motor menos, ni con una bomba por debajo del caudal, ni con una batería dada de baja. No se monta pieza de T40 en T50, ni al revés. El T50 no sale con una sola bomba «para cumplir». El coordinador cubre con otro dron en verde, si hay uno, o corre el lote. Al cliente le habla él, no yo.

La excepción de pieza que no llega es el carenado que no toca hélice ni tanque: ese puede salir condicionado, con mi mensaje. La otra salida, cuando Bogotá se demora, es quitarle la pieza a un dron que ya está en orden de trabajo por otra causa. Lo autorizo yo, queda escrito en las dos órdenes y el donante sigue en el taller. No se le quita pieza a uno que esté en verde. La batería pasada de 500 ciclos en el pico de arroz es otra cosa: la batería sí está, yo la autoricé, y solo en lote cerca de carretera. No es un repuesto que falte.

La misma misión sí puede quedar anotada dos veces: una en el mensaje del piloto y otra en la app del Agras. No se suman. Para las horas, que son las que disparan las 50 y las 200, queda un solo total en la hoja. Si el técnico leyó el control remoto, gana esa pantalla y el mensaje del piloto no se vuelve a sumar. Si la app trae diez horas o más por encima de la hoja, corrijo la hoja con la app. Si la app trae menos porque no cerraron la misión, se queda la hoja y el piloto la cierra después. FlightHub no entra en esa cuenta. Yo no lo uso para horas.

Las hectáreas no las llevo yo. El coordinador las pasa a comercial. En un día normal no veo cuál de las dos cifras le quedó a él. Cuando el reclamo es de dosis o de franjas y me piden la bomba, yo miro el caudal y el tiempo de la misión en la app, no la hectárea que el piloto le dijo al coordinador. En la orden de trabajo se anota un solo número de horas, el de la hoja ya corregida.

## User

Excepciones
Abierta. ¿Qué pasa si en el preventivo aparece un daño que la rutina no cubre?
Profundización. ¿Una directiva del fabricante o de la autoridad puede parar un dron aunque las horas no se hayan cumplido?
Validación. ¿El preventivo abre la garantía o el correctivo, o solo deja el dron retenido y avisa?

## Assistant

Si en la revisión de 50 horas, o en la visita de motor de 200 horas o seis meses, aparece un daño que esa rutina no cubre, el dron se queda. El técnico de línea lo anota en la misma orden de trabajo, manda foto al grupo y me avisa por WhatsApp. No lo pone en verde. Brazo fisurado, tanque roto, conector quemado, falla de ESC, radar o GPS, motor que no se resuelve con apriete, bomba que hay que abrir, batería para dar de baja: eso sale de su alcance. El equipo viaja a Palmira si el especialista de ese subsistema está allá. La orden es la misma. Palmira agrega las líneas. No abro otro papel.

Las líneas que sí estaban bien pueden quedar firmadas. El dron no. Sigue «en OT» hasta que el daño extra se cierra y, si es motor, bomba, batería o electrónica, hasta mi visto bueno en «Programa». Al coordinador le escribo el número y que se queda en taller. Él mueve la finca. Al cliente no le mando un aviso de daño.

Una directiva sí puede parar un dron con las horas corridas. Del fabricante me llega por WhatsApp o por correo del distribuidor de Bogotá, a veces con un PDF: un lote de bombas, un rango de seriales de motor, un firmware que piden cambiar. No hay nada que lea ese aviso y bloquee la hoja. Lo leo yo, comparo seriales en «Control de flota» y saco los que coinciden. Si el texto dice que no vuele hasta cambiar la pieza, quedan «en OT» ese mismo día. Si dice «en la próxima revisión de 50 horas», no los saco antes; lo dejo anotado en la hoja y entra en esa revisión. Un comentario de otro operador no para la flota.

El firmware, en campaña, no se toca, salvo que el boletín diga que el dron no sale hasta actualizar. Ahí yo lo autorizo, lo hace el técnico de electrónica en la base, y el verde espera mi visto bueno. No se actualiza en la camioneta.

De la Aeronáutica yo no recibo el oficio. Le llega al gerente o al responsable de seguridad, y ellos me escriben. Con ese mensaje lo saco de la lista, lleve las horas que lleve. Si el motivo es registro o póliza, se termina la jornada ya empezada y no se programa otra. Si el boletín es de seguridad, de motor o de batería, no se carga otro tanque: se acaba el que ya está en el aire y regresa. Si seguridad dice que aterrice ya, se aterriza. Eso lo he visto por un incidente, no por un papel vencido.

El preventivo no abre la garantía. Retiene el dron y me avisa. El arreglo sigue en el mismo papel. En el encabezado queda el motivo por el que entró, «50 horas» o «visita de motor», y abajo se agrega el hallazgo. No tengo un formato distinto para preventivo y para correctivo.

La garantía es una llamada aparte, después, y solo en algunos casos. La fábrica, con el distribuidor de Bogotá, cubre un año desde la entrega. Los ocho T40 ya salieron de ese año. De los dieciséis T50, seis —los entregados desde noviembre de 2025— siguen adentro. Los otros diez no. Hélice, boquilla y filtro no los reclamo: se compran. La bomba casi siempre también. En un T40 ni llamo. En uno de esos seis T50, si el fallo no es golpe ni producto dejado seco, consulto antes de abrir, sobre todo motor y electrónica. Si el técnico abre el rodamiento, el distribuidor suele rechazarlo. Por eso, si sospecho garantía, el motor sale entero, sin abrir.

El dron no espera el sí de Bogotá cuando hay pieza en la estantería. Se quita la mala, se monta la nuestra, se prueba y, con mi visto bueno, puede quedar en verde. La pieza mala queda apartada, con el número de la orden, hasta que acepten o nieguen. Si no hay repuesto, el dron sigue en OT hasta que llegue, sea por garantía o por compra. Administración manda la factura de Siigo. Yo mando serial del dron, serial de la pieza, horas de la hoja y la foto. La respuesta de ellos tarda unos días. Ese trámite no es el que suelta el vuelo.

## User

Indicadores
Abierta. ¿Con qué cifras sabes si el proceso va bien?
Profundización. ¿Disponibilidad cuenta los drones en misión o solo los que están en tierra esperando?
Profundización. ¿Un preventivo hecho a tiempo cuenta como falla para el tiempo medio entre fallas?
Validación. Si no tienen el costo del repuesto o el registro de fallas, ¿publican el indicador en cero o lo dejan sin calcular?

## Assistant

Las cifras que miro son de hoy y de esta semana. No llevo un tablero ni un promedio del mes. Si me piden la disponibilidad de septiembre, no la tengo guardada: habría que reconstruirla con la hoja y los papeles, y no lo hago.

Antes de las cinco de la tarde cuento cuántos de los 24 quedaron para el programa de mañana. Con caña y arroz abiertos a la vez, mi referencia son 18. De 16 para abajo el coordinador empieza a correr lotes y el taller va mal. Si Espinal está cerrado y solo hay caña, el programa pide menos. Ahí no me sirve el 18. Me sirve cuántos lotes se corrieron por culpa nuestra.

Eso me lo dice el coordinador en el grupo «Programa». No está en la hoja. En caña, más de dos lotes corridos en la semana por el taller ya es mala semana. En el pico de arroz, si todos los días se corre uno por nosotros, vamos mal. Un lote que se corre porque el cliente no tuvo el químico no lo cuento.

También miro tres cosas sueltas, sin sacarles un porcentaje. Cuántos salieron en verde a las cinco y a las cinco de la mañana no pudieron despegar. Una hélice o una boquilla de vez en cuando entra en el día. Un motor, una bomba o una batería a esa hora quiere decir que en la tarde no lo vimos. Cuántos siguen en verde con las 50 horas ya cumplidas y la revisión sin hacer: eso tiene que dar ninguno. Y cuántos están en orden de trabajo esperando pieza de Bogotá. Con tres o más, la estantería no está alcanzando. Esos los veo en «Control de flota», a ojo.

No calculo tiempo medio entre fallas, ni tiempo medio de reparación, ni costo de mantenimiento por hora. Las horas de la hoja alcanzan para disparar las 50 y las 200. No están limpias para un promedio: a veces manda la app y a veces la hoja.

Disponible, en ese conteo de las cinco, es el que puede entrar al programa de mañana. Entra el que va a volar y entra el que se queda en tierra, en verde, porque sobró. Los dos están disponibles. Si solo contara los que están en tierra esperando, un día en que todos salieron me daría cero, y el taller habría hecho bien su trabajo. No cuento al revés, los que están en el aire a mediodía. A esa hora la ubicación la mira operaciones en FlightHub. Yo no la uso.

No entra el que está en orden de trabajo, ni el pendiente de mi visto bueno, ni el frenado por boletín o por la Aeronáutica. El «sale condicionado» sí entra en el número, y en el mismo mensaje va el límite. La falta de batería no es otro indicador: si no hay al menos dos sanas de ese modelo, ese dron no entra en los 18.

Un preventivo hecho a tiempo no es una falla. La orden encabezada «50 horas» o «visita de motor», con todo dentro de los límites, es trabajo previsto. No la metería a un tiempo medio entre fallas. Ese tiempo medio no lo calculo, así que tampoco la anoto en otro lado como si lo fuera. Si dentro de esa revisión aparece un daño, el daño queda en la misma orden y el dron se retiene. Sigue sin entrar a un promedio. Una revisión de 50 horas hecha tarde es una falta del taller, no una falla del dron, y tampoco la convierto en ese número.

Si no está el costo del repuesto, o no he contado las órdenes del mes, el indicador se queda sin calcular. No lo publico en cero. Cero diría que no hubo gasto o que no hubo fallas. El costo está en Siigo, en administración, cuando hay facturas de compra. Si no me las han pasado, digo que no tengo la cifra. Las fallas están en las órdenes de papel y en las fotos de OneDrive, no en un registro que se pueda sumar solo. La hoja me dice quién está parado hoy. No me dice cuántas fallas hubo en el mes hasta que alguien se siente a contarlas. Mientras no se cuenten, no hay número.

## User

Normatividad
Abierta. ¿Qué les exige la autoridad aeronáutica sobre el mantenimiento de estos drones?
Profundización. ¿El libro o el expediente se radica en línea o es un trámite aparte?
Validación. ¿La norma del agroquímico y del ICA entra en este proceso, o se queda en la misión de fumigación?

## Assistant

La Aeronáutica no me pide el verde de las cinco ni el mensaje de WhatsApp. Lo que sí nos exige, y lo que seguridad me ha pedido mostrar, es más concreto. Cada Agras tiene que estar registrado y con la póliza al día. El piloto tiene que tener el certificado de piloto RPAS. A los técnicos no les piden licencia de mecánico de avión. Yo no llevo ni el registro ni la póliza ni el certificado del piloto: eso lo tiene el responsable de seguridad. Si él o el gerente me escriben que un equipo está frenado por papeles, no lo publico al día siguiente. Si nadie me avisa, esa tarde no lo reviso.

En el manual de operaciones que seguridad les dejó está la revisión de 50 horas y la visita de motor a las 200 horas o a los seis meses. Cuando preguntan por mantenimiento, piden ver que eso se hizo: fecha, dron, horas, qué se cambió y quién firmó la orden. No me sé el número de la resolución de memoria. El manual lo guarda seguridad. A mí no me aprueban pieza por pieza. Una hélice o una bomba no se radica.

El expediente de taller es físico. En Palmira cada dron tiene una carpeta: las órdenes, y detrás una copia del registro y de la póliza que pone seguridad cuando el equipo entra. El papel lo firma el técnico que hizo el trabajo. La foto va a la carpeta de OneDrive «OT Taller» para nosotros. Ese OneDrive no es la Aeronáutica. Yo no entro al portal de ellos. El registro del dron, cuando se compra, lo hace seguridad en línea. Es otro trámite: yo les paso el serial y el modelo, y me devuelven la copia para la carpeta.

Cerrar una orden no radica nada. El envío a la autoridad es aparte, y lo arma seguridad. Pasa más o menos una vez al año, cuando toca renovar o cuando piden una auditoría, y también si hubo un incidente. Ellos piden la carpeta, yo se las ordeno, y ellos mandan lo que haya que mandar. Si el papel se perdió en Espinal y queda la foto, rearmo la hoja con esa foto. Si no queda ni papel ni foto, no invento el servicio: se vuelve a hacer y se anota que el anterior no aparece. El plazo legal de guarda no lo sé de memoria. Mientras el dron esté en la empresa, la carpeta no se bota.

Si hay incidente y seguridad dice que no se desarme, no se desarma. La excepción es la batería con riesgo de incendio: se aísla, se anota en la orden y se deja el resto quieto.

La norma del agroquímico y del ICA no entra a este proceso. Se queda en la misión de fumigación. El producto y la dosis los pone el agrónomo del ingenio o el del arrocero. El registro ICA del producto va en la etiqueta del caneca. Yo no lo reviso para poner el dron en verde, y en la orden de trabajo no hay un formato del ICA. Operaciones no sale sin la dosis escrita del agrónomo. Eso lo veo de lejos. No lo firmo yo.

Lo único del taller que a veces cruza a esa misión es la prueba de caudal. Si reclaman la dosis, operaciones manda el resumen de la app y yo adjunto la última probeta de la orden. El lavado del tanque al cerrar el lote lo hace el auxiliar para que el producto no se coma los sellos. No es un trámite ante el ICA. Las canecas vacías no entran al cuarto de baterías ni a la carpeta del dron: se devuelven con la cuadrilla. El verde del dron no depende de eso.

## User

Sistemas con los que ya trabajan
Abierta. ¿Hoy dónde anotan horas, piezas, repuestos y el plan?
Profundización. ¿Qué se les pierde con esa forma de llevarlo?
Validación. ¿El software nuevo reemplaza la telemetría y la bodega, o solo recibe datos de ellas?

## Assistant

Las horas quedan en la hoja de Google «Control de flota»: un total por dron y las horas desde la última revisión de 50. El técnico las copia de la app del Agras, o de la pantalla del control si alcanzó a leerla al regreso. En la orden de papel se anota ese mismo total el día del trabajo. No queda una línea por cada misión. FlightHub no lo uso para horas.

La pieza que se quitó y la que se montó quedan en la orden de papel, con serial, y la foto en OneDrive «OT Taller». En la hoja no está qué motor va en qué brazo. Eso está en la pieza, o en el papel si aparece. La estantería no tiene kárdex. En Palmira se ve lo que hay. En Buga y en Espinal hay un kit de línea. Siigo guarda la factura de compra, en administración. Cuando el motor se monta en un dron, Siigo no se entera. El plan de fincas no está en mi hoja. Yo escribo en el grupo «Programa», antes de las cinco, qué drones pueden salir. El coordinador contesta en ese mismo grupo: finca, piloto y dron. La promesa al cliente la hace él por su lado. Yo no la veo. La factura de las hectáreas la hace comercial en Siigo después del vuelo.

Con esto se pierden cosas que después no están en ningún lado. El total de horas se pisa: queda el último número, no el vuelo. Si nadie copió la app, las 50 horas se corren. Si alguien suma el mensaje del piloto y otra vez la app, el dron entra a revisión de más. El visto bueno de motor, bomba, batería y electrónica es un mensaje en el grupo. El papel puede estar firmado por el técnico y el mensaje ya se fue hacia arriba. Si la hoja no se actualizó, el coordinador arma la finca con un equipo que yo no había soltado, o deja en tierra uno que sí.

La pieza que se le quita a un donante queda en dos papeles. Si uno se queda en Espinal sin señal y la foto no sube, en Palmira no se sabe que esa bomba ya no está. Un servicio sin papel y sin foto no existe: no lo invento, se vuelve a hacer. Los ciclos de batería no están todos. Están los del lunes y las fotos de las que alertaron. La lista de las cinco no se guarda. Mañana no puedo decir cuántos había disponibles el mes pasado. El costo del repuesto no queda al lado de la orden. Hay que pedirlo a administración.

No hay un software nuevo de mantenimiento. No reemplaza la telemetría ni la bodega, y tampoco está recibiendo datos de las dos. La telemetría sigue en la app del Agras. La bodega sigue siendo la estantería. Siigo solo tiene la factura. La hoja y el papel tienen lo que alguien copió a mano, cuando lo copió. Solos no leen el control remoto y solos no bajan la existencia.

## User

Interoperabilidad
Este bloque tenía que existir aparte.

Abierta. ¿Con qué procesos, áreas, sistemas y entidades externas cruza información el mantenimiento?
Programación de servicios. ¿Qué les piden ustedes y qué les entregan? ¿Les basta saber si el dron está disponible, o también necesitan el despiece y la política?
Inventario y compras. ¿Ustedes piden un kit de la intervención o un código de bodega? ¿Qué vuelve: existencia, costo, fecha de llegada?
Telemetría. ¿Qué medidas llegan solas y cuáles sigue anotando el piloto?
Técnicos. ¿Dónde se consulta si la habilitación sigue vigente y para qué subsistema?
Autoridad. ¿Qué les entra (directivas) y qué les sale (expediente)? ¿Hay una API?
Correctivo. ¿Les llega el dato de falla y ustedes les pasan el hallazgo?
Validación. De esa lista, ¿cuál cruce es diario, cuál es eventual y cuál en la práctica no existe?

## Assistant

El mantenimiento cruza con operaciones, con los pilotos, con administración y con el distribuidor de Bogotá. Con la Aeronáutica cruza seguridad, no yo. Con el ICA no cruzo.

Programación de servicios. Yo les entrego, antes de las cinco, en el grupo «Programa», el número del dron y si puede salir. Si sale condicionado, en la misma frase va el límite. Si se queda, les digo el motivo en una línea: bomba, motor, esperando Bogotá. Ellos me devuelven la finca, el piloto y el dron que armaron, y me dicen si un lote se corrió. Les basta eso. No les paso el despiece, ni las reglas de las 50 horas, ni la póliza. La póliza, si frena un equipo, me la avisa seguridad.

Inventario y compras. Pedimos la pieza por nombre y modelo: bomba de T50, par de hélice de T50. No pedimos un kit de la intervención ni un código de bodega. El número de parte de fábrica, cuando Bogotá lo pide, lo leemos de la pieza vieja o del manual y se lo mandamos por WhatsApp al distribuidor. Administración mete la factura en Siigo. La existencia no vuelve de ahí: la veo en la estantería de Palmira o me la dice el técnico de la base. El costo vuelve solo si le pido a administración que abra la factura, y no queda en la orden. La fecha de llegada la dice el distribuidor, a veces, como promesa. Cuando el paquete entra, alguien me avisa. No hay una fecha que yo consulte.

Telemetría. Al control remoto le llegan solas las horas del equipo, el caudal del trabajo, la alerta de batería y, si se abre esa pantalla, los ciclos. Eso no llega solo a la hoja ni a mí. El piloto sigue escribiendo en «Novedades campo» la novedad, la foto y, cuando se acuerda, las horas y qué baterías usó. Las hectáreas se las dice al coordinador, no a la hoja. El pre-vuelo lo marca en la hoja laminada y esa hoja se queda en la carpeta. Yo copio el total de horas a «Control de flota» cuando alguien leyó la pantalla. FlightHub lo mira operaciones para la ubicación. A mantenimiento no le entra.

Técnicos. No hay dónde consultar si la habilitación sigue vigente. No vence en un registro. La Aeronáutica no les pide licencia de mecánico. El alcance es el puesto: dos de motores, uno de baterías, uno de bombas, uno de electrónica, y los de línea en las bases. Lo sé porque yo los puse ahí. Para un motor miro quién está en Palmira, no una pantalla.

Autoridad. A mí no me entra una directiva de la Aeronáutica. Me entra un mensaje de seguridad o del gerente: este dron no sale, por registro, por póliza o por incidente. El boletín de fábrica es otra cosa: llega del distribuidor, por WhatsApp o por correo, y lo comparo yo con los seriales de la hoja. Les sale el expediente solo cuando seguridad lo pide, una vez al año o si hubo incidente. Yo ordeno la carpeta. Ellos la mandan. No hay API. Yo no entro al portal. El registro de un dron nuevo lo hace seguridad en línea. Yo les doy serial y modelo, y me guardan la copia detrás de las órdenes.

Correctivo. No hay un correctivo aparte que me mande la falla y espere el hallazgo. La falla llega en el mensaje del piloto, o la escribe el técnico al recibir el dron, o aparece en las 50 horas, en la misma orden. El hallazgo se queda en ese papel. Al coordinador le pasa una frase. Al piloto no le devuelvo la probeta ni el serial de la pieza. Al cliente tampoco. Si el reclamo es de dosis, operaciones pide la última probeta y esa sí sale, junto con el resumen de la app.

Diario, los días que se vuela: el cruce con operaciones en «Programa» y la novedad del piloto en «Novedades campo». Copiar las horas a la hoja también es del día, y muchas veces no se hace. Semanal es el recuento de baterías, los lunes, en Palmira. Eventual: la compra y el costo en Siigo, el pedido y la garantía con Bogotá, el boletín del distribuidor, el mensaje de seguridad cuando hay papeles o incidente, y la probeta cuando reclaman la dosis. En la práctica no existe el código de bodega, la existencia que vuelve sola, la API con la Aeronáutica, la consulta de habilitación del técnico, la telemetría entrando sola a mis registros, y un correctivo al que yo le responda con el hallazgo. El ICA tampoco cruza con el taller.

## User

Cierre de validación
Si tuvieras que decir qué no debe hacer este software, ¿qué dejarías por fuera?
¿Qué decisión de las que me contaste no puede fallar, aunque falle todo lo demás?

## Assistant

Dejaría por fuera todo lo que el taller no decide y todo lo que un programa no tiene cómo saber.

No programa fincas, no promete al cliente y no factura hectáreas. Eso es del coordinador y de comercial, en el grupo «Programa» y en Siigo. Al programa le basta el número del dron, si sale, y el límite si sale condicionado. No le metería el despiece ni las reglas de las 50 horas.

No reemplaza la app del Agras ni FlightHub. Las horas, el caudal y la alerta de batería nacen en el control. Tampoco reemplaza la estantería ni Siigo. No inventa existencia, ni costo, ni fecha de llegada. No pide por código de bodega: pedimos bomba de T50 o par de hélice, y la pieza se ve en Palmira o la confirma la base.

No habla con la Aeronáutica ni con el ICA. No entra al portal, no radica la orden, no revisa la póliza solo y no mira la etiqueta del agroquímico. El registro, la carpeta y el oficio los sigue sacando seguridad. La dosis la sigue poniendo el agrónomo.

No lleva la habilitación de los técnicos, porque no existe ese registro. No da de baja una batería por su cuenta, no cruza pieza entre T40 y T50, no abre garantía con Bogotá y no actualiza firmware. No suma el mensaje del piloto con la app. Si falta el costo o no se contaron las fallas, no publica cero.

La decisión que no puede fallar es soltar el vuelo. Motor, bomba, batería y electrónica no salen porque el técnico firmó, porque la finca ya está vendida o porque el piloto quiere terminar el lote. Sin mi visto bueno en «Programa», el coordinador no lo arma. Si yo no contesto, se queda en tierra. Puede fallar la hora copiada, la foto en OneDrive, el costo en Siigo o el papel que se quedó en Espinal. Ese dron, aun así, no despega.