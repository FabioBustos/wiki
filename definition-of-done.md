---
title: Definition of Done (DoD)
date: 2026-04-27
tags: [agil, scrum, dod, calidad, desarrollo, metodologia]
alias: [Definición de Terminado, Done-is-Done]
---

# Definition of Done (DoD) o "Definición de Terminado"

## Definición

La **Definition of Done (DoD)**, o "Definición de Terminado", es un acuerdo formal y compartido por todo el equipo de desarrollo sobre el conjunto de criterios de calidad que un incremento de producto (una funcionalidad, una historia de usuario, una tarea) debe cumplir para ser considerado "terminado". Es una lista de verificación que asegura que el trabajo entregado es de alta calidad y está listo para ser potencialmente desplegado.

## Importancia en el Proyecto

La DoD es crucial para nuestro proyecto de sistema de ticketera, especialmente si seguimos metodologías ágiles, porque:

-   **Claridad y Transparencia**: Proporciona un entendimiento común de lo que significa "terminado", eliminando ambigüedades.
-   **Calidad Consistente**: Asegura que cada incremento de producto cumpla con un estándar de calidad mínimo antes de ser entregado.
-   **Reducción de Retrabajo**: Evita que el trabajo se considere terminado prematuramente y luego requiera correcciones significativas.
-   **Confianza del Equipo**: Aumenta la confianza del equipo en su capacidad para entregar software funcional y de alta calidad.
-   **Facilita la Colaboración**: Sirve como un contrato entre el equipo de desarrollo, el Product Owner y los stakeholders.

## Elementos Típicos de una DoD

La DoD puede variar según el proyecto y el equipo, pero típicamente incluye criterios como:

-   **Código**:
    -   El código ha sido escrito y revisado (Code Review).
    -   Cumple con los estándares de [[calidad-de-codigo|calidad de código]] (linters, formateadores).
    -   No hay deuda técnica significativa introducida.
-   **Pruebas**:
    -   Se han escrito y pasado todas las [[pruebas-unitarias|pruebas unitarias]].
    -   Se han escrito y pasado las [[pruebas-de-integracion|pruebas de integración]] relevantes.
    -   Se han escrito y pasado las [[pruebas-end-to-end|pruebas E2E]] relevantes.
    -   La cobertura de código cumple con el umbral definido.
-   **Funcionalidad**:
    -   La funcionalidad cumple con los criterios de aceptación de la historia de usuario.
    -   Ha sido probada por QA.
    -   No hay bugs conocidos.
-   **Documentación**:
    -   La [[documentacion-de-proyecto|documentación]] técnica ha sido actualizada (ej. wiki, comentarios de código).
    -   La documentación de usuario (si aplica) ha sido creada/actualizada.
-   **Despliegue**:
    -   El código ha sido fusionado en la rama principal.
    -   Ha pasado el pipeline de [[ci-cd|CI/CD]].
    -   Ha sido desplegado en un entorno de staging/QA.

## El Patrón "Done-is-Done" (Metodologías Ágiles)

El patrón "Done-is-Done" enfatiza que una tarea o funcionalidad no se considera "terminada" hasta que cumple con **todos** los criterios de la Definition of Done. No hay "casi terminado" o "terminado al 90%". Si no cumple con la DoD, el trabajo se considera incompleto y no se puede pasar a la siguiente etapa (ej. a la revisión del Product Owner o al despliegue).

Este patrón fomenta la disciplina y la responsabilidad, asegurando que el equipo entregue incrementos de producto verdaderamente completos y de alta calidad en cada iteración.

## Cómo Establecer una DoD

1.  **Colaboración del Equipo**: La DoD debe ser creada y acordada por todo el equipo de desarrollo, incluyendo QA y, si es posible, el Product Owner.
2.  **Evolutiva**: La DoD no es estática; debe ser revisada y adaptada periódicamente a medida que el equipo madura y el proyecto evoluciona.
3.  **Visible**: Debe ser visible y accesible para todos los miembros del equipo (ej. en la wiki, en un tablero físico).

## Mejores Prácticas

### [!tip] Ser Específico y Medible
-   Los criterios deben ser claros y verificables, evitando ambigüedades.

### [!tip] Enfocarse en la Calidad
-   La DoD debe reflejar el compromiso del equipo con la entrega de software de alta calidad.

### [!tip] No Comprometer la DoD
-   Evitar la tentación de relajar la DoD para "terminar" una tarea a tiempo. Esto solo pospone los problemas.

## Relación con Otros Conceptos

- [[metodologias-agiles]] (I will create this file later if it doesn't exist) - La DoD es un concepto central en Scrum y otras metodologías ágiles.
- [[calidad-de-codigo]] - La DoD asegura la calidad del código.
- [[pruebas-unitarias]] / [[pruebas-de-integracion]] / [[pruebas-end-to-end]] - Los criterios de prueba son parte de la DoD.
- [[ci-cd]] - El pipeline de CI/CD ayuda a automatizar la verificación de la DoD.
- [[documentacion-de-proyecto]] - La actualización de la documentación es un criterio común de la DoD.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*