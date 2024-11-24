# 0013-eleccion-metodo-login

## Cómo se debe llevar a cabo el login

* Status: Accepted  
* Date: 2024-11-24  
* Decision-Makers: Alejandro Rico, Daniel Rong  
* Consulted: Elena Ceinos, Gaizka Aranbarri  
* Informed: Jon Mazcuñán, Alberto Acebes, Pablo Villamayor  

## Context and Problem Statement

La compañía necesita un sistema de login seguro y eficiente para autenticar a los usuarios que acceden a los microservicios desde las aplicaciones cliente (PC y móvil). El sistema de login debe ser capaz de manejar múltiples métodos de autenticación y garantizar la seguridad de las credenciales de los usuarios. Además, dependiendo del tipo de usuario que inicie sesión, se debe permitir el acceso a diferentes métodos y funcionalidades según su rol o nivel de privilegios.

## Decision Drivers

* RF-21: Iniciar sesión
* Diferenciación de acceso según el rol del usuario (administrador, cliente, gestor, etc.).
* Facilidad de uso para los usuarios finales.

## Considered Options

* 0013-1-Autenticación basada en JWT (JSON Web Tokens) y control de acceso mediante roles.
* 0013-2-Autenticación mediante OAuth2 y permisos delegados.
* 0013-3-Sistema de login tradicional con sesiones basadas en cookies y control de acceso basado en roles.

## Pros and Cons of the Options

### 0013-1-Autenticación basada en **JWT (JSON Web Tokens)**

* **Good** porque proporciona un sistema sin estado (stateless), lo que mejora la escalabilidad de los microservicios.
* **Good** porque es compatible con una arquitectura de microservicios y permite la delegación de accesos de manera eficiente.
* **Bad** porque requiere la gestión segura de las claves privadas y la implementación de un sistema de renovación de tokens.
* **Bad** porque la gestión de revocación de tokens puede ser compleja.

### 0013-2: Autenticación mediante **OAuth2** y permisos delegados

* **Good** porque es un estándar ampliamente utilizado y es ideal para integrarse con otros servicios externos, como proveedores de identidad (Google, Facebook).
* **Good** porque permite la delegación de autenticación sin compartir credenciales.
* **Bad** porque la implementación es más compleja y requiere una infraestructura de autorización.
* **Bad** porque el sistema depende de un tercero para la autenticación, lo que podría introducir problemas de disponibilidad.

### 0013-3: Sistema de login tradicional con **cookies** y control de acceso basado en roles

* **Good** porque es una solución sencilla y ampliamente conocida que se adapta bien a arquitecturas monolíticas.
* **Good** porque permite gestionar el acceso por sesión de usuario y roles de manera sencilla.
* **Bad** porque no es ideal para una arquitectura de microservicios, ya que introduce dependencia en un servidor centralizado de sesiones.
* **Bad** porque la escalabilidad puede ser limitada al manejar sesiones en servidores de backend.

## Decision Outcome

* **Chosen option:** "0013-3-Sistema de login tradicional con cookies y control de acceso basado en roles"

Se ha decidido optar por un sistema de login tradicional basado en cookies debido a su simplicidad, bajo costo y la facilidad de implementación en el contexto actual del proyecto. Aunque no es la solución más escalable para arquitecturas completamente distribuidas, este enfoque satisface los requisitos del sistema y permite una integración rápida con los microservicios ya existentes.

### Positive Consequences

* Solución sencilla y ampliamente conocida, fácil de implementar y mantener.
* Control de acceso a través de roles de usuario utilizando cookies y sesiones.
* Bajo costo de implementación sin necesidad de gestionar infraestructura adicional como servidores de tokens.

### Negative Consequences

* Dependencia de un servidor centralizado de sesiones, lo que puede limitar la escalabilidad en un futuro.
