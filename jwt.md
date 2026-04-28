---
title: JWT (JSON Web Token)
date: 2026-04-27
tags: [jwt, autenticacion, autorizacion, seguridad, tokens, backend]
alias: [JSON Web Token]
---

# JWT (JSON Web Token)

## Definición

Un **JWT** (JSON Web Token) es un estándar abierto (RFC 7519) que define una forma compacta y auto-contenida de transmitir información de forma segura entre partes como un objeto JSON. Esta información puede ser verificada y confiable porque está firmada digitalmente. Los JWTs se utilizan comúnmente para la autenticación y autorización en aplicaciones web.

## Estructura de un JWT

Un JWT consta de tres partes separadas por puntos (`.`):

1.  **Header (Cabecera)**: Contiene el tipo de token (JWT) y el algoritmo de firma utilizado (ej. HS256, RS256).
    ```json
    {
      "alg": "HS256",
      "typ": "JWT"
    }
    ```
2.  **Payload (Carga Útil)**: Contiene las "claims" (declaraciones) sobre una entidad (ej. un usuario) y metadatos adicionales. Las claims pueden ser:
    -   **Registradas (Registered Claims)**: Nombres de claims predefinidos (ej. `iss` para emisor, `exp` para expiración, `sub` para sujeto).
    -   **Públicas (Public Claims)**: Definidas por quienes usan JWTs, pero deben ser registradas en el IANA JSON Web Token Registry o ser un URI que contenga un espacio de nombres resistente a colisiones.
    -   **Privadas (Private Claims)**: Claims personalizadas creadas para compartir información entre partes que acuerdan su uso.
    ```json
    {
      "sub": "1234567890",
      "name": "John Doe",
      "admin": true,
      "iat": 1516239022
    }
    ```
3.  **Signature (Firma)**: Se crea codificando la cabecera y la carga útil en Base64Url, concatenándolas con un punto, y luego firmando el resultado con el algoritmo especificado en la cabecera y una clave secreta. La firma se utiliza para verificar que el remitente del JWT es quien dice ser y que el mensaje no ha sido alterado.

El token final se ve así: `xxxxx.yyyyy.zzzzz`

## Cómo Funciona la Autenticación con JWT

1.  **Login**: El usuario envía sus credenciales (ej. nombre de usuario y contraseña) al servidor.
2.  **Generación de JWT**: El servidor verifica las credenciales y, si son válidas, genera un JWT. Este JWT contiene información sobre el usuario (ej. `userId`, `roles`) y una fecha de expiración. El token se firma con una clave secreta del servidor.
3.  **Envío al Cliente**: El servidor envía el JWT al cliente (navegador o aplicación móvil).
4.  **Almacenamiento en Cliente**: El cliente almacena el JWT (ej. en `localStorage` o `cookies`).
5.  **Acceso a Recursos Protegidos**: En cada solicitud subsiguiente a un recurso protegido, el cliente envía el JWT en el encabezado `Authorization` (ej. `Bearer <token>`).
6.  **Verificación en Servidor**: El servidor intercepta la solicitud, verifica la firma del JWT utilizando la misma clave secreta. Si la firma es válida y el token no ha expirado, el servidor extrae la información del usuario del payload y autoriza el acceso al recurso.

## Importancia en el Sistema de Ticketera

JWT es el mecanismo principal para la autenticación y autorización de usuarios en nuestro backend [[nestjs]].

-   **Autenticación de Usuarios**: Permite a los usuarios iniciar sesión y obtener un token para acceder a recursos protegidos.
-   **Autorización de Roles**: El payload del JWT puede contener roles o permisos del usuario, permitiendo al backend controlar el acceso a funcionalidades específicas (ej. solo organizadores pueden crear eventos).
-   **API Stateless**: Al ser un token auto-contenido, el servidor no necesita almacenar el estado de la sesión, lo que facilita la escalabilidad.

## Implementación en [[nestjs]]

[[nestjs]] ofrece módulos y estrategias para implementar JWT de forma sencilla, a menudo utilizando `@nestjs/jwt` y `passport-jwt`.

```typescript
// auth.service.ts (ejemplo simplificado)
import { Injectable } from '@nestjs/common';
import { JwtService } from '@nestjs/jwt';

@Injectable()
export class AuthService {
  constructor(private jwtService: JwtService) {}

  async login(user: any) {
    const payload = { username: user.username, sub: user.userId };
    return {
      access_token: this.jwtService.sign(payload),
    };
  }

  async validateUser(payload: any) {
    // Lógica para validar el usuario a partir del payload del JWT
    return { userId: payload.sub, username: payload.username };
  }
}
```

## Consideraciones de Seguridad

-   **Clave Secreta**: La clave secreta utilizada para firmar el JWT debe ser fuerte y mantenerse estrictamente confidencial.
-   **Expiración**: Los tokens deben tener un tiempo de expiración razonable para limitar la ventana de oportunidad en caso de compromiso.
-   **Almacenamiento en Cliente**: Almacenar JWTs en `localStorage` es susceptible a ataques XSS. Usar `HttpOnly cookies` puede ser más seguro.
-   **Revocación**: Implementar mecanismos de revocación de tokens (ej. listas negras) para invalidar tokens comprometidos antes de su expiración natural.

## Relación con Otros Conceptos

- [[nestjs]] - Backend que implementa la autenticación y autorización con JWT.
- [[seguridad-de-datos]] - JWT es una medida de seguridad clave.
- [[variables-de-entorno]] - La clave secreta de JWT se almacena como variable de entorno.
- [[integracion-con-backend]] - JWT se utiliza para proteger las APIs del backend.
- [[autenticacion]] (I will create this file later if it doesn't exist) - Concepto general de autenticación.
- [[autorizacion]] (I will create this file later if it doesn't exist) - Concepto general de autorización.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*