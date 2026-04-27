---
title: Herramientas del Sistema
date: 2026-04-27
tags: [herramientas, sistema, agentes, opencode]
---

# Herramientas del Sistema

Este documento describe las herramientas fundamentales disponibles para los agentes dentro del entorno de OpenCode. Estas herramientas permiten a los agentes interactuar con el sistema de archivos, ejecutar comandos, buscar información y comunicarse con el usuario.

## Definición

Las **Herramientas del Sistema** son funciones predefinidas y accesibles para los agentes de IA, que les permiten realizar acciones específicas en el entorno de ejecución. Son la interfaz principal a través de la cual los agentes extienden sus capacidades más allá del procesamiento de lenguaje natural.

## Herramientas Principales

| Herramienta | Descripción | Uso Principal |
|---|---|---|
| `read` | Lee el contenido de un archivo o directorio. | Acceder a código fuente, documentación, configuraciones. |
| `write` | Escribe contenido en un archivo, sobrescribiendo si existe. | Crear o actualizar archivos de código, documentación, configuraciones. |
| `edit` | Realiza reemplazos de texto específicos en un archivo. | Modificar líneas de código, actualizar valores en archivos de configuración. |
| `glob` | Busca archivos y directorios que coinciden con un patrón. | Encontrar archivos relevantes en el codebase. |
| `grep` | Busca patrones de texto dentro del contenido de los archivos. | Localizar definiciones de funciones, variables, o cadenas específicas. |
| `bash` | Ejecuta comandos de shell en el sistema operativo. | Operaciones de Git, instalación de dependencias, ejecución de scripts. |
| `skill` | Carga una skill especializada para extender las capacidades del agente. | Acceder a conocimientos y flujos de trabajo específicos de un dominio. |
| `task` | Lanza un nuevo agente para manejar tareas complejas y multi-paso. | Delegar subtareas a agentes especializados. |
| `question` | Permite al agente hacer preguntas al usuario para clarificación o decisiones. | Interacción con el usuario para obtener información adicional. |

## Cómo se Utilizan

Los agentes invocan estas herramientas mediante llamadas de función estructuradas en su proceso de pensamiento. Por ejemplo, para leer un archivo, un agente podría generar una llamada como:

```python
tool_code = "read(filePath='src/app.ts')"
```

El sistema ejecuta esta llamada y devuelve el resultado al agente, que luego lo utiliza para continuar su razonamiento o acción.

## Importancia en el Proyecto

-   **Extensibilidad**: Permiten a los agentes interactuar con el mundo exterior y realizar acciones concretas.
-   **Control**: El acceso a estas herramientas está mediado y puede ser auditado.
-   **Flexibilidad**: Los agentes pueden combinar diferentes herramientas para lograr objetivos complejos.
-   **Seguridad**: Las herramientas están diseñadas para operar dentro de límites seguros y controlados.

## Relación con Otros Conceptos

- [[Agentes-especializados]]
- [[Skills]]
- [[Modelo de Contexto (MCP)]]
- [[Flujos-de-trabajo]]

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*