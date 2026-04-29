---
title: Autorización
date: 2026-04-27
tags: [autorizacion, seguridad, roles, permisos, backend, jwt]
---

# Autorización

## Definición

La **Autorización** es el proceso de determinar qué acciones o recursos un usuario o sistema autenticado tiene permitido realizar o acceder. Una vez que la identidad de un usuario ha sido verificada mediante [[autenticacion|autenticación]], la autorización decide si ese usuario tiene los permisos necesarios para llevar a cabo una operación específica (ej. crear un evento, comprar un ticket, ver un perfil de usuario).

## Importancia en el Sistema de Ticketera

La autorización es un componente crítico de la [[seguridad-de-datos|seguridad]] en nuestro sistema de ticketera:

-   **Control de Acceso**: Asegura que los usuarios solo puedan acceder a los datos y funcionalidades para los que tienen permiso.
-   **Separación de Roles**: Permite definir diferentes tipos de usuarios (ej. asistente, organizador, administrador) con distintos niveles de acceso.
-   **Protección de Datos Sensibles**: Evita que usuarios no autorizados accedan a información confidencial o realicen acciones destructivas.
-   **Cumplimiento**: Ayuda a cumplir con las normativas de privacidad y seguridad.

## Modelos de Autorización Comunes

1.  **Control de Acceso Basado en Roles (RBAC - Role-Based Access Control)**:
    -   Los permisos se asignan a roles (ej. "Organizador", "Asistente", "Administrador").
    -   Los usuarios se asignan a uno o más roles.
    -   Es el modelo más común y flexible para la mayoría de las aplicaciones.

2.  **Control de Acceso Basado en Atributos (ABAC - Attribute-Based Access Control)**:
    -   Los permisos se basan en atributos del usuario, del recurso o del entorno.
    -   Más granular y dinámico que RBAC, pero también más complejo.

3.  **Control de Acceso Discrecional (DAC - Discretionary Access Control)**:
    -   El propietario de un recurso puede otorgar o revocar permisos a otros usuarios.

## Implementación en el Proyecto

En nuestro backend [[nestjs]], la autorización se implementa utilizando una combinación de [[jwt|JSON Web Tokens (JWT)]] y guards.

### Flujo de Autorización con JWT y Guards

1.  **[[autenticacion|Autenticación]]**: El usuario se autentica y recibe un [[jwt|JWT]] que contiene información sobre su identidad y sus roles/permisos en el payload.
2.  **Solicitud a Recurso Protegido**: El frontend [[nextjs]] envía una solicitud al backend con el [[jwt|JWT]] en el encabezado `Authorization`.
3.  **Validación de JWT**: Un guard de autenticación verifica la validez del [[jwt|JWT]].
4.  **Guard de Autorización**: Un guard de autorización (ej. `RolesGuard`) lee los roles/permisos del payload del [[jwt|JWT]] y verifica si el usuario tiene permiso para acceder al recurso o realizar la acción solicitada.
5.  **Acceso/Denegación**: Si el usuario está autorizado, la solicitud procede; de lo contrario, se devuelve un error (ej. `403 Forbidden`).

### Ejemplo de Guard de Roles en NestJS

```typescript
// src/auth/roles.guard.ts
import { Injectable, CanActivate, ExecutionContext } from '@nestjs/common';
import { Reflector } from '@nestjs/core';

@Injectable()
export class RolesGuard implements CanActivate {
  constructor(private reflector: Reflector) {}

  canActivate(context: ExecutionContext): boolean {
    const requiredRoles = this.reflector.get<string[]>('roles', context.getHandler());
    if (!requiredRoles) {
      return true; // No se requieren roles específicos, acceso permitido
    }
    const request = context.switchToHttp().getRequest();
    const user = request.user; // Usuario autenticado, con roles del JWT

    return requiredRoles.some((role) => user.roles.includes(role));
  }
}
```

```typescript
// src/events/events.controller.ts
import { Controller, Post, UseGuards, SetMetadata } from '@nestjs/common';
import { AuthGuard } from '@nestjs/passport';
import { RolesGuard } from '../auth/roles.guard';

@Controller('events')
@UseGuards(AuthGuard('jwt'), RolesGuard) // Aplicar guards de autenticación y autorización
export class EventsController {
  @Post()
  @SetMetadata('roles', ['organizer', 'admin']) // Solo organizadores y administradores pueden crear eventos
  createEvent() {
    // ... lógica para crear evento
  }
}
```

## Mejores Prácticas

### [!tip] Principio de Mínimo Privilegio
-   Otorgar solo los permisos estrictamente necesarios a cada rol o usuario.

### [!tip] Roles Claros y Bien Definidos
-   Definir roles con responsabilidades claras y asignar permisos de forma granular.

### [!tip] Auditoría de Acceso
-   Registrar los intentos de acceso (exitosos y fallidos) para fines de auditoría y seguridad.

### [!tip] Separación de Autenticación y Autorización
-   Mantener estos dos procesos distintos para mayor claridad y flexibilidad.

## Relación con Otros Conceptos

- [[autenticacion]] - La autorización siempre sigue a la autenticación.
- [[jwt]] - Utilizado para transportar información de roles y permisos.
- [[seguridad-de-datos]] - La autorización es un pilar de la seguridad.
- [[nestjs]] - Backend que implementa la lógica de autorización con guards.
- [[nextjs]] - Frontend que interactúa con recursos protegidos.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*