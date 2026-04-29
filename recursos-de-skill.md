---
title: Recursos de Skill
date: 2026-04-27
tags: [skill, recursos, agentes, opencode, documentación]
---

# Recursos de Skill

## Definición

Los **Recursos de Skill** son los materiales y la información que forman parte de una [[skills|skill]] y que se inyectan en el [[contexto|contexto]] de un agente cuando la [[herramienta-skill|skill]] es cargada. Estos recursos proporcionan al agente el conocimiento especializado y las herramientas prácticas necesarias para realizar tareas específicas de manera efectiva.

## Tipos de Recursos de Skill

Los recursos de skill pueden incluir una variedad de elementos:

1.  **Instrucciones y Directrices**: Texto que describe el propósito de la skill, cómo debe ser utilizada, los pasos a seguir, las mejores prácticas y las consideraciones importantes.
2.  **Ejemplos de Uso**: Fragmentos de código, comandos o interacciones que demuestran cómo aplicar la skill.
3.  **Plantillas**: Estructuras predefinidas para la generación de código, documentos o configuraciones.
4.  **Scripts**: Pequeños programas o comandos que el agente puede ejecutar para automatizar tareas.
5.  **Referencias**: Enlaces a documentación externa, APIs o guías relevantes.
6.  **Glosarios**: Definiciones de términos específicos del dominio de la skill.

## Importancia en el Proyecto

Los Recursos de Skill son fundamentales para la eficacia de nuestros [[agentes-especializados|agentes de IA]] en [[opencode|OpenCode]]:

-   **Conocimiento Especializado**: Proporcionan a los agentes el conocimiento profundo necesario para dominios específicos (ej. testing con Jest, diseño UI/UX).
-   **Guía para la Acción**: Dirigen al agente sobre cómo proceder con una tarea, asegurando que siga las mejores prácticas.
-   **Automatización**: Permiten al agente ejecutar scripts o utilizar plantillas para acelerar el trabajo.
-   **Consistencia**: Aseguran que las tareas se realicen de manera uniforme y con alta calidad.

## Ejemplo de Uso

Cuando un agente carga la skill `obsidian-markdown`, sus recursos de skill incluirían:

-   Instrucciones sobre la sintaxis de [[obsidian-markdown|Obsidian Flavored Markdown]].
-   Ejemplos de cómo usar wikilinks, callouts y frontmatter.
-   Plantillas para la creación de nuevos documentos de wiki.
-   Directrices sobre la [[buenas-practicas-de-nomenclatura-de-archivos|nomenclatura de archivos]] en Obsidian.

## Relación con Otros Conceptos

- [[skills]] - La skill es el contenedor de estos recursos.
- [[herramienta-skill]] - La herramienta que carga estos recursos en el contexto del agente.
- [[contexto]] - Donde se inyectan los recursos de skill.
- [[agentes-especializados]] - Los agentes que utilizan estos recursos.
- [[opencode]] - El framework que gestiona las skills y sus recursos.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*