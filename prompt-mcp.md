---
title: Prompt (MCP)
date: 2026-04-27
tags: [mcp, protocolo, prompt, ia, comunicación]
---

# Prompt (MCP)

Este documento describe el concepto de "Prompt" dentro del Modelo de Contexto Protocol (MCP).

## Definición

En el contexto del [[Modelo de Contexto (MCP)|Modelo de Contexto Protocol (MCP)]], un **Prompt** es un tipo de [[Capacidad (MCP)|Capacidad]] que representa una plantilla o fragmento de texto predefinido que un [[Cliente MCP|Cliente MCP]] (agente de IA) puede utilizar para interactuar con un [[Modelo de Contexto (MCP)|Modelo de Lenguaje Grande (LLM)]] o con el usuario. Los prompts están diseñados para guiar la generación de texto o para solicitar información específica de manera estructurada.

## Características de un Prompt

-   **Plantilla de Texto**: Contiene texto predefinido que puede incluir marcadores de posición para variables.
-   **Guía para LLM**: Ayuda al LLM a entender el tipo de respuesta esperada o el formato deseado.
-   **Interacción con Usuario**: Puede ser utilizado para formular preguntas claras al usuario o presentar opciones.
-   **Reutilizable**: Permite la estandarización de las interacciones y la generación de contenido.

## Ejemplos de Prompts

Aunque no se exponen directamente como herramientas en nuestro sistema actual, el concepto de prompt es fundamental para la operación de los agentes. Ejemplos de cómo se usarían los prompts si fueran una capacidad MCP explícita:

-   Un prompt para solicitar al LLM que genere un resumen de un documento.
-   Un prompt para pedir al usuario que elija entre varias opciones.
-   Un prompt para guiar al LLM en la creación de un plan de desarrollo.

## Flujo de Uso

1.  El [[Cliente MCP]] identifica la necesidad de generar texto o interactuar con el LLM/usuario de una manera específica.
2.  El Cliente MCP selecciona el prompt adecuado y rellena los marcadores de posición con la información relevante.
3.  El prompt se envía al LLM o se presenta al usuario.
4.  El LLM genera una respuesta basada en el prompt, o el usuario proporciona la información solicitada.

## Relación con Otros Conceptos

- [[Modelo de Contexto (MCP)]]
- [[Capacidad (MCP)]]
- [[Cliente MCP]]
- [[Servidor MCP]]
- [[Herramienta]]

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*