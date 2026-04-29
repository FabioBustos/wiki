---
title: Regresión (Software)
date: 2026-04-27
tags: [regresion, testing, calidad, software, errores, ci-cd]
---

# Regresión (Software)

## Definición

En el contexto del desarrollo de software, una **Regresión** ocurre cuando una nueva funcionalidad, una corrección de errores o un cambio en el código introduce un defecto o un comportamiento no deseado en una funcionalidad existente que previamente funcionaba correctamente. Esencialmente, es un paso atrás en la calidad o funcionalidad del software.

## Importancia en el Proyecto

La prevención y detección temprana de regresiones son críticas para nuestro sistema de ticketera porque:

-   **Impacto en el Usuario**: Una regresión puede afectar directamente la experiencia del usuario, impidiendo la compra de entradas o la validación de tickets.
-   **Costos**: Detectar una regresión en producción es mucho más costoso que detectarla en etapas tempranas del desarrollo.
-   **Confianza**: Las regresiones frecuentes erosionan la confianza de los usuarios y organizadores en la plataforma.

## Causas Comunes de Regresiones

-   **Cambios en el Código**: Modificaciones en una parte del código que afectan inadvertidamente a otra parte.
-   **Falta de Pruebas**: Ausencia de pruebas automatizadas o manuales que cubran la funcionalidad afectada.
-   **Dependencias Ocultas**: Cambios en librerías o servicios externos que no se prueban adecuadamente.
-   **Falta de Entendimiento**: No comprender completamente el impacto de un cambio en todo el sistema.

## Estrategias para Prevenir y Detectar Regresiones

### 1. Pruebas Automatizadas

-   **Pruebas Unitarias**: Aseguran que los componentes individuales funcionen correctamente.
-   **Pruebas de Integración**: Verifican la interacción entre diferentes módulos o servicios.
-   **Pruebas End-to-End (E2E)**: Simulan el flujo completo del usuario para detectar problemas en la aplicación.
-   **Pruebas de Regresión**: Un conjunto de pruebas diseñadas específicamente para asegurar que los cambios recientes no han introducido nuevos defectos en funcionalidades existentes.

### 2. Integración Continua (CI)

-   **[[ci-cd|Pipelines de CI/CD]]**: Ejecutar automáticamente todas las pruebas cada vez que se realiza un cambio en el código. Esto proporciona retroalimentación rápida sobre si un cambio ha introducido una regresión.

### 3. Revisiones de Código

-   **Code Reviews**: Ayudan a identificar posibles problemas lógicos o efectos secundarios no deseados antes de que el código se fusione.

### 4. Monitoreo

-   **[[sentry|Sentry]]**: Configurar [[sentry|Sentry]] para detectar regresiones de errores, es decir, un aumento significativo en la tasa de errores después de un nuevo despliegue.
-   **[[apm|APM]]**: Monitorear el rendimiento para detectar regresiones de rendimiento.

## Relación con Otros Conceptos

- [[ci-cd]] - El pipeline de CI/CD es clave para la detección de regresiones.
- [[sentry]] - Herramienta para detectar regresiones de errores.
- [[apm]] - Herramienta para detectar regresiones de rendimiento.
- [[calidad-de-codigo]] - La prevención de regresiones es un aspecto fundamental de la calidad del código.
- [[testing]] (I will create this file later if it doesn't exist) - Las pruebas son la principal defensa contra las regresiones.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*