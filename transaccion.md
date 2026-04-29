---
title: Transacción (Sentry)
date: 2026-04-27
tags: [sentry, transaccion, apm, rendimiento, observabilidad, tracing]
---

# Transacción (Sentry)

## Definición

En el contexto de [[sentry|Sentry]] y [[apm|Application Performance Monitoring (APM)]], una **Transacción** representa una unidad de trabajo o una operación completa que se monitorea para medir el rendimiento. Una transacción es el punto de entrada de un [[tracing|trace distribuido]] y encapsula una serie de [[span|spans]] que representan operaciones individuales dentro de esa unidad de trabajo.

## Ejemplos de Transacciones

-   **Carga de Página**: La carga completa de una página web en el frontend.
-   **Solicitud HTTP**: Una solicitud a un endpoint de API en el backend.
-   **Proceso en Segundo Plano**: Una tarea asíncrona o un job que se ejecuta en el servidor.

## Componentes de una Transacción

-   **Nombre**: Un nombre descriptivo para la transacción (ej. "GET /events", "Carga de Página Principal").
-   **Operación (`op`)**: Un identificador de la operación que se está realizando (ej. `http.server`, `http.client`, `ui.load`, `db.query`).
-   **Duración**: El tiempo total que tarda la transacción en completarse.
-   **[[span|Spans]]**: Operaciones individuales anidadas dentro de la transacción, que proporcionan un desglose detallado de dónde se gasta el tiempo.
-   **Contexto**: Información adicional como el [[environment|entorno]], [[release|release]], usuario, tags personalizados.

## Importancia en el Proyecto

Las transacciones de [[sentry|Sentry]] son fundamentales para el [[monitoreo-de-rendimiento|monitoreo de rendimiento]] de nuestro sistema de ticketera porque nos permiten:

-   **Identificar Cuellos de Botella**: Ver dónde se gasta el tiempo en una operación, ya sea en el frontend o en el backend.
-   **Optimizar Flujos Críticos**: Analizar el rendimiento de flujos de usuario clave (ej. proceso de compra de tickets).
-   **Detectar Regresiones de Rendimiento**: Identificar si un nuevo despliegue ha introducido una degradación en el rendimiento.
-   **Obtener Visibilidad End-to-End**: Rastrear una solicitud desde el navegador del usuario hasta el backend y la base de datos.

## Implementación en el Proyecto

Los SDKs de [[sentry|Sentry]] para [[nextjs]] y [[nestjs]] permiten iniciar y finalizar transacciones, así como crear [[span|spans]] dentro de ellas.

```typescript
// Ejemplo de inicio de transacción en NestJS (ver sentry.md para más detalles)
const transaction = Sentry.startTransaction({
  name: 'Get Event by ID',
  op: 'http.server',
});

// ... lógica de negocio ...

transaction.setStatus('ok'); // o 'internal_error'
transaction.finish();
```

## Relación con Otros Conceptos

- [[sentry]] - Plataforma que gestiona y analiza transacciones.
- [[apm]] - Las transacciones son el corazón del APM.
- [[tracing]] - Una transacción es el inicio de un trace distribuido.
- [[span]] - Componentes individuales de una transacción.
- [[monitoreo-de-rendimiento]] - Las transacciones proporcionan datos clave para el monitoreo.
- [[observabilidad]] - Contribuyen a la observabilidad del sistema.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*