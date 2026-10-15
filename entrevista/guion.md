# Guion de la entrevista

Empresa simulada: la que el experto fijó al presentarse, CampoAlto S.A.S. Las preguntas están agrupadas por tema. En cada bloque hay una pregunta abierta, una de profundización y una de validación. El bloque de interoperabilidad es aparte, como pide el examen.

La conversación, con las respuestas, está en [conversacion.md](conversacion.md).

## Contexto de la organización

- Abierta. ¿A qué se dedica la empresa y qué cultivos atiende?
- Abierta. ¿Cómo está compuesta la flota: cuántos modelos, qué piezas lleva cada uno y dónde se guarda?
- Profundización. ¿El mantenimiento se hace en base o también en el cultivo?
- Validación. ¿El cliente contrata fumigación, o también contrata el mantenimiento de los drones?

## Proceso de extremo a extremo

- Abierta. ¿Cuál es el camino desde que un dron termina una jornada hasta que vuelve a estar disponible?
- Profundización. ¿En qué momento se decide que una pieza ya toca intervenirla: por horas, por ciclos, por fecha o por cómo se ve?
- Profundización. ¿Cerrar el trabajo del técnico y autorizar el siguiente vuelo son el mismo paso?
- Validación. ¿La inspección que hace el piloto antes de despegar forma parte de este proceso?

## Actores

- Abierta. ¿Quién pide el mantenimiento, quién lo hace y quién autoriza que el dron vuele otra vez?
- Profundización. ¿Cualquier técnico puede firmar cualquier pieza, o el alcance depende del subsistema?
- Validación. ¿El piloto puede devolver el dron al servicio?

## Reglas de negocio

- Abierta. ¿Qué tiene que cumplirse para que un dron se considere disponible?
- Profundización. Si una pieza vence por horas y otra por calendario, ¿cuál manda?
- Profundización. Si el repuesto no llega y ya hay una fumigación vendida, ¿el dron sale igual?
- Validación. ¿Una misma misión puede quedar contada dos veces, una por el piloto y otra por la telemetría? ¿Cuál dato se queda?

## Excepciones

- Abierta. ¿Qué pasa si en el preventivo aparece un daño que la rutina no cubre?
- Profundización. ¿Una directiva del fabricante o de la autoridad puede parar un dron aunque las horas no se hayan cumplido?
- Validación. ¿El preventivo abre la garantía o el correctivo, o solo deja el dron retenido y avisa?

## Indicadores

- Abierta. ¿Con qué cifras sabes si el proceso va bien?
- Profundización. ¿Disponibilidad cuenta los drones en misión o solo los que están en tierra esperando?
- Profundización. ¿Un preventivo hecho a tiempo cuenta como falla para el tiempo medio entre fallas?
- Validación. Si no tienen el costo del repuesto o el registro de fallas, ¿publican el indicador en cero o lo dejan sin calcular?

## Normatividad

- Abierta. ¿Qué les exige la autoridad aeronáutica sobre el mantenimiento de estos drones?
- Profundización. ¿El libro o el expediente se radica en línea o es un trámite aparte?
- Validación. ¿La norma del agroquímico y del ICA entra en este proceso, o se queda en la misión de fumigación?

## Sistemas con los que ya trabajan

- Abierta. ¿Hoy dónde anotan horas, piezas, repuestos y el plan?
- Profundización. ¿Qué se les pierde con esa forma de llevarlo?
- Validación. ¿El software nuevo reemplaza la telemetría y la bodega, o solo recibe datos de ellas?

## Interoperabilidad

- Abierta. ¿Con qué procesos, áreas, sistemas y entidades externas cruza información el mantenimiento?
- Programación de servicios. ¿Qué les piden ustedes y qué les entregan? ¿Les basta saber si el dron está disponible, o también necesitan el despiece y la política?
- Inventario y compras. ¿Ustedes piden un kit de la intervención o un código de bodega? ¿Qué vuelve: existencia, costo, fecha de llegada?
- Telemetría. ¿Qué medidas llegan solas y cuáles sigue anotando el piloto?
- Técnicos. ¿Dónde se consulta si la habilitación sigue vigente y para qué subsistema?
- Autoridad. ¿Qué les entra (directivas) y qué les sale (expediente)? ¿Hay una API?
- Correctivo. ¿Les llega el dato de falla y ustedes les pasan el hallazgo?
- Validación. De esa lista, ¿cuál cruce es diario, cuál es eventual y cuál en la práctica no existe?

## Cierre

- Si tuvieras que decir qué no debe hacer este software, ¿qué dejarías por fuera?
- ¿Qué decisión de las que contaste no puede fallar, aunque falle todo lo demás?
