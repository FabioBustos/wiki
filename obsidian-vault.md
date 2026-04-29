---
title: Obsidian Vault
date: 2026-04-27
tags: [obsidian, vault, conocimiento, gestión, wiki, organización]
alias: [Vault de Obsidian]
---

# Obsidian Vault

## Definición

Un **Obsidian Vault** (o bóveda de Obsidian) es una carpeta local en tu sistema de archivos que contiene todas tus notas en formato Markdown, así como cualquier otro archivo relacionado (imágenes, PDFs, etc.). Es el espacio de trabajo central en [[obsidian|Obsidian]], donde se organiza y se interconecta todo tu conocimiento.

## Características Clave

-   **Local y Portable**: Los vaults se almacenan localmente en tu ordenador, lo que te da control total sobre tus datos. Son fácilmente portables y se pueden sincronizar con servicios en la nube (ej. Google Drive, Dropbox) o con Git.
-   **Markdown**: Todas las notas se escriben en [[obsidian-markdown|Markdown]], un formato de texto plano que asegura la longevidad y la compatibilidad con otras herramientas.
-   **Interconexión**: La principal fortaleza de un vault es la capacidad de enlazar notas entre sí utilizando [[obsidian-markdown|wikilinks]], creando una red de conocimiento.
-   **Plugins**: Los vaults pueden ser extendidos con una gran variedad de plugins que añaden funcionalidades como gestión de tareas, diagramas, integración con otras herramientas, etc.
-   **Vista de Grafo**: Una representación visual de todas las notas y sus conexiones dentro del vault, que ayuda a explorar la estructura del conocimiento.

## Estructura de Nuestro Vault

Nuestro vault de Obsidian para la wiki del proyecto se encuentra en el directorio `doc/wiki/` dentro del repositorio principal.

```
ventasEntrasdasV2/
├── doc/
│   └── wiki/             # Este es nuestro Obsidian Vault
│       ├── indice.md
│       ├── apm.md
│       ├── ... (otras notas .md)
│       └── assets/       # Carpeta para imágenes y otros archivos incrustados
├── .obsidian/            # Carpeta de configuración de Obsidian (oculta)
│   ├── workspace.json
│   ├── app.json
│   └── ... (configuraciones de plugins, temas)
└── ... (otros directorios del proyecto)
```

## Importancia en el Proyecto

El Obsidian Vault es el corazón de nuestra [[documentacion-de-proyecto|documentación del proyecto]] y [[gestion-del-conocimiento|gestión del conocimiento]].

-   **Fuente de Verdad Centralizada**: Sirve como un repositorio único para toda la información relevante del proyecto.
-   **Facilita el Onboarding**: Nuevos miembros del equipo pueden explorar el vault para entender rápidamente la arquitectura, los procesos y las decisiones clave.
-   **Colaboración**: Aunque Obsidian es una aplicación de escritorio, al almacenar el vault en un repositorio Git, facilitamos la colaboración y el versionamiento de la documentación.
-   **Búsqueda y Descubrimiento**: La capacidad de búsqueda y la vista de grafo de Obsidian permiten descubrir relaciones entre conceptos y encontrar información de manera eficiente.

## Mejores Prácticas

### [!tip] Nomenclatura Consistente
-   Utilizar una [[buenas-practicas-de-nomenclatura-de-archivos|nomenclatura de archivos]] consistente (ej. `kebab-case`) para facilitar los wikilinks.

### [!tip] Uso de Frontmatter
-   Incluir `title`, `date`, `tags` y `alias` en el frontmatter de cada nota para mejorar la organización y búsqueda.

### [!tip] Enlaces Bidireccionales
-   Fomentar el uso de wikilinks para conectar conceptos y crear una red de conocimiento rica.

### [!tip] Sincronización con Git
-   Mantener el vault sincronizado con Git para el control de versiones y la colaboración del equipo.

## Relación con Otros Conceptos

- [[obsidian]] - La aplicación que gestiona el vault.
- [[obsidian-markdown]] - El formato de las notas dentro del vault.
- [[documentacion-de-proyecto]] - El vault contiene la documentación del proyecto.
- [[gestion-del-conocimiento]] - El vault es la herramienta principal para la gestión del conocimiento.
- [[git]] - Utilizado para versionar y sincronizar el vault.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*