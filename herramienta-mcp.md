---
title: Herramienta (MCP)
date: 2026-04-27
tags: [mcp, protocolo, herramienta, acciones]
---

# Herramienta (MCP)

Este documento describe el concepto de "Herramienta" dentro del Modelo de Contexto Protocol (MCP).

## Definición

En el contexto del [[Modelo de Contexto (MCP)|Modelo de Contexto Protocol (MCP)]], una **Herramienta** es un tipo de [[Capacidad (MCP)|Capacidad]] que representa una función ejecutable que un [[Cliente MCP|Cliente MCP]] (agente de IA) puede invocar para realizar una acción específica. A diferencia de los [[Recurso (MCP)|Recursos]] (que son de solo lectura), las herramientas pueden modificar el estado del sistema, interactuar con servicios externos o realizar operaciones complejas.

## Características de una Herramienta

-   **Acciones Ejecutables**: Permite al agente realizar operaciones activas en el entorno.
-   **Parámetros**: Acepta argumentos de entrada que definen cómo debe ejecutarse la acción.
-   **Resultados**: Devuelve un resultado que indica el éxito o fracaso de la operación, y opcionalmente datos generados por la acción.
-   **Efectos Secundarios**: Puede tener efectos en el estado del sistema o en servicios externos.
-   **Seguridad**: La ejecución de herramientas puede estar sujeta a controles de acceso y sandboxing para garantizar la seguridad.

## Ejemplos de Herramientas en el Proyecto

En nuestro sistema, las [[Herramientas del Sistema|Herramientas del Sistema]] son ejemplos de herramientas que los agentes pueden invocar:

-   `write`: Para crear o modificar archivos.
-   `edit`: Para realizar cambios específicos en el contenido de un archivo.
-   `bash`: Para ejecutar comandos de shell.
-   `skill`: Para cargar conocimientos especializados.
-   `task`: Para delegar tareas a otros agentes.

Además, los [[Servidor MCP|Servidores MCP]] como Playwright o Chrome DevTools exponen herramientas para interactuar con navegadores web.

## Flujo de Uso

1.  El [[Cliente MCP]] decide que necesita realizar una acción y selecciona la herramienta adecuada.
2.  El Cliente MCP construye una solicitud de ejecución de herramienta, incluyendo los parámetros necesarios.
3.  El [[Servidor MCP]] recibe la solicitud, valida los parámetros y ejecuta la herramienta.
4.  El Servidor MCP devuelve el resultado de la ejecución (éxito, error, datos de salida) al Cliente MCP.

## Relación con Otros Conceptos

- [[Modelo de Contexto (MCP)]]
- [[Capacidad (MCP)]]
- [[Cliente MCP]]
- [[Servidor MCP]]
- [[Recurso (MCP)]]
- [[Herramientas del Sistema]]

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*