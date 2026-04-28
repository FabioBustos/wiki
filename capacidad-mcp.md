---
title: Capacidad (MCP)
date: 2026-04-27
tags: [mcp, protocolo, capacidad, herramientas]
---

# Capacidad (MCP)

Este documento describe el concepto de "Capacidad" dentro del Modelo de Contexto Protocol (MCP).

## Definición

En el contexto del [[Modelo de Contexto (MCP)|Modelo de Contexto Protocol (MCP)]], una **Capacidad** es una funcionalidad específica que un [[Servidor MCP|Servidor MCP]] ofrece a un [[Cliente MCP|Cliente MCP]]. Las capacidades definen qué tipo de interacciones puede tener un agente de IA con el mundo exterior, ya sea a través de la ejecución de herramientas, el acceso a recursos o la utilización de prompts predefinidos.

## Tipos de Capacidades

MCP define varios tipos de capacidades:

1.  **Recursos**: Representan fuentes de datos que el cliente puede leer. Pueden ser archivos, bases de datos, APIs de solo lectura, etc.
    -   Ejemplo: Un recurso que permite leer el contenido de un archivo específico.
2.  **Herramientas**: Son funciones ejecutables que realizan acciones y pueden modificar el estado del sistema o interactuar con servicios externos.
    -   Ejemplo: Una herramienta para escribir en un archivo, ejecutar un comando de shell, o llamar a una API de creación de usuarios.
3.  **Prompts**: Son plantillas predefinidas o fragmentos de texto que el cliente puede utilizar para generar interacciones comunes con el LLM.
    -   Ejemplo: Un prompt para generar un resumen de un documento o para pedir al LLM que elabore un plan.
4.  **Logging**: Permite al servidor MCP enviar registros de actividad o información de depuración al cliente.

## Declaración de Capacidades

Los Servidores MCP declaran sus capacidades de manera estructurada, lo que permite a los Clientes MCP descubrir qué pueden hacer y cómo invocarlas. Esta declaración incluye:

-   El nombre de la capacidad.
-   Una descripción de su propósito.
-   Los parámetros que acepta (tipo, obligatoriedad, descripción).
-   El tipo de retorno esperado.

## Importancia en el Proyecto

La definición clara de capacidades es fundamental para:

-   **Interoperabilidad**: Permite que diferentes agentes y herramientas se comuniquen de manera estandarizada.
-   **Seguridad**: Al limitar las acciones que un agente puede realizar a través de capacidades explícitas.
-   **Extensibilidad**: Facilita la adición de nuevas funcionalidades al sistema simplemente declarando nuevas capacidades.
-   **Claridad**: Proporciona una interfaz bien definida para la interacción entre IA y el entorno.

## Relación con Otros Conceptos

- [[Modelo de Contexto (MCP)]]
- [[Cliente MCP]]
- [[Servidor MCP]]
- [[Herramienta]]
- [[Recurso]]
- [[Prompt]]

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*