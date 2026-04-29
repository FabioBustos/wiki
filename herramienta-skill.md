---
title: Herramienta Skill
date: 2026-04-27
tags: [skill, herramienta, agentes, opencode, extensibilidad]
---

# Herramienta Skill

## Definición

La **Herramienta Skill** es un mecanismo fundamental dentro del framework de [[opencode|agentes de OpenCode]] que permite a un agente cargar y utilizar una [[skills|skill]] especializada. Al invocar esta herramienta, el agente inyecta en su [[contexto|contexto]] actual las instrucciones, workflows y recursos definidos por la skill, extendiendo así sus capacidades para realizar tareas específicas de manera más efectiva.

## Cómo Funciona

1.  **Identificación de Necesidad**: Un agente de IA determina que necesita un conocimiento o una capacidad especializada para completar una tarea.
2.  **Invocación de la Herramienta Skill**: El agente utiliza la herramienta `skill` y le proporciona el nombre de la [[skills|skill]] que desea cargar (y opcionalmente, parámetros adicionales).
    ```bash
    @skill nombre-de-la-skill [parámetros]
    ```
3.  **Inyección de Contexto**: El sistema de OpenCode inyecta el contenido de la [[skills|skill]] (instrucciones, ejemplos, scripts, etc.) en el [[contexto|contexto]] del agente.
4.  **Ejecución de Tarea**: El agente utiliza el nuevo conocimiento y las directrices de la [[skills|skill]] para proceder con la tarea.

## Importancia en el Proyecto

La Herramienta Skill es crucial para la [[extensibilidad-de-plataforma|extensibilidad]] y flexibilidad de nuestros [[agentes-especializados|agentes de IA]]:

-   **Especialización Dinámica**: Permite a los agentes adquirir especializaciones temporales según la tarea, sin necesidad de tener todo el conocimiento cargado permanentemente.
-   **Modularidad**: Las [[skills|skills]] se desarrollan y mantienen de forma independiente, facilitando la gestión de capacidades.
-   **Reutilización**: Una [[skills|skill]] puede ser utilizada por diferentes [[agentes-especializados|agentes]] cuando sea necesario.
-   **Eficiencia**: Solo se carga el conocimiento especializado cuando es requerido, optimizando el uso de recursos.

## Relación con Otros Conceptos

- [[skills]] - Las entidades que son cargadas por esta herramienta.
- [[opencode]] - El framework que proporciona esta herramienta.
- [[contexto]] - Donde se inyecta el conocimiento de la skill.
- [[agentes-especializados]] - Los agentes que utilizan esta herramienta.
- [[herramientas-del-sistema]] - La Herramienta Skill es una de las herramientas disponibles para los agentes.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*