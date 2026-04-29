---
title: Span (Sentry)
date: 2026-04-27
tags: [sentry, span, apm, rendimiento, observabilidad, tracing]
---

# Span (Sentry)

## Definición

En el contexto de [[sentry|Sentry]] y el [[tracing|tracing distribuido]], un **Span** representa una operación individual o una unidad de trabajo dentro de una [[transaccion|transacción]]. Cada span tiene un nombre, un tiempo de inicio, una duración y puede contener metadatos adicionales (tags, logs). Los spans se anidan para formar un [[tracing|trace]], mostrando la secuencia y la jerarquía de las operaciones.

## Componentes de un Span

-   **Nombre**: Un nombre descriptivo para la operación (ej. "db.query", "http.client", "render.component").
-   **Operación (`op`)**: Un identificador de la operación que se está realizando (ej. `db`, `http`, `ui`).
-   **Tiempo de Inicio y Fin**: Marca de tiempo de cuándo comenzó y terminó la operación.
-   **Duración**: El tiempo total que tardó la operación.
-   **Tags**: Pares clave-valor para añadir contexto al span (ej. `db.table: users`, `http.status_code: 200`).
-   **Logs**: Mensajes de log asociados a la operación.
-   **Padre-Hijo**: Los spans pueden tener relaciones padre-hijo, formando una estructura de árbol que representa el [[tracing|trace]].

## Importancia en el Proyecto

Los spans son fundamentales para el [[monitoreo-de-rendimiento|monitoreo de rendimiento]] detallado de nuestro sistema de ticketera porque nos permiten:

-   **Desglose Detallado**: Ver exactamente dónde se gasta el tiempo dentro de una [[transaccion|transacción]] (ej. cuánto tiempo toma una consulta a la base de datos, una llamada a un servicio externo, o el renderizado de un componente).
-   **Identificación de Cuellos de Botella**: Pinpointar operaciones lentas que están afectando el rendimiento general.
-   **Análisis de Latencia**: Entender la latencia de cada componente en un sistema distribuido.
-   **Depuración de Rendimiento**: Proporcionar información granular para optimizar el código y las interacciones entre servicios.

## Implementación en el Proyecto

Los SDKs de [[sentry|Sentry]] para [[nextjs]] y [[nestjs]] permiten crear [[span|spans]] dentro de las [[transaccion|transacciones]].

```typescript
// Ejemplo de creación de span en NestJS (dentro de una transacción)
const transaction = Sentry.startTransaction({ name: 'Get Event by ID', op: 'http.server' });

try {
  const dbSpan = transaction.startChild({ op: 'db.query', description: 'Query event from DB' });
  const event = await this.eventsService.getEvent(id, query);
  dbSpan.finish();

  const r2Span = transaction.startChild({ op: 'storage.r2', description: 'Fetch image from R2' });
  // ... lógica para obtener imagen de R2 ...
  r2Span.finish();

  transaction.setStatus('ok');
  return event;
} catch (error) {
  transaction.setStatus('internal_error');
  throw error;
} finally {
  transaction.finish();
}
```

## Relación con Otros Conceptos

- [[sentry]] - Plataforma que gestiona y analiza spans.
- [[apm]] - Los spans son el componente básico del APM.
- [[tracing]] - Los spans se anidan para formar un trace.
- [[transaccion]] - Los spans son operaciones dentro de una transacción.
- [[monitoreo-de-rendimiento]] - Los spans proporcionan el detalle granular para el monitoreo.
- [[observabilidad]] - Contribuyen a la observabilidad del sistema.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*