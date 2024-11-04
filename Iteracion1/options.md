# 0001-Elección_Arquitectura
* Parent: Opciones
* Status: proposed
* Date: 2024-11-01
* Decision-Makers: Alejandro Rico, Daniel Rong
* Consulted: Elena Ceinos, Gaizka Aranbarri
* Informed: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor



## Context and Problem Statement

La empresa de productos alimenticios quiere cambiar su sistema monolítico a una arquitectura más flexible y escalable. Se han considerado tres opciones principales: arquitectura monolítica, arquitectura por capas y arquitectura de servicios. 

## Decision Drivers

* Necesidad de flexibilidad y escalabilidad
* Complejidad de implementación y mantenimiento
* Costos asociados al cambio
* Desempeño y respuesta
* Gestión de pedidos con reporte de incidencias
* Gestionar los pagos de manera segura mediante Stripe


## Considered Options

* 0001-1-Arquitectura Monolítica
* 0001-2-Arquitectura por Capas
* 0001-3-Arquitectura de Servicios 


## Pros and Cons of the Options

### 0001-1-Arquitectura Monolítica

* Good, because es simple de implementar y gestionar inicialmente.
* Good, porque facilita la comprensión y despliegue del sistema en un solo entorno.
* Bad, because tiene un alto acoplamiento, lo que complica la escalabilidad y la flexibilidad para hacer cambios.
* Bad, porque un fallo en un componente puede afectar a todo el sistema.

### 0001-2-Arquitectura por Capas

* Good, because separa la lógica de presentación, negocio y datos, facilitando la organización del código.
* Good, porque mejora la estructuración y permite una evolución más ordenada del sistema.
* Bad, because las capas están acopladas, lo que puede complicar la escalabilidad independiente.
* Bad, porque un fallo en una capa crítica puede impactar todo el sistema.

### 0001-3-Arquitectura de Servicios 

* Good, porque permite el desacoplamiento de servicios y la integración con nuevas tecnologías.
* Good, porque ofrece reutilización de servicios y mayor flexibilidad en el desarrollo.
* Bad, because requiere un sistema de gobernanza robusto para gestionar la orquestación y la comunicación entre servicios.
* Bad, porque la dependencia de un ESB introduce complejidad y un posible punto de fallo.


## Decision Outcome

Chosen option: "0001-3-Arquitectura de Servicios"

### Positive Consequences

* Permite un mayor desacoplamiento entre módulos, facilitando su mantenimiento y escalabilidad individual.
* Mejora la reutilización de servicios, lo que puede optimizar los recursos y reducir la duplicación de funcionalidades.
* Flexibilidad para integrar tecnologías externas, como la pasarela de pago de Stripe.

### Negative Consequences

* La implementación de la arquitectura de servicios requiere una gestión sólida, lo cual añade complejidad operativa.
* La dependencia del API Gateway es un punto central de acceso para todas las solicitudes entrantes, por lo que es un punto único de fallo.
* Mayor sobrecarga en la comunicación entre servicios, lo que puede impactar en la latencia.

