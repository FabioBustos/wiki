---
title: Contexto (Agentes de IA)
date: 2026-04-27
tags: [ia, agentes, contexto, conocimiento, memoria]
---

# Contexto (Agentes de IA)

## Definición

En el ámbito de los agentes de Inteligencia Artificial, el **Contexto** se refiere al conjunto de información relevante que un agente posee o puede acceder en un momento dado para comprender una situación, tomar decisiones y generar respuestas. Es la "memoria" operativa del agente, que le permite mantener la coherencia y la relevancia en sus interacciones.

## Tipos de Contexto

1.  **Contexto de Conversación**:
    -   **Descripción**: El historial de interacciones previas con el usuario o con otros agentes. Permite al agente recordar lo que se ha dicho antes y mantener el hilo de la conversación.
    -   **Importancia**: Esencial para diálogos coherentes y para evitar repeticiones o malentendidos.

2.  **Contexto de Tarea**:
    -   **Descripción**: Información específica sobre la tarea actual que el agente está realizando (ej. el objetivo, los pasos ya completados, los resultados intermedios).
    -   **Importancia**: Guía al agente en la ejecución de la tarea y le permite retomar el trabajo si se interrumpe.

3.  **Contexto de Herramientas/Skills**:
    -   **Descripción**: La información sobre las [[herramientas-del-sistema|herramientas]] y [[skills|skills]] disponibles para el agente, incluyendo sus capacidades, parámetros y cómo utilizarlas.
    -   **Importancia**: Permite al agente seleccionar y utilizar las herramientas adecuadas para resolver un problema.

4.  **Contexto del Entorno**:
    -   **Descripción**: Información sobre el entorno de ejecución del agente (ej. sistema de archivos, variables de entorno, estado de la aplicación).
    -   **Importancia**: Permite al agente interactuar con el mundo exterior y adaptar su comportamiento a las condiciones actuales.

## Gestión del Contexto

La gestión efectiva del contexto es un desafío clave en el diseño de agentes de IA:

-   **Ventana de Contexto (Context Window)**: Los modelos de lenguaje grandes (LLMs) tienen una limitación en la cantidad de información que pueden procesar en una sola interacción. La gestión del contexto implica seleccionar y resumir la información más relevante para que quepa en esta ventana.
-   **Memoria a Largo Plazo**: Para tareas complejas o conversaciones prolongadas, los agentes necesitan mecanismos para almacenar y recuperar información más allá de la ventana de contexto inmediata.
-   **[[modelo-de-contexto-mcp|Modelo de Contexto Protocol (MCP)]]**: Proporciona un marco estructurado para que los agentes accedan y gestionen el contexto de herramientas y recursos externos.

## Importancia en el Proyecto

En nuestro sistema de [[opencode|agentes de OpenCode]], la gestión del contexto es fundamental para:

-   **Coherencia de los Agentes**: Asegurar que los agentes mantengan un comportamiento coherente a lo largo de sus interacciones.
-   **Eficiencia en la Resolución de Tareas**: Permitir que los agentes accedan a la información necesaria para completar tareas complejas.
-   **Interacción con el Usuario**: Facilitar que los agentes entiendan las preguntas del usuario y proporcionen respuestas relevantes.

## Relación con Otros Conceptos

- [[skills]] - Las skills inyectan contexto especializado en el agente.
- [[herramientas-del-sistema]] - Las herramientas proporcionan acceso a información del entorno.
- [[modelo-de-contexto-mcp]] - Protocolo para gestionar el contexto de herramientas.
- [[agentes-especializados]] - Agentes que operan dentro de un contexto específico.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*