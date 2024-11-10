# Cambio en el diseño UML propuesto en la iteración anterior
* Parent: Opciones
* Status: accepted
* Date: 2024-11-06
* Decision-Makers: Alejandro Rico, Daniel Rong
* Consulted: Elena Ceinos, Gaizka Aranbarri
* Informed: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor

## Context and Problem Statement

Durante la iteración anterior, se propuso un diseño UML a un nivel muy alto para el desarrollo del sistema. Sin embargo, a medida que el proyecto avanza y se clarifican los detalles de implementación, surge la necesidad de evaluar si es conveniente realizar cambios en el diseño UML para alinear mejor la estructura del modelo con los requerimientos actuales.

## Decision Drivers

* Mejorar la claridad y el detalle en el modelo para guiar a los desarrolladores en la implementación
* Prevenir problemas que puedan surgir por la implementacion ambigua del diseño ya planteado
* Minimizar el impacto en el tiempo y recursos del equipo, especialmente en los desarrolladores juniors

## Considered Options

* 0005-1-Mantener el diseño UML actual sin cambios
* 0005-2-Cambiar el diseño UML

## Pros and Cons of the Options

### 0005-1-Mantener el diseño UML actual sin cambios

* Good, porque evita el tiempo y el esfuerzo necesario para realizar y documentar cambios en el modelo
* Good, porque permite a los desarrolladores seguir con una estructura conocida y no requiere adaptación adicional
* Bad, porque el modelo actual puede no representar  adecuadamente la arquitectura seleccionada
* Bad, porque puede afectar la capacidad de los arquitectos para prever y resolver problemas de diseño a medida que el proyecto crece en complejidad

### 0005-2-Cambiar el diseño UML
* Good, porque mejora la comprensión del sistema y facilita la implementación correcta de la arquitectura
* Good, porque permite identificar problemas de diseño con anticipación
* Bad, porque requiere tiempo y esfuerzo en un proyecto que ya está en marcha, generando posibles retrasos en las tareas de diseño
* Bad, porque puede generar frustración en los desarrolladores juniors al enfrentar un cambio en el modelo, lo que podría impactar en su productividad

## Decision Outcome

* Chosen option: "0005-2-Cambiar el diseño UML"

### Positive Consequences

* Aumenta la claridad y el alineamiento del diseño UML con los requerimientos y decisiones actuales, ofreciendo una mejor guía para la implementación y el diseño.
* Ayuda a prevenir problemas de diseño futuros al establecer un modelo más detallado, exhaustivo y correcto.
* A largo plazo, un modelo UML bien adaptado a las necesidades reales del sistema mejorar la calidad general del diseño, facilitando las revisiones y las actualizaciones.

### Negative Consequences

* La actualización del modelo consume tiempo que podría dedicarse a continuar con el diseño, afectando potencialmente el cronograma de entrega.
* Un microservicio de mayor tamaño puede requerir un esfuerzo adicional en la gestión de la lógica de negocio y los despliegues, ya que todos los cambios y pruebas afectan la misma base de código.
* Si el nuevo modelo agrega complejidad innecesaria, esto podría llevar a mayores dificultades de mantenimiento y a una percepción de rigidez en futuras iteraciones del diseño.
