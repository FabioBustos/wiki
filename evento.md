---
title: Evento (Sentry)
date: 2026-04-27
tags: [sentry, evento, error, monitoreo, observabilidad]
---

# Evento (Sentry)

## Definición

En el contexto de [[sentry|Sentry]], un **Evento** es una ocurrencia discreta de algo que sucede en tu aplicación y que es reportado a la plataforma de Sentry. Los eventos pueden ser errores (excepciones, fallos), mensajes (logs), o transacciones de rendimiento. Cada evento contiene un conjunto de datos que describen lo que sucedió, cuándo sucedió y en qué contexto.

## Tipos de Eventos

1.  **Errores (Errors)**:
    -   Representan excepciones no manejadas, fallos de la aplicación o mensajes de error explícitos.
    -   Contienen el stack trace, tipo de error, mensaje y contexto adicional.
    -   Ejemplo: Una excepción `TypeError` en el frontend o un `Internal Server Error` en el backend.

2.  **Transacciones (Transactions)**:
    -   Representan una unidad de trabajo o una operación que se monitorea para medir el rendimiento (parte del [[apm|APM]]).
    -   Contienen [[span|spans]] que detallan las operaciones individuales dentro de la transacción.
    -   Ejemplo: Una solicitud HTTP a un endpoint de API, una carga de página en el frontend.

3.  **Mensajes (Messages)**:
    -   Logs o mensajes informativos que se envían a Sentry.
    -   Menos comunes que los errores o transacciones, pero útiles para registrar información específica.

## Datos Contenidos en un Evento

Cada evento en Sentry incluye una gran cantidad de información contextual para facilitar la depuración:

-   **Stack Trace**: La secuencia de llamadas a funciones que llevaron al error.
-   **Tipo y Mensaje de Error**: Descripción del problema.
-   **Contexto de la Aplicación**: Versión del código ([[release]]), [[environment|entorno]] de despliegue, nombre del host.
-   **Contexto del Usuario**: ID de usuario, dirección IP, información de sesión (si está disponible y configurado).
-   **Contexto del Dispositivo**: Tipo de navegador, sistema operativo, dispositivo.
-   **Contexto de la Solicitud**: URL, método HTTP, encabezados, cuerpo de la solicitud.
-   **Breadcrumbs**: Una línea de tiempo de las acciones que el usuario realizó antes de que ocurriera el evento.
-   **Tags**: Pares clave-valor para filtrar y agrupar eventos.

## Importancia en el Proyecto

Los eventos de Sentry son la fuente principal de información para:

-   **Depuración**: Proporcionan todos los detalles necesarios para reproducir y solucionar errores.
-   **Monitoreo**: Permiten rastrear la frecuencia y el impacto de los errores y problemas de rendimiento.
-   **Alertas**: Disparan alertas cuando se detectan nuevos errores o aumentos en la tasa de errores.
-   **Análisis de Tendencias**: Ayudan a identificar patrones y problemas recurrentes en la aplicación.

## Relación con Otros Conceptos

- [[sentry]] - La plataforma que gestiona y analiza los eventos.
- [[apm]] - Las transacciones son un tipo de evento APM.
- [[release]] - Los eventos se asocian a un release específico.
- [[environment]] - Los eventos ocurren en un entorno específico.
- [[session]] - Los eventos pueden estar asociados a una sesión de usuario.
- [[logs-y-monitoreo]] - Los eventos son una forma de log estructurado.
- [[manejo-de-errores]] - El proceso de capturar y reportar eventos de error.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*