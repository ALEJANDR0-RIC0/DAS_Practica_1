# 0012-seleccion-API-mensajeria

# Que API de mensajerría utilizar para reportar y gestionar incidencias

* Status: Accepted
* Date: 2024-11-12
* Decision-Makers: Alejandro Rico, Daniel Rong
* Consulted: Elena Ceinos, Gaizka Aranbarri
* Informed: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor

## Context and Problem Statement

Para el módulo de incidencias, es crucial seleccionar una API de mensajería que permita reportar eventos críticos de manera rápida y fiable. Se han considerado varias opciones populares en el mercado, y es necesario evaluar cuál de ellas se adapta mejor a nuestras necesidades.

## Decision Drivers

* RF-17: Reportar incidencias
* RF-18: Notificar incidencias
* RF-19: Consultar notificaciones
* Costo
* Facilidad de integración
* Fiabilidad y escalabilidad

## Considered Options

* 0012-1-Twilio
* 0012-2-Slack
* 0012-3-Telegram

## Pros and Cons of the Options

### 0012-1-Twilio

* **Good** porque ofrece una integración sencilla y rápida para notificaciones SMS.  
* **Good** porque es altamente fiable y escalable, con soporte global.  
* **Bad** porque introduce un costo recurrente por cada mensaje enviado.  
* **Bad** porque puede ser costoso si el volumen de mensajes es alto.  

### 0012-2-Slack

* **Good** porque permite enviar mensajes en tiempo real a canales específicos.  
* **Good** porque es ampliamente utilizado y tiene una buena documentación y soporte.  
* **Bad** porque requiere que los usuarios estén en la plataforma Slack.  
* **Bad** porque puede no ser ideal para notificaciones SMS.  

### 0012-3-Telegram

* **Good** porque permite enviar mensajes en tiempo real y es gratuito.  
* **Good** porque tiene una API robusta y es fácil de integrar.  
* **Bad** porque requiere que los usuarios tengan la aplicación Telegram instalada.  
* **Bad** porque puede no ser tan fiable como Twilio para notificaciones críticas.  

## Decision Outcome

* **Chosen option**: "0012-3-Telegram"  
Se ha decidido utilizar Twilio para las notificaciones SMS debido a su fiabilidad, escalabilidad, facilidad de integración y la gran flexibilidad para añadir más funcionalidades. Aunque introduce un costo recurrente, se considera que los beneficios superan los inconvenientes.

### Positive Consequences

* Implementación rápida y sencilla, alineada con los tiempos del proyecto.  
* Alta fiabilidad y escalabilidad, manejando picos de notificaciones sin problemas.  
* Acceso a funcionalidades avanzadas como logs de mensajes, reintentos automáticos y reportes de estado.

### Negative Consequences

* Costo recurrente por el uso de la API, que dependerá del volumen de incidencias reportadas.  
* La personalización estará limitada por las características de la API elegida.  
