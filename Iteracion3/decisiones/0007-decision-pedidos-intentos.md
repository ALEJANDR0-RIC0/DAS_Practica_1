# 0007-decision-pedidos-intentos


# Elección de patron para el intento de pedidos
* Status: Accepted
* Date: 2024-11-12
* Decision-Makers: Alejandro Rico, Daniel Rong
* Consulted: Elena Ceinos, Gaizka Aranbarri
* Informed: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor
---

## Context and Problem Statement
* Necesidad de reintentar realizar un pedido si éste fallaPer. Permitir un máximo de tres intentos.

## Considered Options

* **0007-1-utilizar-patron-retry**
* **0007-2-utilizar-patron-retry-con-circuit-breaker**

## Decision Outcome

Chosen option: 
"0007-2-utilizar-patron-retry-con-circuit-breaker"

### Consequences

* Good, because el patrón retry permite lcontrolar el numero de intentos fallidos.
* Good, porque Circuit Breaker asegura que los reintentos se interrumpan en caso de fallos críticos, evitando la sobrecarga del sistema y permitiendo que los recursos se restablezcan antes de procesar nuevos intentos.

* Bad, por la complejidad de la implementacion.
* Bad, por el posible aumento de la latencia en caso de fallo.