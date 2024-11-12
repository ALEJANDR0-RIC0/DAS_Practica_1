# Elección del patron de acceso a la base de datos
* Parent: Opciones
* Status: Accepted
* Date: 2024-11-07
* Decision-Makers: Alejandro Rico, Daniel Rong
* Consulted: Elena Ceinos, Gaizka Aranbarri
* Informed: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor

## Context and Problem Statement

Se requiere conectar la BBDD de clientes con el microservicio Clientes de una manera segura, escalable y eficiente.

## Decision Drivers

* RF-01: Acceso a la BBDD mediante componente Gateway
* RF-02: Acceder a la base de datos de “Clientes”
* RF-04: Visualizar los datos personales de los clientes

## Considered Options

* 0003-1 - Singleton
* 0003-2 - Builder


## Pros and Cons of the Options

### Opción 1 - Singleton

* Good, porque asegura una única instancia de un recurso, simplificando el acceso y reduciendo la carga de memoria.
* Good, porque facilita el control centralizado de ciertos recursos, como la configuración global o el manejo de conexiones.

* Bad, porque dificulta las pruebas, ya que el Singleton mantiene una única instancia en el sistema, lo que limita la capacidad de aislamiento en pruebas.
* Bad, porque puede llevar a un acoplamiento innecesario si se usa excesivamente, afectando la flexibilidad del sistema.

### Opción 2 - Builder

* Good, porque permite construir objetos complejos de manera controlada y flexible, útil cuando se requiere configuración detallada.
* Good, porque mejora la legibilidad del código al hacer que la creación de objetos sea clara y ordenada.

* Bad, porque no asegura una única instancia de un objeto, lo cual no cumple con el objetivo de tener un solo punto de acceso para ciertas funcionalidades.
* Bad, porque añade complejidad innecesaria en casos donde no se requiere un objeto con múltiples configuraciones.

## Decision Outcome

Chosen option: "Builder", porque ya que permite la creación de objetos con configuraciones específicas y controladas, asegurando flexibilidad y adaptabilidad en escenarios donde las configuraciones pueden variar. Es particularmente adecuado para crear múltiples instancias con propiedades específicas, beneficiando a un sistema distribuido.

## Consequences

* Good, por dar flexibildad, mejorar la escalabilidad y facilitar la legibilidad del código.

* Bad, por añadir complejidad a la implementación del patrón y por la posible sobrecarga de la configuracion

