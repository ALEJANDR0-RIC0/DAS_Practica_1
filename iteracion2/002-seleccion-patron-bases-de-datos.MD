# 0002-Selección-Base-de-Datos

# Elección de la arquitectura de base de datos
* Parent: Opciones
* Status: proposed
* Date: 2024-11-07
* Decision-Makers: Alejandro Rico, Daniel Rong
* Consulted: Elena Ceinos, Gaizka Aranbarri
* Informed: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor


## Context and Problem Statement

Dado que la compañía de productos alimenticios ha decidido migrar de una arquitectura monolítica a una basada en microservicios, se ha evaluado el uso de una base de datos independiente para cada microservicio (**Database per Service**) frente al uso de una base de datos compartida (**Shared Database**). 

El objetivo de esta decisión es seleccionar la opción de arquitectura de base de datos que mejor se adapte a los requisitos de escalabilidad, rendimiento y simplicidad operativa del sistema.

## Decision Drivers

* RF-02 - Acceder a la base de datos de Clientes.
* RF-05 - Realizar pedidos.
* RF-12 - Organizar ruta.
* RF-14, RF-15, RF-16 - Mostrar estadísticas de distintos servicios.
* RF-17, RF-21 - Reportar y gestionar incidencias.

## Considered Options

* **0001-1 - Database per service**: Cada microservicio tendría su propia base de datos.
* **0001-2 - Shared database**: Uso de dos bases de datos compartidas.
## Pros and Cons of the Options

### 0001-1 - Database per service

* **Good**: Cada microservicio tiene control total sobre su base de datos, lo que permite un desacoplamiento completo y facilita la independencia del servicio.
* **Good**: La optimización de la base de datos se puede adaptar a las necesidades específicas de cada microservicio, mejorando potencialmente el rendimiento en consultas y transacciones específicas.
* **Bad**: Requiere un mecanismo de sincronización y consistencia de datos entre bases de datos, especialmente para datos compartidos entre servicios como **Clientes** y **Pedidos**.
* **Bad**: Aumenta la complejidad de la infraestructura y los costos de mantenimiento, ya que es necesario gestionar múltiples bases de datos, lo cual puede ser complejo y costoso en el contexto de este proyecto.

### 0001-2 - Shared database

* **Good**: Centraliza los datos en dos bases de datos compartidas, simplificando la gestión y evitando la necesidad de sincronización entre bases de datos.
* **Good**: Reduce los costos de infraestructura y mantenimiento, al evitar la duplicación de bases de datos y alinear la estructura con la actual.
* **Bad**: Introduce acoplamiento entre los microservicios, lo cual puede dificultar la escalabilidad y la independencia de los servicios.
* **Bad**: Puede generar problemas de contención y afectar el rendimiento si varios servicios acceden simultáneamente a la misma base de datos, especialmente en los módulos críticos como **Pedidos** y **Clientes**.

## Decision Outcome

Chosen option: **0001-2 - Shared database**, utilizando dos bases de datos compartidas: una para **Clientes** y **Pagos** y otra para **Pedidos**. Esta opción se alinea mejor con los requisitos del sistema, minimizando la complejidad de sincronización de datos y optimizando los recursos de infraestructura.

### Consequences

### Positive Consequences

* **Centralización**: La centralización de datos simplifica la gestión, reduce la duplicación y minimiza el esfuerzo de sincronización entre bases de datos.
* **Optimización de Recursos**: Reduce los costos y el esfuerzo de infraestructura, al evitar la creación y gestión de múltiples bases de datos para cada microservicio.
* **Consistencia de Datos**: La centralización en bases de datos compartidas asegura la consistencia de los datos para servicios que necesitan acceder a la misma información.

### Negative Consequences

* **Acoplamiento entre Servicios**: Al utilizar bases de datos compartidas, se reduce la independencia de cada microservicio, lo que puede hacer que los cambios en los datos afecten a varios servicios.
* **Contención y Rendimiento**: Los problemas de contención pueden ser una preocupación, ya que los servicios críticos pueden competir por el acceso a los mismos datos en la base de datos, afectando el rendimiento en momentos de alta demanda.
* **Dificultad para Escalar Individualmente**: Esta estructura limita la capacidad de escalar individualmente los servicios de acuerdo a sus necesidades específicas, ya que la base de datos compartida se convierte en un cuello de botella en ciertos escenarios.

