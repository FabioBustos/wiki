---
title: Atomic Design
date: 2026-04-27
tags: [diseño, ui, ux, componentes, metodologia, frontend]
alias: [Diseño Atómico]
---

# Atomic Design

## Definición

**Atomic Design** es una metodología para construir sistemas de diseño de interfaz de usuario (UI) de forma jerárquica y modular. Desarrollada por Brad Frost, descompone las interfaces en sus elementos más fundamentales ("átomos") y los combina progresivamente para construir componentes más complejos ("moléculas", "organismos") hasta llegar a las "plantillas" y "páginas" finales.

## Principios Clave

La metodología se basa en cinco etapas distintas, que van de lo abstracto a lo concreto:

1.  **Átomos (Atoms)**:
    -   Los bloques de construcción más básicos de la UI.
    -   Ejemplos: Etiquetas HTML (botones, inputs, etiquetas de texto), paletas de colores, tipografías.
    -   En nuestro proyecto: Clases de [[tailwind|Tailwind CSS]], elementos HTML básicos.

2.  **Moléculas (Molecules)**:
    -   Grupos de átomos unidos que funcionan como una unidad.
    -   Ejemplos: Un campo de búsqueda (input + botón), un formulario de login (varios inputs + botón).
    -   En nuestro proyecto: Componentes de React como `SearchInput`, `LoginForm`.

3.  **Organismos (Organisms)**:
    -   Grupos de moléculas y/o átomos que forman secciones de interfaz más complejas y distintas.
    -   Ejemplos: Una cabecera de página (logo + navegación + campo de búsqueda), una tarjeta de evento.
    -   En nuestro proyecto: Componentes de React como `EventCard`, `Header`.

4.  **Plantillas (Templates)**:
    -   Disposiciones de grupos de organismos que definen la estructura de una página, pero sin contenido real. Se enfocan en la estructura del contenido.
    -   Ejemplos: Un layout de página de detalles de evento (cabecera + sección de contenido + pie de página).
    -   En nuestro proyecto: Layouts de [[nextjs|Next.js]] o componentes de layout.

5.  **Páginas (Pages)**:
    -   Instancias específicas de las plantillas con contenido real. Son la representación final de la UI que ve el usuario.
    -   Ejemplos: La página de inicio con eventos reales, la página de detalles de un evento específico.
    -   En nuestro proyecto: Las páginas de [[nextjs|Next.js]] con datos reales.

## Importancia en el Proyecto

La aplicación de Atomic Design en nuestro frontend [[nextjs]] es fundamental para:

-   **Consistencia del Diseño**: Asegura que todos los componentes sigan las guías de diseño y la identidad visual del proyecto.
-   **Reutilización de Componentes**: Fomenta la creación de componentes modulares y reutilizables, acelerando el desarrollo.
-   **Mantenibilidad**: Facilita la gestión y actualización de la UI, ya que los cambios se propagan de forma controlada.
-   **Colaboración**: Proporciona un lenguaje común para diseñadores y desarrolladores.
-   **Escalabilidad**: Permite construir interfaces complejas a partir de bloques de construcción simples.

## Integración con Herramientas

-   **[[storybook|Storybook]]**: Es una herramienta ideal para implementar y documentar un sistema de diseño basado en Atomic Design, mostrando cada átomo, molécula y organismo de forma aislada.
-   **[[tailwind|Tailwind CSS]]**: Las clases de utilidad de Tailwind pueden verse como los "átomos" de estilizado, que se combinan para formar componentes.
-   **[[react|React]] / [[nextjs|Next.js]]**: La naturaleza basada en componentes de React se alinea perfectamente con Atomic Design.

## Relación con Otros Conceptos

- [[ui-ux-design]] - Metodología de diseño para construir sistemas de UI.
- [[storybook]] - Herramienta para implementar Atomic Design.
- [[tailwind]] - Framework CSS que se integra bien con Atomic Design.
- [[nextjs]] / [[react]] - Tecnologías frontend.
- [[modularidad]] - Principio de diseño subyacente.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*