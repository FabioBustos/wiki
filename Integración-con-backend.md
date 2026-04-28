---
title: Integración con Backend
date: 2026-04-27
tags: [integración, backend, frontend, arquitectura, comunicación]
---

# Integración con Backend

Este documento describe las estrategias y patrones para la integración entre el frontend y el backend de nuestro sistema.

## Definición

La **Integración con Backend** se refiere a cómo el frontend (desarrollado en [[nextjs]]) se comunica y consume los servicios y datos proporcionados por el backend (desarrollado en [[nestjs]]). Una integración robusta es clave para una experiencia de usuario fluida y una funcionalidad completa.

## Principios Clave

1.  **[[api-rest-especificacion|API RESTful]]**: El backend expone una API RESTful bien definida para que el frontend interactúe con ella.
2.  **Comunicación Clara**: Definir contratos claros (tipos, esquemas) para las solicitudes y respuestas de la API.
3.   **Manejo de Errores**: Implementar estrategias consistentes para manejar errores de la API en el frontend.
4.   **Seguridad**: Asegurar que la comunicación sea segura (HTTPS) y que las solicitudes estén autenticadas/autorizadas.
5.   **Rendimiento**: Optimizar las llamadas a la API para minimizar la latencia y el uso de recursos.

## Patrones de Comunicación

### 1. Solicitudes HTTP Directas

El frontend realiza llamadas HTTP directas a los endpoints del backend.

-   **Herramientas**: `fetch` API, `axios`.
-   **Ejemplo (Frontend [[nextjs]])**:
    ```typescript
    // pages/api/events.ts (o en componentes/servicios)
    async function fetchEvents() {
      try {
        const response = await fetch(`${process.env.NEXT_PUBLIC_API_URL}/events`);
        if (!response.ok) {
          throw new Error(`HTTP error! status: ${response.status}`);
        }
        const data = await response.json();
        return data;
      } catch (error) {
        console.error("Error fetching events:", error);
        // Manejar error, quizás reportar a Sentry
        return [];
      }
    }
    ```
-   **Consideraciones**:
    -   Gestionar variables de entorno (`NEXT_PUBLIC_API_URL`) para la URL base del backend.
    -   Implementar manejo de errores y estados de carga en la UI.

### 2. Comunicación en Tiempo Real ([[websockets]])

Para funcionalidades que requieren actualizaciones instantáneas (ej. notificaciones, chat en vivo).

-   **Tecnología**: WebSockets (implementado en el backend [[nestjs]], consumido en el frontend).
-   **Ejemplo**: El backend puede usar [[nestjs]] Gateway para manejar conexiones WebSocket. El frontend utiliza la API de WebSocket del navegador o bibliotecas como `socket.io-client`.

### 3. Almacenamiento de Archivos

-   **Subida Directa a R2**: El frontend obtiene una URL firmada del backend y sube el archivo directamente a [[cloudflare-r2]].
-   **Proxy a través del Backend**: El frontend envía el archivo al backend, que luego lo sube a R2. Menos eficiente pero puede ser útil si se requiere procesamiento intermedio.

## Manejo de Errores

-   **Códigos de Estado HTTP**: Utilizar códigos estándar (200 OK, 201 Created, 400 Bad Request, 401 Unauthorized, 404 Not Found, 500 Internal Server Error).
-   **Respuestas de Error Estructuradas**: El backend debe devolver mensajes de error claros y consistentes.
    ```json
    // Ejemplo de respuesta de error del backend
    {
      "statusCode": 400,
      "message": "Validation failed",
      "error": "Bad Request",
      "details": {
        "field": "email",
        "message": "Invalid email format"
      }
    }
    ```
-   **Reporte a Sentry**: Capturar errores de red o de la API en el frontend y backend usando [[sentry]].

## Seguridad

-   **HTTPS**: Toda la comunicación debe ser sobre HTTPS.
-   **Autenticación**: Uso de [[jwt]] (JSON Web Tokens) u otros mecanismos para verificar la identidad del usuario.
-   **Autorización**: Verificar que el usuario autenticado tenga permisos para realizar la acción solicitada.
-   **Validación de Entrada**: El backend debe validar rigurosamente todos los datos recibidos del frontend.

## Relación con Otros Conceptos

- [[api-rest-especificacion]]
- [[nestjs]]
- [[nextjs]]
- [[jwt]]
- [[sentry]]
- [[cloudflare-r2]]
- [[websockets]]

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*