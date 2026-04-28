---
title: Política de CORS
date: 2026-04-27
tags: [cors, seguridad, web, frontend, backend, http]
alias: [CORS Policy, Cross-Origin Resource Sharing]
---

# Política de CORS

## Definición

**CORS** (Cross-Origin Resource Sharing, o Intercambio de Recursos de Origen Cruzado) es un mecanismo de seguridad implementado en los navegadores web que restringe las solicitudes HTTP realizadas desde un origen (dominio, protocolo, puerto) diferente al que sirvió la página web actual. La **Política de CORS** define qué orígenes, métodos HTTP y encabezados están permitidos para acceder a los recursos de un servidor.

## ¿Por qué es Necesario CORS?

Los navegadores implementan la "política del mismo origen" (Same-Origin Policy - SOP) para prevenir ataques como la falsificación de solicitudes entre sitios (CSRF). SOP permite que los scripts de una página web accedan a datos de otra página solo si ambas tienen el mismo origen. CORS es una forma controlada de relajar esta política, permitiendo la comunicación entre orígenes diferentes de manera segura.

## Cómo Funciona

Cuando un navegador detecta una solicitud de origen cruzado (cross-origin request), añade un encabezado `Origin` a la solicitud. El servidor, si está configurado para CORS, responde con un encabezado `Access-Control-Allow-Origin` que indica qué orígenes están permitidos.

Para solicitudes "preflight" (que modifican datos, como POST, PUT, DELETE), el navegador primero envía una solicitud `OPTIONS` para preguntar al servidor si la solicitud real está permitida.

### Encabezados CORS Clave

-   `Access-Control-Allow-Origin`: Indica qué orígenes pueden acceder al recurso. Puede ser `*` (cualquier origen) o una lista específica de dominios.
-   `Access-Control-Allow-Methods`: Indica qué métodos HTTP (GET, POST, PUT, DELETE) están permitidos.
-   `Access-Control-Allow-Headers`: Indica qué encabezados HTTP personalizados están permitidos.
-   `Access-Control-Allow-Credentials`: Indica si el navegador debe enviar cookies o encabezados de autorización con la solicitud.
-   `Access-Control-Expose-Headers`: Indica qué encabezados del servidor pueden ser expuestos al cliente.

## Uso en el Sistema de Ticketera

En nuestro proyecto, la política de CORS es crucial para permitir la comunicación segura entre:

1.  **Frontend ([[nextjs]]) y Backend ([[nestjs]])**: Nuestro frontend se ejecuta en un dominio diferente al de nuestro backend API.
2.  **Frontend y [[cloudflare-r2]]**: Si el frontend necesita realizar subidas directas a R2 o acceder a recursos públicos.

### Configuración en el Backend (NestJS)

En NestJS, CORS se configura típicamente en el archivo `main.ts` o a través de un middleware.

```typescript
// src/main.ts
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);

  app.enableCors({
    origin: [
      'http://localhost:3000', // Desarrollo local del frontend
      'https://nuestro-frontend-dev.com', // Entorno de desarrollo
      'https://nuestro-frontend-prod.com', // Entorno de producción
    ],
    methods: 'GET,HEAD,PUT,PATCH,POST,DELETE',
    credentials: true, // Si se usan cookies o encabezados de autorización
  });

  await app.listen(3001);
}
bootstrap();
```

### Configuración en Cloudflare R2

Para permitir que el frontend acceda directamente a [[cloudflare-r2]] (ej. para subidas directas con [[url-firmada|URLs firmadas]]), se debe configurar una política de CORS en el bucket de R2.

```json
[
  {
    "AllowedHeaders": ["*"],
    "AllowedMethods": ["GET", "PUT", "POST", "DELETE"],
    "AllowedOrigins": [
      "http://localhost:3000",
      "https://nuestro-frontend-dev.com",
      "https://nuestro-frontend-prod.com"
    ],
    "ExposeHeaders": [],
    "MaxAgeSeconds": 3000
  }
]
```

## Mejores Prácticas

### [!tip] Orígenes Específicos
-   Siempre especificar los `AllowedOrigins` en lugar de usar `*` en entornos de producción para mayor seguridad.
-   Asegurarse de incluir todos los dominios donde se ejecutará el frontend.

### [!tip] Métodos y Encabezados Necesarios
-   Permitir solo los `AllowedMethods` y `AllowedHeaders` que sean estrictamente necesarios.

### [!tip] Credenciales
-   Si el frontend necesita enviar cookies o encabezados de autorización (ej. JWT), configurar `credentials: true` en el backend y `Access-Control-Allow-Credentials: true` en el servidor.

## Solución de Problemas Comunes

### [!warning] Error de CORS en el Navegador
-   **Síntoma**: El navegador bloquea una solicitud con un mensaje como "Access to XMLHttpRequest at '...' from origin '...' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource."
-   **Solución**:
    1.  Verificar que el origen del frontend esté incluido en la lista `AllowedOrigins` del backend o del servicio de almacenamiento.
    2.  Asegurarse de que los métodos HTTP y encabezados utilizados por el frontend estén permitidos.
    3.  Si se usan credenciales, verificar que `credentials: true` esté configurado correctamente.

## Relación con Otros Conceptos

- [[seguridad-de-datos]] - CORS es un mecanismo de seguridad web fundamental.
- [[nextjs]] - Nuestro frontend que inicia solicitudes cross-origin.
- [[nestjs]] - Nuestro backend que debe configurar la política de CORS.
- [[cloudflare-r2]] - Servicio de almacenamiento que también requiere configuración de CORS para acceso directo desde el frontend.
- [[http]] - Protocolo sobre el que opera CORS.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*