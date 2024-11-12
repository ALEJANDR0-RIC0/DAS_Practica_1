# 0006-Utilización-Cliente-Servidor

# Elección de arquiterctura de cliente-servidor
* Status: Proposed
* Date: 2024-11-12
* Decision-Makers: Alejandro Rico, Daniel Rong
* Consulted: Elena Ceinos, Gaizka Aranbarri
* Informed: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor
---

## Context and Problem Statement
El sistema actual de la empresa alimenticia está basado en una arquitectura monolítica que resulta rígida y difícil de escalar. Para mejorar la flexibilidad y la capacidad de respuesta ante demandas crecientes, se está evaluando el diseño de una nueva arquitectura para el sistema.
La arquitectura cliente-servidor se propone como una solución, en la que los clientes (aplicaciones móviles y de escritorio) se conecten a servidores centralizados para realizar operaciones como gestionar pedidos, consultar rutas, procesar pagos, y visualizar estadísticas.

## Considered Options

* **0006-1-utilizar-arquitectura-cliente-servidor**

## Decision Outcome

Chosen option: "0006-1-utilizar-arquitectura-cliente-servidor"

### Consequences

### Positive Consequences

* Reducción de duplicación: Al centralizar la lógica en el servidor, se evita duplicar funciones críticas como la gestión de rutas o el procesamiento de pagos en los clientes.
* Escalabilidad del cliente: Permite soportar una mayor variedad de plataformas de cliente (PC, móvil, tabletas) con una interacción mínima, ya que la lógica principal está en el servidor.
* Soporte a múltiples clientes simultáneos: Es ideal para manejar un gran número de usuarios simultáneos con peticiones diversas, como pedidos o consultas de rutas.


### Negative Consequences

* Requerimientos de conectividad: Los clientes necesitan una conexión constante y confiable para interactuar con el servidor, lo que podría ser problemático en áreas con baja conectividad.
* Complejidad en la sincronización: Si los clientes necesitan operar parcialmente offline, mantener la consistencia de datos entre cliente y servidor añade complejidad.

