---
title: Obsidian CLI (Skill)
date: 2026-04-27
tags: [skill, obsidian, cli, documentación, gestión-conocimiento, automatizacion]
alias: [Obsidian Command Line Interface]
---

# Obsidian CLI (Skill)

## Definición

**Obsidian CLI** es una [[skills|skill]] que permite a los agentes interactuar con vaults de [[obsidian|Obsidian]] utilizando una interfaz de línea de comandos (CLI). Esta skill proporciona comandos para leer, crear, buscar y gestionar notas, tareas, propiedades y otros elementos dentro de un vault de Obsidian. También soporta el desarrollo de plugins y temas para Obsidian.

## Características Clave

-   **Gestión de Notas**: Crear nuevas notas, leer el contenido de notas existentes, actualizar notas.
-   **Búsqueda Avanzada**: Buscar notas por contenido, título, tags o propiedades.
-   **Gestión de Propiedades**: Leer y establecer propiedades (frontmatter) en las notas.
-   **Gestión de Tareas**: Crear, actualizar y marcar tareas en las notas.
-   **Desarrollo de Plugins/Temas**: Comandos para recargar plugins, ejecutar JavaScript, capturar errores, tomar capturas de pantalla e inspeccionar el DOM de Obsidian.

## Uso Potencial en el Proyecto

Un agente con la skill Obsidian CLI podría ser utilizado en nuestro proyecto para:

-   **Automatización de Documentación**: Crear automáticamente borradores de documentos técnicos o de negocio en la wiki de [[obsidian|Obsidian]].
-   **Actualización de Propiedades**: Actualizar propiedades de notas (ej. `date`, `status`) de forma programática.
-   **Búsqueda de Información**: Buscar rápidamente información relevante en la wiki para responder preguntas o asistir en tareas.
-   **Gestión de Tareas**: Crear o actualizar tareas directamente en las notas de Obsidian.
-   **Desarrollo de la Wiki**: Asistir en la creación y mantenimiento de la estructura de la wiki.

## Integración con Agentes

Esta skill sería utilizada por agentes como `@doc-writer` o `@architect` para interactuar con la wiki del proyecto.

```bash
@skill obsidian-cli
```

Una vez invocada, la skill proporciona los comandos CLI para que el agente pueda manipular el vault de Obsidian.

## Relación con Otros Conceptos

- [[skills]] - La skill Obsidian CLI es un ejemplo de skill especializada.
- [[obsidian]] - La aplicación con la que esta skill interactúa.
- [[documentacion-de-proyecto]] - La wiki del proyecto se gestiona con Obsidian.
- [[gestion-del-conocimiento]] - Esta skill automatiza aspectos de la gestión del conocimiento.
- [[agentes-especializados]] - Agentes que utilizarían esta skill.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*