---
title: Obsidian Bases (Skill)
date: 2026-04-27
tags: [skill, obsidian, bases, datos, gestión-conocimiento, productividad]
alias: [Obsidian Databases]
---

# Obsidian Bases (Skill)

## Definición

**Obsidian Bases** es una [[skills|skill]] que permite a los agentes crear y editar archivos `.base` dentro de un [[obsidian-vault|vault de Obsidian]]. Estos archivos `.base` funcionan como bases de datos ligeras o vistas estructuradas de las notas de Obsidian, permitiendo organizar la información en formatos de tabla, tarjetas, calendarios, etc., con funcionalidades de filtros, fórmulas y resúmenes.

## Características Clave

-   **Vistas Estructuradas**: Permite visualizar colecciones de notas como tablas, tarjetas, calendarios o líneas de tiempo.
-   **Filtros**: Filtrar notas basándose en sus propiedades (frontmatter) o contenido.
-   **Fórmulas**: Crear columnas calculadas utilizando fórmulas para extraer o transformar información de las notas.
-   **Resúmenes**: Generar resúmenes de datos (ej. contar notas, sumar valores).
-   **Integración con Notas**: Las entradas en una base son enlaces a notas existentes en el vault.
-   **Automatización**: Permite a los agentes gestionar colecciones de notas de forma programática.

## Uso Potencial en el Proyecto

Un agente con la skill Obsidian Bases podría ser utilizado en nuestro proyecto para:

-   **Gestión de Tareas**: Crear una base de datos de tareas del proyecto, filtrando por estado, asignado o fecha límite.
-   **Seguimiento de Requisitos**: Organizar los requisitos del proyecto en una tabla, con propiedades para estado, prioridad y módulos afectados.
-   **Inventario de Componentes**: Crear una base de datos de componentes de UI, con enlaces a sus stories en [[storybook|Storybook]] y a su documentación.
-   **Gestión de Recursos**: Organizar enlaces a recursos externos, artículos, tutoriales, etc.
-   **Análisis de Documentación**: Filtrar y resumir información de la wiki basada en tags o propiedades.

## Integración con Agentes

Esta skill sería utilizada por agentes como `@doc-writer` o `@product-owner` para organizar y gestionar la información estructurada dentro del vault de Obsidian.

```bash
@skill obsidian-bases
```

Una vez invocada, la skill proporciona las funcionalidades para que el agente pueda manipular archivos `.base`.

## Relación con Otros Conceptos

- [[skills]] - La skill Obsidian Bases es un ejemplo de skill especializada.
- [[obsidian]] - La aplicación con la que esta skill interactúa.
- [[obsidian-vault]] - El vault donde se crean y gestionan las bases.
- [[documentacion-de-proyecto]] - Las bases pueden organizar la documentación.
- [[gestion-del-conocimiento]] - Mejora la gestión del conocimiento estructurado.
- [[agentes-especializados]] - Agentes que utilizarían esta skill.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*