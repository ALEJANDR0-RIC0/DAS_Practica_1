# 0011-Elección-patrón-Estadísticas

# Elección de patrón Circuit Braker para conectar los módulos de Pedidos y Pagos del sistema

* **Status**: Accepted
* **Date**: 2024-11-13
* **Deciders**: Alejandro Rico, Daniel Rong
* **Consulted**: Elena Ceinos, Gaizka Aranbarri
* **Informed**: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor

## Context and Problem statement

* El módulo de Pedidos interactuá con el módulo de Pagos, que usa una pasarela externa (Stripe), para llevar a cabo las transacciones. En caso de que el servicio de Pagos esté inactivo o no disponible, las llamadas fallidas pueden afectar negativamente el rendimiento general del sistema. Por lo que es necesario implementar un mecanismo que maneje los fallos en caso de que se colapse el módulo de Pagos, y así evitar sobrecargar el sistema con llamadas.

## Drivers de Decisión

* RF-5: Realizar pedidos
* RF-20: Pagar

## Considered Options

* 0011-1-Patrón Circuit Breaker
* 0011-2-No implementar ningún patrón de diseño y manejar los fallos con reintentos automáticos

## Pros and Cons of the Options

### 0011-1-Patrón Circuit Breaker

* Good, porque permite proteger al sistema cuando ocurren fallos prolongados en el módulo de Pagos al evitar llamadas repetidas al servicio inactivo.
* Good, porque permite que el sistema se recupere y establezca nuevamente de manera correcta.

* Bad, porque añade complejidad al sistema debido a la configuración y gestión de los estados del Circuit Breaker (abierto, medio abierto, cerrado).
* Bad, porque requiere configurar de manera correcta los tiempos de espera para evitar que el patrón sea demasiado restrictivo o demasiado permisivo.

### 0011-2-No implementar ningún patrón de diseño y manejar los fallos con reintentos automáticos

* Good, porque es una implementación simple, ya que consiste en reintentar llamadas fallidas después de un tiempo.
* Good, porque no requiere un estado o una lógica de gestión de circuitos.

* Bad, porque puede sobrecargar el módulo de Pedidos con llamadas repetidas si el servicio de Pagos aún no responde, causando latencia en el redimiento.
* Bad, porque no proporciona una protección efectiva contra fallos prolongados o repetidos, lo que puede generar una mala experiencia para el usuario.

## Decision outcome

* **Chosen option**: 0011-1-Patrón Circuit Breaker
Se integrará el patrón Circuit Breaker entre los módulos Pedidos y Pagos del sistema para garantizar un manejo óptimo del sistema y evitar sobrecargarlo en caso de que el servicio de pagos tenga fallas. 

### Positive Consequences

* Mejora la resiliencia y la estabilidad del módulo de Pedidos al manejar fallos en el módulo de Pagos de manera controlada.
* Evita la sobrecarga del sistema causada por llamadas repetidas a un servicio que no está disponible.

### Negative Consequences

* Requiere una configuración y gestión adecuada para garantizar su correcto funcionamiento.
* Aumenta la complejidad del sistema en términos de monitoreo y gestión.