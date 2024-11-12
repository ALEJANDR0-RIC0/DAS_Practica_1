# 0009 - Elección de Patrón para el Sistema de Pedidos en Tres Fases (Preprocesado, Autorización y Aceptación)

* **Status**: Accepted
* **Date**: 2024-11-07
* **Deciders**: Alejandro Rico, Daniel Rong
* **Consulted**: Elena Ceinos, Gaizka Aranbarri
* **Informed**: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor

## Context and Problem statement

* El sistema de pedidos pasa por tres fases secuenciales: Preprocesado, Autorización y Aceptación, asegurando que cada una se completa antes que la anterior.

## Drivers de Decisión

* Asegurar el procesamiento secuencial de cada fase (preprocesado, autorización, aceptación).


## Considered Options

* 0010-1-Utilizar patrón Chain of Responsibility
* 0010-2-Utilizar patrón Event Sourcing

## Pros and Cons of the Options

### 0010-1-Utilizar patrón Chain of Responsibility

* Good, porque permite el desacoplamiento de cada una de las fases así como la adición de más
* Good, porque cada manejador dedcide si pasa a la siguiente fase.

* Bad, porque en procedimientos largos se dificulta el seguimiento
* Bad, porque al crear una instancia de cada manejador de fase, se puede sobrecargar.


### 0010-2-Utilizar patrón Event Sourcing

* Good porque registra cada fase de un pedido.
* Good porque permite la lectura de el estado de un pedido.

* Bad porque la implementación es compleja y pueded plantear problemas de almacenimiento.


## Decision outcome

Chosen option: "0010-2-Utilizar el patrón Event sourcing"

**Opción elegida: Chain of Responsibility**, ya que permite un flujo de procesamiento claro y secuencial de cada fase del pedido (preprocesado, autorización, aceptación), asegurando un desacoplamiento modular y facilitando la adición de nuevas fases sin complejidad adicional en el registro de eventos. Chain of Responsibility se alinea mejor con el requerimiento de un procesamiento secuencial y modular, mientras que Event Sourcing introduce una complejidad innecesaria en este caso.

## Consecuencias

* Good porque permite ver qué eventos ocurrieron y cuándo, facilitando auditorías y diagnóstico de problemas.

* Good porque se asegura un estado preciso y consistente de los pedidos. Esto ayuda a los administradores y sistemas externos a conocer el progreso exacto del proceso de pedidos.

* Good porque la arquitectura basada en eventos puede escalarse mejor, ya que cada evento se procesa de forma independiente. También permite reintentar eventos fallidos sin afectar el flujo general del sistema.

* Bad, porque es complejo ded implementar y puede plantear retos debido al almacenamiento requerido por el registro tan detallado que hace.