---
title: Variables de Entorno
date: 2026-04-27
tags: [variables-de-entorno, configuración, seguridad, despliegue, devops]
alias: [Environment Variables, Env Vars]
---

# Variables de Entorno

## Definición

Las **Variables de Entorno** son valores dinámicos con nombre que afectan el comportamiento de los procesos que se ejecutan en un sistema operativo. Son una forma estándar de configurar aplicaciones sin modificar su código fuente, lo que es crucial para gestionar configuraciones diferentes entre entornos (desarrollo, staging, producción).

## Importancia en el Proyecto

En nuestro sistema, las variables de entorno son fundamentales para:

-   **Configuración por Entorno**: Permiten que la misma base de código se comporte de manera diferente en desarrollo, staging y producción (ej. URLs de API, claves de base de datos).
-   **Gestión de Secretos**: Almacenan información sensible (claves API, credenciales de base de datos, secretos JWT) de forma segura, sin exponerla en el código fuente.
-   **Portabilidad**: Facilitan el despliegue de la aplicación en diferentes entornos o plataformas (ej. [[Railway]], [[Seenode]], [[Docker]]).

## Ejemplos de Variables de Entorno en el Proyecto

### Backend ([[nestjs]])

-   `DATABASE_URL`: Cadena de conexión a la base de datos (ej. MongoDB).
-   `JWT_SECRET`: Clave secreta para firmar y verificar JSON Web Tokens.
-   `CLOUDFLARE_R2_ENDPOINT`: Endpoint del servicio [[cloudflare-r2]].
-   `CLOUDFLARE_R2_ACCESS_KEY_ID`: ID de la clave de acceso para R2.
-   `CLOUDFLARE_R2_SECRET_ACCESS_KEY`: Clave secreta de acceso para R2.
-   `SENTRY_DSN`: DSN de [[sentry]] para el backend.
-   `NODE_ENV`: Entorno de ejecución (development, production).

### Frontend ([[nextjs]])

-   `NEXT_PUBLIC_API_URL`: URL base de la API del backend.
-   `NEXT_PUBLIC_SENTRY_DSN`: DSN de [[sentry]] para el frontend (debe ser público).
-   `NEXT_PUBLIC_CLOUDFLARE_R2_PUBLIC_URL`: URL pública para acceder a activos en R2.
-   `NODE_ENV`: Entorno de ejecución.

> [!note] Convención `NEXT_PUBLIC_`
> En Next.js, las variables de entorno que comienzan con `NEXT_PUBLIC_` se exponen al navegador. Las demás solo están disponibles en el servidor.

## Gestión de Variables de Entorno

-   **Archivos `.env`**: En desarrollo local, las variables se definen en archivos `.env` (ej. `.env.development`, `.env.production.local`). Estos archivos **nunca deben ser versionados en Git**.
-   **Plataformas de Despliegue**: En entornos de staging y producción, las variables de entorno se configuran directamente en el panel de control de la plataforma de despliegue (ej. [[Railway]], [[Seenode]]). Estas plataformas se encargan de inyectarlas de forma segura en los contenedores de la aplicación.

## Mejores Prácticas

### [!tip] No Versionar Archivos `.env`
-   Añadir `*.env` al `.gitignore` para evitar que los secretos se suban al repositorio.

### [!tip] Usar Nombres Descriptivos
-   Utilizar nombres claros y descriptivos para las variables de entorno (ej. `DATABASE_URL`, no `DB_CONN`).

### [!tip] Separación por Entorno
-   Mantener configuraciones separadas para cada entorno (desarrollo, staging, producción).
-   Las plataformas de despliegue facilitan esto.

### [!tip] Rotación de Credenciales
-   Rotar periódicamente las claves secretas y credenciales almacenadas en variables de entorno.

### [!tip] Validación
-   Validar la presencia y el formato de las variables de entorno al inicio de la aplicación para evitar errores en tiempo de ejecución.

## Relación con Otros Conceptos

- [[Seguridad-de-datos]] - Elemento clave para la protección de secretos.
- [[Gestión-de-credenciales]] - Prácticas para manejar credenciales de forma segura.
- [[Railway]] / [[Seenode]] - Plataformas que gestionan variables de entorno.
- [[Docker]] - Contenedores que consumen variables de entorno.
- [[NestJS]] / [[Next.js]] - Aplicaciones que utilizan variables de entorno.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*