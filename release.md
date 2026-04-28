---
title: Release (Sentry)
date: 2026-04-27
tags: [sentry, release, version, despliegue, monitoreo]
---

# Release (Sentry)

## Definición

En el contexto de [[sentry|Sentry]], un **Release** (lanzamiento o versión) es una versión específica de tu código que se despliega en un entorno. Sentry utiliza los releases para rastrear el ciclo de vida de los errores y problemas de rendimiento, permitiendo correlacionar los errores con versiones de código específicas y entornos de despliegue.

## Importancia en el Proyecto

La configuración de releases en [[sentry|Sentry]] es crucial para nuestro sistema de ticketera porque nos permite:

-   **Identificar Regresiones**: Saber si un error fue introducido en un nuevo despliegue.
-   **Monitorear la Salud de la Versión**: Ver el porcentaje de sesiones sin errores para una versión específica.
-   **Priorizar Errores**: Entender qué errores afectan a qué versiones y en qué entornos.
-   **Facilitar la Depuración**: Correlacionar los errores con el código fuente exacto que se desplegó.

## Cómo Funciona

1.  **Creación de Release**: Antes o durante el proceso de despliegue, se crea un release en Sentry con un nombre único (ej. `frontend@1.0.0`, `backend@2026-04-27-abcde`).
2.  **Asociación de Commits**: Se asocian los commits de Git al release, lo que permite a Sentry mostrar qué cambios de código están incluidos en esa versión.
3.  **Configuración en la Aplicación**: El SDK de Sentry en el frontend [[nextjs]] y el backend [[nestjs]] se configura con el nombre del release actual.
4.  **Despliegue**: Se notifica a Sentry cuando un release se despliega en un [[environment|entorno]] específico (ej. `production`, `staging`).

## Configuración en el Proyecto

### Frontend ([[nextjs]])

```typescript
// lib/sentry.init.ts
Sentry.init({
  // ... otras configuraciones
  release: process.env.NEXT_PUBLIC_SENTRY_RELEASE || 'unknown',
});
```

### Backend ([[nestjs]])

```typescript
// src/sentry/sentry.module.ts
Sentry.init({
  // ... otras configuraciones
  release: process.env.SENTRY_RELEASE || 'unknown',
});
```

El valor de `SENTRY_RELEASE` se inyecta como una [[variables-de-entorno|variable de entorno]] durante el proceso de [[ci-cd|CI/CD]], a menudo utilizando el hash del commit de Git o un número de versión.

## Mejores Prácticas

### [!tip] Nombres de Release Consistentes
-   Utilizar un esquema de nombres consistente y significativo para los releases (ej. `nombre-servicio@version`, `nombre-servicio@git-sha`).

### [!tip] Integración con CI/CD
-   Automatizar la creación y el marcado de releases en Sentry como parte del pipeline de [[ci-cd|CI/CD]].
-   Notificar a Sentry sobre los despliegues a cada [[environment|entorno]].

### [!tip] Asociar Commits
-   Asegurarse de que los commits de Git estén asociados a los releases para una trazabilidad completa.

## Relación con Otros Conceptos

- [[sentry]] - Plataforma que utiliza el concepto de release.
- [[environment]] - Los releases se despliegan en entornos específicos.
- [[ci-cd]] - El pipeline de CI/CD gestiona la creación y despliegue de releases.
- [[nextjs]] / [[nestjs]] - Aplicaciones que reportan su release a Sentry.
- [[variables-de-entorno]] - Utilizadas para configurar el nombre del release.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*