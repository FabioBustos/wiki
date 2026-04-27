---
title: Buenas Prácticas de Nomenclatura de Archivos
date: 2026-04-27
tags: [nomenclatura, archivos, organización, convenciones, código, documentación]
---

# Buenas Prácticas de Nomenclatura de Archivos

Este documento establece las convenciones y mejores prácticas para nombrar archivos en el proyecto, asegurando consistencia, claridad y facilidad de gestión.

## Principios Fundamentales

1.  **Claridad y Descriptividad**: Los nombres deben indicar claramente el contenido o propósito del archivo.
2.  **Consistencia**: Seguir un patrón uniforme en todo el proyecto.
3.  **Legibilidad**: Usar nombres fáciles de leer y entender.
4.  **Evitar Caracteres Especiales**: Limitarse a caracteres alfanuméricos y guiones/guiones bajos.
5.  **Sensibilidad a Mayúsculas/Minúsculas**: Ser consistente (generalmente minúsculas).

## Convenciones por Tipo de Archivo

### 1. Código Fuente (TypeScript/JavaScript)

-   **Archivos**: `nombreDelComponente.tsx`, `servicioDeUsuario.ts`, `utilidades.ts`
    -   Usar `camelCase` para nombres de archivo.
    -   Los archivos de componentes de UI suelen tener la extensión `.tsx` (o `.jsx`).
    -   Los archivos de lógica de negocio o utilidades usan `.ts` (o `.js`).
-   **Clases/Interfaces**: Si un archivo contiene una única clase o interfaz principal, el nombre del archivo debe coincidir con el nombre de la exportación principal.
-   **Archivos de Prueba**: `nombreDelArchivo.test.ts` (o `.spec.ts`) para pruebas unitarias/integración.
-   **Archivos de Estilo**: `nombreDelComponente.module.css` (CSS Modules) o `nombreDelComponente.scss`.

### 2. Documentación (Markdown)

-   **Archivos Wiki**: `nombre-del-tema.md` (usar `kebab-case` para wikilinks y nombres de archivo).
    -   Ejemplos: `indice-de-la-wiki.md`, `cloudflare-r2.md`, `modelo-de-contexto-mcp.md`.
-   **READMEs**: `README.md` (en la raíz de módulos o directorios importantes).
-   **Documentación de API**: `api-especificacion.yaml` o `swagger.json`.

### 3. Configuración

-   `opencode.json`
-   `.env` (variables de entorno)
-   `docker-compose.yml`
-   `Dockerfile`
-   `railway.toml`

### 4. Assets (Imágenes, Fuentes, etc.)

-   **Prefijos Descriptivos**: Usar prefixes para organizar, especialmente en [[Cloudflare R2]].
    -   `event-images/{eventId}/{timestamp}-{randomString}.{ext}`
    -   `logos/{nombreLogo}.svg`
    -   `fonts/{nombreFuente}-{peso}.woff2`
-   **Nombres Claros**: Evitar nombres genéricos como `image1.jpg`. Usar nombres que describan el contenido.
-   **Minúsculas y Guiones**: `mi-imagen-de-evento.jpg`

### 5. Scripts

-   `generate-module.js`
-   `deploy-production.sh`
-   `run-tests.bat`

## Reglas Generales

-   **Minúsculas**: Preferir nombres de archivo en minúsculas.
-   **Guiones vs. Guiones Bajos**: Usar `kebab-case` (guiones) para archivos de documentación y nombres de URL/wikilinks. Usar `camelCase` para archivos de código fuente. Usar guiones bajos (`snake_case`) solo si es requerido por una convención específica (ej. algunas bases de datos o scripts).
-   **Evitar Espacios**: Los espacios en nombres de archivo pueden causar problemas en algunos sistemas y comandos.
-   **Longitud**: Mantener los nombres de archivo razonablemente cortos pero descriptivos.
-   **Extensiones**: Siempre incluir la extensión de archivo correcta.

## Relación con Otros Conceptos

- [[OpenCode]] - Cómo los agentes manejan archivos y nombres.
- [[Cloudflare R2]] / [[Amazon S3]] - Organización de archivos mediante prefixes.
- [[Git]] - Convenciones para nombres de ramas y mensajes de commit.
- [[Obsidian]] - Cómo se enlazan los documentos wiki.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*