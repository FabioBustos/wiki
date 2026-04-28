---
title: Transporte (MCP)
date: 2026-04-27
tags: [mcp, protocolo, transporte, comunicación]
---

# Transporte (MCP)

Este documento describe los mecanismos de transporte utilizados por el Modelo de Contexto Protocol (MCP).

## Definición

En el [[Modelo de Contexto (MCP)|Modelo de Contexto Protocol (MCP)]], el **Transporte** se refiere al método o protocolo de comunicación subyacente que se utiliza para intercambiar mensajes entre un [[Cliente MCP|Cliente MCP]] y un [[Servidor MCP|Servidor MCP]]. La elección del transporte adecuado depende de la naturaleza de la herramienta o servicio que se está exponiendo.

## Mecanismos de Transporte Comunes

MCP está diseñado para ser agnóstico al transporte, permitiendo su implementación sobre diversos protocolos:

1.  **Stdio (Standard Input/Output)**:
    -   **Descripción**: Comunicación a través de la entrada y salida estándar del sistema. Típicamente usado para herramientas locales que se ejecutan como procesos separados.
    -   **Uso**: Común para ejecutar comandos de shell (`bash`), scripts locales o herramientas de línea de comandos.
    -   **Ejemplo**: Un agente ejecutando `bash` a través de MCP.

2.  **HTTP/SSE (Server-Sent Events)**:
    -   **Descripción**: Comunicación basada en la web, utilizando solicitudes HTTP para la comunicación bidireccional y SSE para actualizaciones unidireccionales del servidor al cliente.
    -   **Uso**: Ideal para interactuar con APIs web, servicios remotos o para notificaciones en tiempo real.
    -   **Ejemplo**: Un agente consultando la [[documentacion-de-proyecto|documentación]] a través de un servicio web MCP.

3.  **WebSocket**:
    -   **Descripción**: Protocolo de comunicación bidireccional y full-duplex sobre una única conexión TCP.
    -   **Uso**: Adecuado para aplicaciones que requieren comunicación en tiempo real y de baja latencia, como herramientas interactivas o colaboración en vivo.
    -   **Ejemplo**: Un servidor MCP que expone una interfaz de edición colaborativa.

## Consideraciones de Selección

La elección del mecanismo de transporte adecuado depende de:

-   **Naturaleza de la Herramienta**: ¿Es una herramienta local o remota? ¿Requiere comunicación en tiempo real?
-   **Latencia**: ¿Qué tan sensible es la aplicación a la latencia de red?
-   **Seguridad**: ¿Qué tan seguro es el canal de comunicación?
-   **Escalabilidad**: ¿Puede el mecanismo de transporte manejar un alto volumen de tráfico?

## Relación con Otros Conceptos

- [[Modelo de Contexto (MCP)]]
- [[Cliente MCP]]
- [[Servidor MCP]]
- [[Herramientas del Sistema]]
- [[Skills]]

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*