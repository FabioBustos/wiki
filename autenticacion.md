---
title: Autenticación
date: 2026-04-27
tags: [autenticacion, seguridad, usuarios, jwt, backend]
---

# Autenticación

## Definición

La **Autenticación** es el proceso de verificar la identidad de un usuario, sistema o entidad que intenta acceder a un recurso o sistema. Es el acto de confirmar que "eres quien dices ser". Este proceso generalmente implica la presentación de credenciales (ej. nombre de usuario y contraseña, token, certificado) que son verificadas contra una fuente de verdad.

## Importancia en el Sistema de Ticketera

La autenticación es un pilar fundamental de la [[seguridad-de-datos|seguridad]] en nuestro sistema de ticketera:

-   **Acceso Controlado**: Asegura que solo los usuarios registrados y verificados puedan acceder a sus perfiles, historial de compras y funcionalidades sensibles.
-   **Personalización**: Permite personalizar la experiencia del usuario basándose en su identidad.
-   **Protección de Datos**: Protege la información personal y financiera de los usuarios.
-   **Autorización**: Es el primer paso para determinar qué acciones puede realizar un usuario (autorización).

## Métodos de Autenticación Comunes

1.  **Basada en Contraseña**: El método más común, donde el usuario proporciona un nombre de usuario y una contraseña. Las contraseñas deben ser almacenadas de forma segura (hasheadas y salteadas).
2.  **Basada en Tokens**: El usuario se autentica una vez y recibe un token (ej. [[jwt|JWT]]) que utiliza para autenticar solicitudes subsiguientes.
3.  **Autenticación de Múltiples Factores (MFA)**: Requiere dos o más factores de verificación para confirmar la identidad del usuario (ej. contraseña + código de un dispositivo móvil).
4.  **OAuth/OpenID Connect**: Para autenticación a través de proveedores de identidad de terceros (ej. Google, Facebook).

## Implementación en el Proyecto

En nuestro backend [[nestjs]], utilizamos la autenticación basada en [[jwt|JSON Web Tokens (JWT)]].

### Flujo de Autenticación con JWT

1.  **Registro/Login**: El usuario envía sus credenciales (email/contraseña) al endpoint de login del backend.
2.  **Verificación**: El backend verifica las credenciales contra la [[base-de-datos|base de datos]].
3.  **Generación de JWT**: Si las credenciales son válidas, el backend genera un [[jwt|JWT]] firmado con una clave secreta.
4.  **Envío de JWT**: El JWT se envía al frontend [[nextjs]].
5.  **Almacenamiento de JWT**: El frontend almacena el JWT (ej. en `localStorage` o `cookies`).
6.  **Acceso a Recursos Protegidos**: En cada solicitud subsiguiente a un recurso protegido, el frontend incluye el JWT en el encabezado `Authorization: Bearer <token>`.
7.  **Validación de JWT**: El backend valida el JWT en cada solicitud para verificar la identidad del usuario.

## Mejores Prácticas

### [!tip] Contraseñas Seguras
-   Forzar el uso de contraseñas fuertes y complejas.
-   Nunca almacenar contraseñas en texto plano; siempre hashearlas y saltearlas.

### [!tip] Autenticación de Múltiples Factores (MFA)
-   Ofrecer MFA como una capa adicional de seguridad, especialmente para cuentas con privilegios.

### [!tip] Gestión de Sesiones
-   Utilizar tokens de corta duración y mecanismos de refresco de tokens para mejorar la seguridad.
-   Implementar mecanismos de revocación de tokens.

### [!tip] Protección contra Ataques
-   Implementar límites de intentos de login para prevenir ataques de fuerza bruta.
-   Utilizar CAPTCHAs.

## Relación con Otros Conceptos

- [[jwt]] - El token utilizado para la autenticación.
- [[seguridad-de-datos]] - La autenticación es un pilar de la seguridad.
- [[autorizacion]] - La autenticación es el primer paso para la autorización.
- [[nestjs]] - Backend que implementa la lógica de autenticación.
- [[nextjs]] - Frontend que gestiona la interfaz de autenticación.
- [[base-de-datos]] - Almacena las credenciales de usuario.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*