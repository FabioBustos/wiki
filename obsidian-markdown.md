---
title: Obsidian Flavored Markdown
date: 2026-04-27
tags: [obsidian, markdown, documentación, sintaxis, wiki]
alias: [Obsidian Markdown, OFM]
---

# Obsidian Flavored Markdown (OFM)

## Definición

**Obsidian Flavored Markdown (OFM)** es una extensión del estándar Markdown que incorpora características adicionales específicas de la aplicación [[obsidian|Obsidian]]. Estas características mejoran la capacidad de interconexión, organización y visualización de la información dentro de un vault de Obsidian, convirtiéndolo en una potente herramienta para la gestión del conocimiento.

## Características Clave de OFM

1.  **Wikilinks (Enlaces Internos)**:
    -   **Sintaxis**: `[[Nombre de la Nota]]` o `[[ruta/a/la/nota|Texto a mostrar]]`.
    -   **Función**: Permite enlazar fácilmente entre notas dentro del mismo vault. Obsidian crea automáticamente enlaces bidireccionales.
    -   **Uso en el Proyecto**: Fundamental para conectar todos los documentos de nuestra wiki.

2.  **Embeds (Incrustaciones)**:
    -   **Sintaxis**: `![[Nombre de la Nota]]` o `![[ruta/a/imagen.png]]`.
    -   **Función**: Permite incrustar el contenido de otra nota, una imagen, un PDF o un archivo de audio/video directamente en la nota actual.
    -   **Uso en el Proyecto**: Para incrustar diagramas, imágenes o secciones de otras notas relevantes.

3.  **Callouts (Bloques de Cita Mejorados)**:
    -   **Sintaxis**:
        ```markdown
        > [!NOTE] Título del Callout
        > Contenido del callout.
        ```
    -   **Tipos**: `note`, `info`, `tip`, `success`, `warning`, `danger`, `bug`, `example`, `quote`.
    -   **Función**: Resaltar información importante, advertencias, consejos o ejemplos de forma visualmente distintiva.
    -   **Uso en el Proyecto**: Para destacar definiciones, mejores prácticas, advertencias y resúmenes en nuestros documentos de la wiki.

4.  **Frontmatter (Propiedades YAML)**:
    -   **Sintaxis**: Bloque YAML al inicio del archivo, delimitado por `---`.
        ```yaml
        ---
        title: Título de la Nota
        date: 2023-10-27
        tags: [tag1, tag2]
        alias: [Alias 1, Alias 2]
        ---
        ```
    -   **Función**: Añadir metadatos estructurados a la nota, facilitando la búsqueda, filtrado y organización.
    -   **Uso en el Proyecto**: Todos nuestros documentos de la wiki utilizan frontmatter para `title`, `date`, `tags` y `alias`.

5.  **Tags (Etiquetas)**:
    -   **Sintaxis**: `#tag` o `#tag/subtag`.
    -   **Función**: Clasificar y agrupar notas por temas.
    -   **Uso en el Proyecto**: Para categorizar los documentos de la wiki por tecnología, concepto o área.

6.  **Diagramas de Mermaid**:
    -   **Sintaxis**: Bloque de código con `mermaid` como lenguaje.
        ```mermaid
        graph TD
            A[Inicio] --> B(Proceso)
        ```
    -   **Función**: Crear diagramas de flujo, secuencias, Gantt, etc., directamente en la nota.
    -   **Uso en el Proyecto**: Para visualizar arquitecturas, flujos de trabajo y procesos en nuestros documentos.

## Relación con Otros Conceptos

- [[obsidian]] - La aplicación que interpreta y utiliza OFM.
- [[documentacion-de-proyecto]] - Nuestra wiki se construye con OFM.
- [[gestion-del-conocimiento]] - OFM facilita la interconexión del conocimiento.
- [[obsidian-cli]] - Permite interactuar con notas OFM de forma programática.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*