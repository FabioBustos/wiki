---
title: Obsidian
date: 2026-04-27
tags: [obsidian, documentación, wiki, markdown, conocimiento, productividad]
alias: [Obsidian.md, Obsidian App]
---

# Obsidian

## Definición

**Obsidian** es una potente aplicación de escritorio para la gestión del conocimiento personal y la toma de notas, que funciona sobre archivos Markdown locales. Se destaca por su capacidad para crear una "segunda mente" o un "cerebro digital" mediante la interconexión de notas a través de enlaces bidireccionales, lo que permite descubrir relaciones y patrones entre ideas.

## Conceptos Clave

-   **Vault (Bóveda)**: Una carpeta local en tu sistema de archivos que contiene todas tus notas Markdown y archivos relacionados.
-   **Notas (Notes)**: Archivos Markdown individuales que contienen tu información.
-   **Enlaces Bidireccionales (Bi-directional Links)**: La característica central de Obsidian. Permite enlazar una nota a otra (`[[Nombre de la Nota]]`) y ver automáticamente qué otras notas enlazan a la actual (backlinks).
-   **Graph View (Vista de Grafo)**: Una representación visual de todas tus notas y sus conexiones, que ayuda a explorar la estructura de tu conocimiento.
-   **Markdown**: El formato de texto plano utilizado para escribir notas, lo que garantiza la portabilidad y la longevidad de tus datos.
-   **Frontmatter**: Metadatos en formato YAML al inicio de una nota Markdown, utilizados para añadir propiedades como `title`, `date`, `tags`, `alias`.
-   **Plugins**: Obsidian es altamente extensible a través de una gran variedad de plugins de la comunidad y oficiales.

## Uso en el Sistema de Ticketera

En nuestro proyecto, utilizamos Obsidian para gestionar la wiki interna y la documentación técnica. Esto nos permite:

-   **Documentación Interconectada**: Crear una red de conocimiento donde los conceptos están enlazados entre sí, facilitando la comprensión de la arquitectura y los procesos.
-   **Gestión del Conocimiento**: Centralizar definiciones, decisiones de diseño, mejores prácticas y glosarios.
-   **Onboarding**: Nuevos miembros del equipo pueden navegar por la wiki para entender rápidamente el proyecto.
-   **Búsqueda Eficiente**: La potente búsqueda de Obsidian y la vista de grafo ayudan a encontrar información relevante rápidamente.

## Estructura de la Wiki en Obsidian

Nuestra wiki se encuentra en el directorio `doc/wiki/` y sigue una estructura plana de archivos Markdown, con enlaces internos para conectar los documentos.

```
doc/wiki/
├── indice.md
├── apm.md
├── arquitectura-de-nube.md
├── base-de-datos.md
├── base-de-datos-mongodb.md
├── base-de-datos-postgresql.md
├── buildpacks.md
├── calidad-de-codigo.md
├── ci-cd.md
├── cloudflare-r2.md
├── cloudflare-workers.md
├── comunicacion-equipo.md
├── comparativa-de-servicios-de-almacenamiento.md
├── configuracion-de-cloudflare-images.md
├── cors.md
├── costo-de-infraestructura.md
├── docker.md
├── documentacion-de-proyecto.md
├── dsn.md
├── egress.md
├── endpoint.md
├── entradas-e-ticket.md
├── etag.md
├── experiencia-de-desarrollador.md
├── experiencia-de-usuario.md
├── fiabilidad.md
├── flujos-de-trabajo.md
├── gestion-de-cambios.md
├── gestion-de-credenciales.md
├── gestion-del-conocimiento.md
├── guia-de-integracion-de-s3.md
├── herramienta-mcp.md
├── herramientas-del-sistema.md
├── http.md
├── implementacion-de-cloudflare-stream.md
├── integracion-con-backend.md
├── integracion-de-sistemas-pago.md
├── jwt.md
├── logs-y-monitoreo.md
├── manejo-de-activos-de-eventos.md
├── manejo-de-errores.md
├── mcp.md
├── medidas-de-seguridad.md
├── mejoras-de-capacidad.md
├── mejores-practicas-de-seguridad-en-almacenamiento.md
├── metadata.md
├── metricas.md
├── modelo-de-contexto-mcp.md
├── monitoreo-de-rendimiento.md
├── multipart-upload.md
├── nano-banana.md
├── nestjs.md
├── nextjs.md
├── notebooklm.md
├── objeto.md
├── observabilidad.md
├── ollama.md
├── onboarding-de-equipo.md
├── opencode.md
├── optimizacion-de-imagenes.md
├── politica-de-ciclo-de-vida.md
├── politica-de-cors.md
├── prefix.md
├── producto-mvp.md
├── prompt-mcp.md
├── railway.md
├── recurso-mcp.md
├── redes-privadas.md
├── region.md
├── regresion.md
├── release.md
├── retroalimentacion-de-usuarios.md
├── revision-de-requisitos.md
├── reutilizacion-de-conocimiento.md
├── sandboxing-mcp.md
├── sdk-de-aws.md
├── secret-access-key.md
├── seguridad-de-datos.md
├── seenode.md
├── sentry.md
├── session.md
├── skills.md
├── storybook.md
├── tailwind.md
├── taxonomia-de-eventos.md
├── tracing.md
├── transporte-mcp.md
├── url-firmada.md
├── variables-de-entorno.md
├── venue.md
├── versioning.md
└── ...
```

## Mejores Prácticas para la Wiki en Obsidian

### [!tip] Nomenclatura de Archivos
-   Utilizar `kebab-case` para los nombres de archivo (ej. `nombre-de-la-nota.md`).
-   Mantener los nombres de archivo cortos pero descriptivos.

### [!tip] Uso de Wikilinks
-   Enlazar conceptos relacionados utilizando `[[Nombre de la Nota]]` para crear una red de conocimiento.
-   Asegurarse de que los wikilinks apunten a archivos existentes o crear placeholders para los que no.

### [!tip] Frontmatter
-   Incluir siempre `title`, `date`, `tags` y `alias` en el frontmatter para facilitar la búsqueda y organización.

### [!tip] Callouts
-   Utilizar callouts (`> [!info]`, `> [!tip]`, `> [!warning]`, `> [!success]`) para resaltar información importante.

### [!tip] Diagramas
-   Integrar diagramas de Mermaid para visualizar arquitecturas, flujos de trabajo y relaciones.

## Relación con Otros Conceptos

- [[documentacion-de-proyecto]] - La wiki es una parte fundamental de la documentación del proyecto.
- [[gestion-del-conocimiento]] - Obsidian es la herramienta principal para la gestión del conocimiento.
- [[opencode]] - Los agentes de OpenCode pueden interactuar con la wiki para crear y actualizar documentación.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*