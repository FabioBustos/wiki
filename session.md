---
title: Sesión (Sentry)
date: 2026-04-27
tags: [sentry, sesión, monitoreo, rendimiento, ux]
---

# Sesión (Sentry)

## Definición

En el contexto de [[sentry|Sentry]], una **Sesión** representa la actividad de un usuario con tu aplicación durante un período de tiempo continuo. Sentry utiliza las sesiones para calcular métricas de salud de la aplicación, como el porcentaje de usuarios sin errores (crash-free users) y el porcentaje de sesiones sin errores (crash-free sessions).

## Importancia en el Proyecto

El monitoreo de sesiones es crucial para nuestro sistema de ticketera porque nos permite:

-   **Medir la Experiencia Real del Usuario**: Entender cuántos usuarios o sesiones están experimentando errores.
-   **Evaluar la Estabilidad de la Aplicación**: Obtener una visión general de la salud de la aplicación desde la perspectiva del usuario.
-   **Identificar Impacto de Errores**: Correlacionar los errores con el impacto real en la experiencia del usuario.
-   **Priorizar Correcciones**: Priorizar los errores que afectan a un mayor número de sesiones o usuarios.

## Cómo Funciona

1.  **Inicio de Sesión**: El SDK de [[sentry|Sentry]] en el frontend [[nextjs]] (o backend para aplicaciones sin UI) inicia una sesión cuando un usuario comienza a interactuar con la aplicación.
2.  **Monitoreo de Actividad**: La sesión se mantiene activa mientras el usuario interactúa.
3.  **Registro de Errores**: Si ocurre un error durante la sesión, Sentry lo asocia a esa sesión.
4.  **Fin de Sesión**: La sesión finaliza después de un período de inactividad o cuando el usuario cierra la aplicación.
5.  **Métricas de Salud**: Sentry agrega los datos de las sesiones para calcular métricas como:
    -   **Crash-free sessions**: Porcentaje de sesiones que no tuvieron errores.
    -   **Crash-free users**: Porcentaje de usuarios que no experimentaron errores durante sus sesiones.

## Configuración en el Proyecto

El SDK de [[sentry|Sentry]] se configura para habilitar el monitoreo de sesiones.

```typescript
// lib/sentry.init.ts (Frontend Next.js)
import * as Sentry from '@sentry/nextjs';

Sentry.init({
  // ... otras configuraciones
  tracesSampleRate: 0.1, // Tasa de muestreo para traces
  replaysSessionSampleRate: 0.1, // Tasa de muestreo para sesiones de Replay
  replaysOnErrorSampleRate: 1.0, // Tasa de muestreo para sesiones de Replay en caso de error
  // ...
});
```

## Relación con Otros Conceptos

- [[sentry]] - Plataforma que utiliza el concepto de sesión.
- [[nextjs]] - Frontend donde se monitorean las sesiones de usuario.
- [[experiencia-de-usuario]] - Las métricas de sesión impactan directamente en la UX.
- [[monitoreo-de-rendimiento]] - Las sesiones son parte del monitoreo de rendimiento.
- [[release]] / [[environment]] - Las métricas de sesión se pueden filtrar por release y entorno.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*