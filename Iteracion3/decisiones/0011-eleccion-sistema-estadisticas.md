# 0011 - Elección de patrón para el módulo de Estadísticas del sistema

* **Status**: Accepted
* **Date**: 2024-11-13
* **Deciders**: Alejandro Rico, Daniel Rong
* **Consulted**: Elena Ceinos, Gaizka Aranbarri
* **Informed**: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor

## Context and Problem statement

* El sistema cuenta con un módulo de estadísticas, el cual debe proporcionar información sobre el estado de los pedidos, situación en tiempo real de los camiones e información valiosa de los clientes.

## Drivers de Decisión

* RF-14: Mostrar estadísticas de pedidos
* RF-15: Mostrar estadísticas de la logística
* RF-16: Mostrar estadísticas de los clientes

## Considered Options

* 0011-1-Patrón CQRS (Command Query Responsibility Segregation)
* 0011-2-Patrón de Vista Materializada

## Pros and Cons of the Options

### 0011-1-Patrón CQRS (Command Query Responsibility Segregation)

* Good, porque separa las operaciones de lectura y escritura, lo que permite que las consultas estadísticamente pesadas no afecten el rendimiento de las operaciones de escritura. 
* Good, porque permite optimización independiente para operaciones de consulta, lo que es ideal para lograr la visualización de los datos en tiempo ideal.

* Bad, porque añade complejidad al sistema, ya que se implementan 2 modelos separados para escritura y lectura.
* Bad, porque puede requerir modelos complejos de sincronización entre ambos modelos, aumentando así los esfuerzos para el mantenimiento.

### 0011-2-Patrón de Vista Materializada

* Good, porque proporciona consultas rápidas al mantener una copia optimizada de los datos.
* Good, porque más simple de implementar que CQRS y no requiere de una separación explícita de modelos de lectura y escritura.

* Bad, porque las vistas materializadas deben mantenerse constantemente actualizadas y de manera inmediata, sino puede generar cierta latencia en los datos.
* Bad, porque no es tan flexible para manejar consultas complejas, en especial si los datos cambian constantemente como es el caso.

## Decision outcome

* **Chosen option**: 0011-1-Patrón CQRS (Command Query Responsibility Segregation)
Se integrará el patrón CQRS para el módulo de Estadísticas del sistema para garantizar la eficiencia a la hora de mostrar en tiempo real la información de los pedidos, situación de los camiones e información de los clientes.

### Positive Consequences

* Mejor rendimiento para consultas de estádisíticas complejas debido a la separación de modelos de lectura y escritura.
* Mayor flexibilidad a la hora de optimizar consultas de estadísticas sin afectar el flujo de transacciones.

### Negative Consequences

* Mayor complejidad en la sincronización entre ambos modelos de comando y consulta.
* Esfuerzo adicional de diseño y manteminimiento.