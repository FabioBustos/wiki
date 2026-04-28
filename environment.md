---
title: Environment (Sentry)
date: 2026-04-27
tags: [sentry, environment, entorno, despliegue, monitoreo]
---

# Environment (Sentry)

## Definición

En el contexto de [[sentry|Sentry]], un **Environment** (entorno) es una etiqueta que se utiliza para distinguir entre diferentes etapas de despliegue de una aplicación. Permite a los desarrolladores filtrar y organizar los errores y problemas de rendimiento por el entorno en el que ocurrieron (ej. `development`, `staging`, `production`).

## Importancia en el Proyecto

La configuración de entornos en [[sentry|Sentry]] es fundamental para nuestro sistema de ticketera porque nos permite:

-   **Filtrar Errores**: Ver solo los errores que ocurren en un entorno específico, lo que es crucial para la depuración.
-   **Comparar Rendimiento**: Analizar el rendimiento de la aplicación en diferentes entornos.
-   **Priorizar Problemas**: Identificar si un error está afectando a los usuarios en producción o solo en desarrollo.
-   **Gestión de Alertas**: Configurar alertas específicas para cada entorno (ej. alertas críticas solo para producción).

## Cómo Funciona

1.  **Configuración en la Aplicación**: El SDK de Sentry en el frontend [[nextjs]] y el backend [[nestjs]] se configura con el nombre del entorno actual.
2.  **Reporte de Eventos**: Cada evento (error o transacción de rendimiento) que se envía a Sentry incluye la etiqueta del entorno.
3.  **Filtrado en Sentry**: En el panel de Sentry, se pueden aplicar filtros para ver los eventos de uno o varios entornos.

## Configuración en el Proyecto

### Frontend ([[nextjs]])

```typescript
// lib/sentry.init.ts
Sentry.init({
  // ... otras configuraciones
  environment: process.env.NODE_ENV, // Utiliza la variable de entorno NODE_ENV
});
```

### Backend ([[nestjs]])

```typescript
// src/sentry/sentry.module.ts
Sentry.init({
  // ... otras configuraciones
  environment: process.env.NODE_ENV, // Utiliza la variable de entorno NODE_ENV
});
```

El valor de `NODE_ENV` se inyecta como una [[variables-de-entorno|variable de entorno]] durante el proceso de despliegue.

## Mejores Prácticas

### [!tip] Nombres de Entorno Consistentes
-   Utilizar nombres de entorno estándar y consistentes (ej. `development`, `staging`, `production`).

### [!tip] Configuración Automática
-   Asegurarse de que el entorno se configure automáticamente en el pipeline de [[ci-cd|CI/CD]] o en la plataforma de despliegue.

### [!tip] Alertas Específicas
-   Configurar alertas en Sentry para que se disparen solo para entornos específicos (ej. solo para `production`).

## Relación con Otros Conceptos

- [[sentry]] - Plataforma que utiliza el concepto de entorno.
- [[release]] - Los releases se despliegan en entornos específicos.
- [[variables-de-entorno]] - Utilizadas para configurar el entorno.
- [[nextjs]] / [[nestjs]] - Aplicaciones que reportan su entorno a Sentry.
- [[ci-cd]] - El pipeline de CI/CD gestiona el despliegue en diferentes entornos.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*