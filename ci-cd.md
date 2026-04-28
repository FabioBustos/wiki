---
title: CI/CD
date: 2026-04-27
tags: [ci-cd, integracion-continua, despliegue-continuo, devops, automatizacion]
alias: [Integración Continua, Despliegue Continuo]
---

# CI/CD

## Definición

**CI/CD** (Integración Continua/Despliegue Continuo o Entrega Continua) es un conjunto de prácticas de desarrollo de software que automatizan las etapas de integración, prueba y entrega de código. Su objetivo es acelerar el ciclo de vida del desarrollo, mejorar la calidad del software y reducir los riesgos asociados con los despliegues.

> [!info] Conceptos Clave
> -   **Integración Continua (CI)**: Los desarrolladores integran sus cambios de código en un repositorio compartido varias veces al día. Cada integración es verificada automáticamente por un build (compilación) y pruebas automatizadas.
> -   **Entrega Continua (CD - Continuous Delivery)**: Una extensión de la CI donde los cambios de código se construyen, prueban y preparan automáticamente para un despliegue en producción. El despliegue final a producción es manual.
> -   **Despliegue Continuo (CD - Continuous Deployment)**: Una extensión de la Entrega Continua donde los cambios de código que pasan todas las etapas de prueba se despliegan automáticamente en producción sin intervención humana.
> -   **Pipeline de CI/CD**: Una serie de pasos automatizados (build, test, deploy) que se ejecutan cada vez que se realiza un cambio en el código.

## Importancia en el Proyecto

La implementación de CI/CD es crucial para nuestro sistema de ticketera, ya que nos permite:

-   **Acelerar la Entrega**: Desplegar nuevas funcionalidades y correcciones de errores de forma rápida y frecuente.
-   **Mejorar la Calidad**: Detectar y corregir errores en etapas tempranas del desarrollo.
-   **Reducir Riesgos**: Minimizar los riesgos asociados con los despliegues al automatizar y estandarizar el proceso.
-   **Consistencia**: Asegurar que el proceso de construcción y despliegue sea consistente en todos los entornos.
-   **Colaboración**: Fomentar la integración frecuente de código entre los miembros del equipo.

## Flujo de un Pipeline de CI/CD Típico

```mermaid
graph TD
    A[Desarrollador hace commit] --> B(Repositorio Git)
    B --> C{Webhook / Evento}
    C --> D[Servidor CI/CD]
    D --> E[Etapa 1: Build]
    E --> F[Etapa 2: Pruebas Unitarias/Integración]
    F --> G{Pruebas Exitosas?}
    G -->|Sí| H[Etapa 3: Build de Imagen Docker]
    H --> I[Etapa 4: Despliegue a Staging]
    I --> J[Etapa 5: Pruebas E2E / QA]
    J --> K{Aprobación Manual (CD)}
    K -->|Sí| L[Etapa 6: Despliegue a Producción]
    K -->|No| M[Notificación de Fallo]
    G -->|No| M
    L --> N[Monitoreo Post-Despliegue]
```

## Herramientas y Servicios Utilizados

-   **Repositorio de Código**: GitHub, GitLab, Bitbucket.
-   **Plataformas CI/CD**: GitHub Actions, GitLab CI, Jenkins, CircleCI, Travis CI.
-   **Contenerización**: [[Docker]] para empaquetar aplicaciones.
-   **Plataformas de Despliegue**: [[Railway]], [[Seenode]] (que a menudo tienen CI/CD integrado o se integran con plataformas externas).
-   **Monitoreo**: [[Sentry]] para monitorear errores post-despliegue.
-   **Testing**: Jest (unitarias), Cypress/Playwright (E2E).
-   **Buildpacks**: Utilizados por [[Railway]] y [[Seenode]] para simplificar la construcción de imágenes.

## Integración en el Proyecto

Nuestro pipeline de CI/CD se configura para:

1.  **Backend ([[NestJS]])**:
    -   Al hacer push a la rama `main`, se ejecuta el pipeline.
    -   Se construyen las imágenes [[Docker]].
    -   Se ejecutan pruebas unitarias y de integración.
    -   Se despliega automáticamente a staging.
    -   Tras aprobación manual, se despliega a producción.
2.  **Frontend ([[Next.js]])**:
    -   Similar al backend, con pasos adicionales para la construcción de assets estáticos y pruebas de interfaz de usuario.

## Beneficios

### [!success] Entrega Rápida y Confiable
-   **Despliegues Frecuentes**: Permite entregar valor a los usuarios de forma continua.
-   **Reducción de Errores**: La automatización reduce la posibilidad de errores humanos.
-   **Rollbacks Sencillos**: Facilita la reversión a versiones anteriores en caso de problemas.

### [!success] Mejora de la Calidad
-   **Detección Temprana de Bugs**: Las pruebas automatizadas identifican problemas antes de que lleguen a producción.
-   **Consistencia del Código**: Asegura que el código cumpla con los estándares de [[Calidad-de-Código]].

### [!success] Colaboración y Productividad
-   **Feedback Rápido**: Los desarrolladores reciben feedback instantáneo sobre sus cambios.
-   **Menos Conflictos**: La integración frecuente reduce los conflictos de código.

## Relación con Otros Conceptos

- [[Docker]] - Contenerización de aplicaciones para despliegue.
- [[Buildpacks]] - Abstracción de la construcción de imágenes.
- [[Railway]] / [[Seenode]] - Plataformas de despliegue.
- [[Sentry]] - Monitoreo post-despliegue.
- [[NestJS]] / [[Next.js]] - Aplicaciones que se construyen y despliegan.
- [[Calidad-de-Código]] - Asegurada a través de pruebas automatizadas.
- [[Flujos-de-trabajo]] - El pipeline de CI/CD define el flujo de trabajo de entrega.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*