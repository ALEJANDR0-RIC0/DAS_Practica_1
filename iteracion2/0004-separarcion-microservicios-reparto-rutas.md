# Separación de microservicios de reparto y rutas
* Parent: Opciones
* Status: proposed
* Date: 2024-11-06
* Decision-Makers: Alejandro Rico, Daniel Rong
* Consulted: Elena Ceinos, Gaizka Aranbarri
* Informed: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor

## Context and Problem Statement

Se sugiere la consideración de dividir el microservicio de Reparto y Rutas en dos microservicios independientes: uno de Reparto y otro de Rutas. Sin embargo, dado el carácter y la interdependencia de las funcionalidades, se evaluará si es más adecuado mantener ambos componentes en un único microservicio.

## Decision Drivers

* RF-12: Organizar rutas
* RF-13: Mostrar rutas
* RF-17: Reportar incidencias
* RF-21: Gestionar incidencias
* Escalabilidad y eficiencia operativa 
* Simplicidad y facilitar el mantenimiento

## Considered Options

* 0004-1-Mantener un único microservicio de Reparto y Rutas
* 0004-2-Separar en dos microservicios: uno de Reparto y otro de Rutas

## Pros and Cons of the Options

### 0004-1-Mantener un único microservicio de Reparto y Rutas

* Good, porque evita la complejidad de gestionar comunicaciones adicionales entre servicios independientes.
* Good, porque simplifica la integración de funcionalidades que dependen unas de otras, como la planificación de rutas y la ejecución de entregas.
* Bad, porque una mayor concentración de funciones puede impactar la claridad de responsabilidades.
* Bad, porque puede aumentar el tiempo de implementación de cambios menores al tener una base de código más grande.

### 0004-2-Separar en dos microservicios: Reparto y Rutas
* Good, porque asigna responsabilidades más específicas y favorece una arquitectura modular y la realización de cambios.
* Good, porque facilita la actualización independiente de los módulos de reparto o rutas si se presentan mejoras específicas en uno de ellos.
* Bad, porque eleva los costos y la complejidad en infraestructura y orquestación para manejar dos servicios separados.
* Bad, porque aumenta la complejidad en la orquestación, al requerir la sincronización de servicios independientes para la gestión de incidencias y ajustes de ruta.

## Decision Outcome

* Chosen option: "0004-1-Mantener un único microservicio de Reparto y Rutas"

### Positive Consequences

* La integración de las funciones de reparto y rutas en un solo microservicio permite un acceso más fácil a las incidencias y hay una optimización en la planificación de entregas.
* Al reducir la cantidad de servicios, se optimizan los recursos y se simplifica la infraestructura, manteniendo el diseño de la arquitectura más sencillo y eficiente.
* Se minimiza la latencia de comunicación, mejorando la eficiencia en tiempo real y reduciendo la necesidad de sincronización compleja entre microservicios.

### Negative Consequences

* La unificación de las funciones de reparto y rutas en un solo microservicio puede conllevar desafíos a largo plazo si se requieren modificaciones muy específicas en alguna de estas áreas, a la vez que dificultan posibles actualizaciones.
* Un microservicio de mayor tamaño puede requerir un esfuerzo adicional en la gestión de la lógica de negocio y los despliegues, ya que todos los cambios y pruebas afectan la misma base de código.