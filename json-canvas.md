---
title: JSON Canvas (Skill)
date: 2026-04-27
tags: [skill, obsidian, canvas, diagramas, visualizacion, gestión-conocimiento]
alias: [Obsidian Canvas, Canvas Files]
---

# JSON Canvas (Skill)

## Definición

**JSON Canvas** es una [[skills|skill]] que permite a los agentes crear y editar archivos `.canvas` dentro de un [[obsidian-vault|vault de Obsidian]]. Estos archivos `.canvas` representan un lienzo infinito donde se pueden organizar visualmente notas, imágenes, PDFs, videos y otros elementos como "tarjetas" interconectadas por "flechas". Es una herramienta poderosa para el pensamiento visual, la planificación y la organización de ideas.

## Características Clave

-   **Lienzo Infinito**: Un espacio de trabajo ilimitado para organizar ideas.
-   **Tarjetas (Nodes)**: Elementos visuales que pueden contener texto, imágenes, enlaces a notas de Obsidian, PDFs, videos, etc.
-   **Conexiones (Edges)**: Flechas que conectan las tarjetas, mostrando relaciones y flujos.
-   **Grupos**: Permite agrupar tarjetas relacionadas para organizar visualmente el lienzo.
-   **Pensamiento Visual**: Ideal para brainstorming, mapas mentales, diagramas de flujo, planificación de proyectos y visualización de arquitecturas.
-   **Integración con Obsidian**: Las tarjetas pueden enlazar directamente a notas existentes en el vault.

## Uso Potencial en el Proyecto

Un agente con la skill JSON Canvas podría ser utilizado en nuestro proyecto para:

-   **Planificación de Proyectos**: Crear diagramas de flujo para el [[flujos-de-trabajo|flujo de trabajo]] de desarrollo o para la [[gestion-de-cambios|gestión de cambios]].
-   **Diseño de Arquitectura**: Visualizar la [[arquitectura-de-nube|arquitectura de nube]] o la [[arquitectura-de-microservicios|arquitectura de microservicios]] del sistema.
-   **Mapas Mentales**: Organizar ideas para nuevas funcionalidades o soluciones a problemas complejos.
-   **Onboarding**: Crear un mapa visual del proyecto para nuevos miembros del equipo.
-   **Brainstorming**: Facilitar sesiones de brainstorming visual.

## Integración con Agentes

Esta skill sería utilizada por agentes como `@architect` o `@business-analyst` para tareas de planificación, diseño y visualización.

```bash
@skill json-canvas
```

Una vez invocada, la skill proporciona las funcionalidades para que el agente pueda manipular archivos `.canvas`.

## Relación con Otros Conceptos

- [[skills]] - La skill JSON Canvas es un ejemplo de skill especializada.
- [[obsidian]] - La aplicación que gestiona los archivos Canvas.
- [[obsidian-vault]] - El vault donde se crean y gestionan los Canvas.
- [[flujos-de-trabajo]] - Los Canvas pueden visualizar flujos de trabajo.
- [[arquitectura-de-nube]] / [[arquitectura-de-microservicios]] - Los Canvas pueden representar estas arquitecturas.
- [[agentes-especializados]] - Agentes que utilizarían esta skill.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*