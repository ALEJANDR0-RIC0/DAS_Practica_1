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

* RF-01: Acceso a la BBDD mediante componente Gateway
* RF-02: Acceder a la base de datos de “Clientes”
* RF-04: Visualizar los datos personales de los clientes

## Considered Options

* 0003-1 - Singleton: Asegura que solo exista una instancia de una clase en todo el sistema, proporcionando un punto de acceso global a esa instancia.
* 0003-2 - Builder: Permite construir objetos complejos paso a paso y es útil cuando un objeto requiere múltiples configuraciones o propiedades.


## Pros and Cons of the Options

### Opción 1 - Singleton

* **Ventajas**:
  - Asegura una única instancia de un recurso, simplificando el acceso y reduciendo la carga de memoria.
  - Facilita el control centralizado de ciertos recursos, como la configuración global o el manejo de conexiones.

* **Desventajas**:
  - Dificulta las pruebas, ya que el Singleton mantiene una única instancia en el sistema, lo que limita la capacidad de aislamiento en pruebas.
  - Puede llevar a un acoplamiento innecesario si se usa excesivamente, afectando la flexibilidad del sistema.

### Opción 2 - Builder

* **Ventajas**:
  - Permite construir objetos complejos de manera controlada y flexible, útil cuando se requiere configuración detallada.
  - Mejora la legibilidad del código al hacer que la creación de objetos sea clara y ordenada.

* **Desventajas**:
  - No asegura una única instancia de un objeto, lo cual no cumple con el objetivo de tener un solo punto de acceso para ciertas funcionalidades.
  - Añade complejidad innecesaria en casos donde no se requiere un objeto con múltiples configuraciones.

## Decisión

**Opción elegida: Builder (Opción 2)**, ya que permite la creación de objetos con configuraciones específicas y controladas, asegurando flexibilidad y adaptabilidad en escenarios donde las configuraciones pueden variar. Es particularmente adecuado para crear múltiples instancias con propiedades específicas, beneficiando a un sistema distribuido.

## Consecuencias

### Consecuencias Positivas

* **Flexibilidad**: El patrón Builder permite una construcción detallada y específica de objetos, adaptando el sistema a diferentes configuraciones.
* **Legibilidad del Código**: Facilita la comprensión y mantenimiento al hacer explícita la creación de objetos.
* **Escalabilidad**: Al permitir múltiples instancias configuradas individualmente, asegura la capacidad de manejar demandas variables y optimizar el uso de recursos.

### Consecuencias Negativas

* **Complejidad Añadida**: La implementación del patrón Builder puede ser más compleja comparada con el Singleton, especialmente cuando no se requiere configuración detallada.
* **Sobrecarga de Configuración**: Si se abusa del patrón, puede añadir complejidad innecesaria en configuraciones simples, afectando la simplicidad en algunas áreas del sistema.