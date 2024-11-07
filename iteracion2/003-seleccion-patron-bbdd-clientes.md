# Elección de la arquitectura de base de datos
* Parent: Opciones
* Status: proposed
* Date: 2024-11-07
* Decision-Makers: Alejandro Rico, Daniel Rong
* Consulted: Elena Ceinos, Gaizka Aranbarri
* Informed: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor

## Context and Problem Statement

Se requiere conectar la BBDD de clientes con el microservicio Clientes de una manera segura, escalable y eficiente.

## Decision Drivers

* RF-02

## Considered Options

* 0003-1 - Singleton: Asegura que solo exista una instancia de una clase en todo el sistema, proporcionando un punto de acceso global a esa instancia.
* 0003-2 - Builder: Permite construir objetos complejos paso a paso y es útil cuando un objeto requiere múltiples configuraciones o propiedades.


## Pros and Cons of the Options

### 0003-1 - Singleton

* **Good**: Asegura una única instancia de un recurso, simplificando el acceso y reduciendo la carga de memoria.
* **Good**: Facilita el control centralizado de ciertos recursos, como la configuración global o el manejo de conexiones.
* **Bad**: Puede dificultar las pruebas, ya que el Singleton mantiene una única instancia en el sistema, lo que limita la capacidad de aislamiento en pruebas.
* **Bad**: Puede llevar a un acoplamiento innecesario si se utiliza de manera excesiva en el código, afectando la flexibilidad.

### 0003-2 - Builder

* **Good**: Permite construir objetos complejos de manera controlada y flexible, útil cuando se requiere configuración detallada.
* **Good**: Mejora la legibilidad del código al hacer que la creación de objetos sea clara y ordenada.
* **Bad**: No asegura una única instancia de un objeto, lo cual no cumple con el objetivo de tener un solo punto de acceso para ciertas funcionalidades.
* **Bad**: Añade complejidad innecesaria en casos donde no se requiere un objeto con múltiples configuraciones, como en este caso.

## Decision Outcome

Chosen option: **0003-1 - Singleton**, porque proporciona una solución simple y eficaz para garantizar que ciertas clases tengan una única instancia a lo largo del sistema, especialmente útil para el acceso a recursos compartidos y configuración global.

## Consequences

### Positive Consequences

* **Control Centralizado**: El patrón Singleton asegura que solo exista una instancia de ciertas clases, lo que simplifica el acceso y control de recursos compartidos.
* **Eficiencia**: Evita la creación de múltiples instancias del mismo recurso, reduciendo el consumo de memoria y mejorando el rendimiento en áreas donde es necesario tener un único punto de control.
* **Facilidad de Implementación**: Singleton es un patrón simple de implementar, lo que facilita su integración y mantenimiento en el sistema.

### Negative Consequences

* **Dificultad para Pruebas Unitarias**: Las clases Singleton pueden ser difíciles de probar, ya que al ser una única instancia global, puede dificultar el aislamiento en las pruebas.
* **Acoplamiento Global**: Dado que proporciona un punto de acceso global, puede introducir un acoplamiento no deseado si se abusa de su uso, haciendo que el sistema dependa demasiado de esa instancia única.
* **Limitación de Escalabilidad**: Si el Singleton maneja recursos que requieren escalabilidad, como conexiones a bases de datos en entornos de alta demanda, podría convertirse en un cuello de botella.

