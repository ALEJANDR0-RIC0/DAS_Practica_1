# 0008-control-algortimos-rutas

# Elección de como se van a controlar los algoritmos de rutas

* Status: Accepted
* Date: 2024-11-12
* Decision-Makers: Alejandro Rico, Daniel Rong
* Consulted: Elena Ceinos, Gaizka Aranbarri
* Informed: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor

## Context and Problem Statement

La compañía de productos alimenticios está migrando a una arquitectura basada en microservicios. Uno de los componentes clave es el manejo de los algoritmos de rutas para los camiones de reparto. Existen dos algoritmos diferentes para gestionar las rutas, y la selección de cuál utilizar depende de la demora del camión. Se necesita una solución flexible que permita cambiar entre estos algoritmos en tiempo de ejecución, y que facilite la integración de nuevos algoritmos en el futuro.

## Decision Drivers
`
* RF-12: Organizar ruta
* Flexibilidad para cambiar entre los dos algoritmos de rutas en función de las condiciones.

## Considered Options

* 0008-1-Utilizar Patrón Strategy
* 0008-2-Utilizar Patrón Factory
* 0008-3-Utilizar Dependency Injection

## Pros and Cons of the Options

### 0008-1-Utilizar Patrón Strategy

* **Good** porque permite cambiar de algoritmo en tiempo de ejecución, ofreciendo flexibilidad para adaptarse a diferentes condiciones de los camiones.
* **Good** porque encapsula cada algoritmo en su propia clase, lo que facilita su mantenimiento y extensión en el futuro.
* **Bad** porque introduce un mayor número de clases y puede aumentar la complejidad inicial del diseño.

### 0008-2-Utilizar Patrón Factory

* **Good** porque centraliza la lógica de selección del algoritmo, lo que facilita la modificación de las condiciones que determinan cuál algoritmo usar.
* **Bad** porque introduce un mayor acoplamiento entre las clases que utilizan los algoritmos y la fábrica que los genera.
* **Bad** porque puede resultar más difícil de probar, ya que la lógica de selección del algoritmo está encapsulada en la fábrica.

### 0008-3-Utilizar Dependency Injection

* **Good** porque desacopla los algoritmos de rutas de las clases que los utilizan, facilitando la prueba y la gestión de dependencias.
* **Bad** porque requiere un mayor esfuerzo de implementación y comprensión del patrón de inyección de dependencias.

## Decision Outcome

* **Chosen option**: "0008-1-Utilizar Patrón Strategy"

### Positive Consequences

* **Flexibilidad**: Permite cambiar entre los algoritmos de rutas sin afectar la lógica de negocio, y se pueden añadir nuevos algoritmos sin modificar las clases existentes.
* **Mantenibilidad**: Cada algoritmo está encapsulado en su propia clase, lo que facilita la localización de problemas y la actualización de algoritmos sin impacto en el resto del sistema.
* **Escalabilidad**: Se pueden intercambiar los algoritmos en tiempo de ejecución sin suponer retrasos o tiempos de carga excesivos.

### Negative Consequences

* **Complejidad inicial**: La implementación del patrón Strategy puede ser más compleja debido a la creación de nuevas clases y la definición de interfaces, lo que puede retrasar el desarrollo inicial.
* **Número de clases**: El número de clases puede aumentar al tener una clase por cada algoritmo, lo que puede hacer que la gestión del código se vuelva más compleja si no se organiza adecuadamente.
