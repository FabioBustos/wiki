---
title: Breadcrumb (Sentry)
date: 2026-04-27
tags: [sentry, breadcrumb, errores, monitoreo, depuracion]
---

# Breadcrumb (Sentry)

## Definición

En el contexto de [[sentry|Sentry]], un **Breadcrumb** (migaja de pan) es un registro de eventos que ocurrieron antes de que se produjera un [[evento|error]] o una [[transaccion|transacción]] de rendimiento. Los breadcrumbs proporcionan una línea de tiempo de las acciones del usuario, las solicitudes de red, los cambios de estado de la aplicación y otros eventos significativos, lo que ayuda a reconstruir el contexto que llevó al problema.

## Tipos de Breadcrumbs

[[sentry|Sentry]] captura automáticamente varios tipos de breadcrumbs, y también permite añadir breadcrumbs personalizados:

-   **Navegación**: Cambios de ruta en el frontend.
-   **Clics de UI**: Interacciones del usuario con elementos de la interfaz.
-   **Solicitudes HTTP**: Llamadas de red realizadas por la aplicación.
-   **Logs**: Mensajes de log de la aplicación.
-   **Cambios de Estado**: Actualizaciones en el estado de la aplicación.
-   **Mensajes Personalizados**: Breadcrumbs añadidos manualmente por el desarrollador para eventos específicos.

## Importancia en el Proyecto

Los breadcrumbs son invaluables para la depuración de errores en nuestro sistema de ticketera porque:

-   **Contexto Pre-Error**: Ayudan a entender qué estaba haciendo el usuario o la aplicación justo antes de que ocurriera un [[evento|error]].
-   **Reproducción de Errores**: Facilitan la reproducción de errores al proporcionar una secuencia de pasos.
-   **Mejora de la Experiencia de Usuario**: Permiten identificar patrones de uso que conducen a errores.

## Implementación en el Proyecto

Los SDKs de [[sentry|Sentry]] para [[nextjs]] y [[nestjs]] capturan automáticamente muchos breadcrumbs. También se pueden añadir breadcrumbs personalizados.

```typescript
// Ejemplo de añadir breadcrumb personalizado en Next.js (frontend)
import * as Sentry from '@sentry/nextjs';

function handleTicketPurchase(ticketId: string) {
  Sentry.addBreadcrumb({
    category: 'ticket.purchase',
    message: `User initiated purchase for ticket ${ticketId}`,
    level: 'info',
    data: {
      ticketId: ticketId,
      paymentMethod: 'credit_card',
    },
  });
  // ... lógica de compra
}
```

## Relación con Otros Conceptos

- [[sentry]] - Plataforma que gestiona y analiza breadcrumbs.
- [[evento]] - Los breadcrumbs proporcionan contexto para los eventos de error.
- [[transaccion]] - Los breadcrumbs pueden ser parte del contexto de una transacción.
- [[manejo-de-errores]] - Los breadcrumbs son una herramienta clave para la depuración de errores.
- [[logs-y-monitoreo]] - Los breadcrumbs son un tipo de log contextual.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*