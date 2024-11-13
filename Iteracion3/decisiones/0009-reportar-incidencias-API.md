# 0009-reportar-incidencias-API

# Sistema para reportar incidencias

* Status: Accepted
* Date: 2024-11-12
* Decision-Makers: Alejandro Rico, Daniel Rong
* Consulted: Elena Ceinos, Gaizka Aranbarri
* Informed: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor

## Context and Problem Statement

El módulo de incidencias debe reportar eventos críticos, como averías de camiones o repartos no realizados, a los gestores de rutas de manera rápida y fiable. Se evaluaron dos opciones: integrar una API de mensajería existente o desarrollar un sistema propio de notificaciones. Tras un análisis detallado, se ha decidido optar por una API de mensajería para garantizar rapidez de implementación y fiabilidad.

## Decision Drivers

* RF-17: Reportar incidencias
* RF-18: Notificar incidencias
* RF-19: Consultar notificaciones

## Considered Options

* 0009-1-Integrar una API de mensajería existente.
* 0009-2-Desarrollar un sistema propio de notificaciones.

## Pros and Cons of the Options

### 0009-1-Integrar una API de mensajería existente

* **Good** porque permite una implementación rápida utilizando APIs populares como Twilio, Slack o Telegram.  
* **Good** porque ofrece alta fiabilidad y escalabilidad, siendo soluciones probadas y ampliamente utilizadas.  
* **Bad** porque introduce un costo recurrente dependiendo del volumen de mensajes enviados.  
* **Bad** porque limita la personalización del sistema de notificaciones.  

### 0009-2-Desarrollar un sistema propio de notificaciones

* **Good** porque permite personalizar completamente las notificaciones y su integración con el resto del software.  
* **Good** porque no depende de servicios de terceros, eliminando costos recurrentes a largo plazo.  
* **Bad** porque requiere un mayor tiempo y esfuerzo de implementación, lo que podría retrasar otros desarrollos.  
* **Bad** porque aumenta la carga de mantenimiento y la necesidad de garantizar escalabilidad y fiabilidad.  

## Decision Outcome

* **Chosen option**: "0009-1-Integrar una API de mensajería existente"  
Se integrará una API de mensajería, como Twilio para notificaciones SMS o Slack/Telegram para mensajes en tiempo real, asegurando que las incidencias sean reportadas de manera rápida y fiable (queda pendiente decidir la API).

### Positive Consequences

* Se garantiza una implementación más rápida, alineada con los tiempos del proyecto.  
* La solución es altamente fiable y escalable, manejando picos de notificaciones sin problemas.  
* La integración con APIs populares proporciona acceso a funcionalidades avanzadas como logs de mensajes, reintentos automáticos y reportes de estado.

### Negative Consequences

* Se asume un costo recurrente por el uso de la API, que dependerá del volumen de incidencias reportadas.  
* La personalización estará limitada por las características de la API elegida.  