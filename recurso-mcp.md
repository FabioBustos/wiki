---
title: Recurso (MCP)
date: 2026-04-27
tags: [mcp, protocolo, recurso, datos]
---

# Recurso (MCP)

Este documento describe el concepto de "Recurso" dentro del Modelo de Contexto Protocol (MCP).

## Definición

En el contexto del [[Modelo de Contexto (MCP)|Modelo de Contexto Protocol (MCP)]], un **Recurso** es un tipo de [[Capacidad (MCP)|Capacidad]] que representa una fuente de datos o información a la que un [[Cliente MCP|Cliente MCP]] (agente de IA) puede acceder. Los recursos son típicamente de solo lectura, lo que significa que el cliente puede consultar su contenido pero no modificarlo directamente a través de esta capacidad.

## Características de un Recurso

-   **Solo Lectura**: La función principal de un recurso es proporcionar acceso a datos existentes.
-   **Identificable**: Cada recurso tiene un identificador único que el cliente utiliza para solicitar acceso.
-   **Contenido**: Puede ser cualquier tipo de datos: el contenido de un archivo, el resultado de una consulta a una base de datos, la respuesta de una API de solo lectura, etc.
-   **Metadatos**: Puede incluir información adicional sobre el recurso, como su tipo, tamaño, fecha de última modificación, etc.

## Ejemplos de Recursos en el Proyecto

En nuestro sistema, ejemplos de recursos que podrían ser expuestos vía MCP incluyen:

-   **Archivos de Documentación**: El contenido de los archivos `.md` de la wiki.
-   **Esquemas de Base de Datos**: La definición de las colecciones o tablas de la base de datos.
-   **Configuraciones del Proyecto**: El contenido del archivo `opencode.json` o `.env`.
-   **Logs de Aplicación**: Registros históricos de eventos del sistema.

## Flujo de Uso

1.  El [[Cliente MCP]] solicita un recurso específico (ej. "leer el archivo `doc/wiki/opencode.md`").
2.  El [[Servidor MCP]] verifica los permisos y localiza el recurso.
3.  El Servidor MCP lee el contenido del recurso.
4.  El Servidor MCP devuelve el contenido al Cliente MCP.

## Relación con Otros Conceptos

- [[Modelo de Contexto (MCP)]]
- [[Capacidad (MCP)]]
- [[Cliente MCP]]
- [[Servidor MCP]]
- [[Herramientas del Sistema]] (`read` tool es un ejemplo de cómo un agente accede a un recurso de archivo)

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*