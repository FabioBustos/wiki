---
title: Pruebas Unitarias
date: 2026-04-27
tags: [pruebas, testing, unitarias, calidad-codigo, desarrollo, metodologia]
alias: [Unit Tests, Pruebas de Unidad]
---

# Pruebas Unitarias

## Definición

Las **Pruebas Unitarias** son un tipo de prueba de software que se enfoca en verificar la funcionalidad de las unidades más pequeñas y aisladas de código de una aplicación. Una "unidad" puede ser una función, un método, una clase o un componente individual. El objetivo es asegurar que cada unidad de código se comporte como se espera de forma independiente.

## Características Clave

-   **Aislamiento**: Cada prueba unitaria debe ser independiente de otras pruebas y de componentes externos (bases de datos, APIs, sistema de archivos). Para lograr esto, se utilizan mocks, stubs y spies.
-   **Automatización**: Las pruebas unitarias son completamente automatizadas y se ejecutan rápidamente.
-   **Granularidad**: Se enfocan en unidades de código muy pequeñas.
-   **Repetibilidad**: Deben producir el mismo resultado cada vez que se ejecutan.
-   **Rapidez**: Se ejecutan en milisegundos, lo que permite una retroalimentación casi instantánea al desarrollador.

## Importancia y Beneficios en el Proyecto

Las pruebas unitarias son un pilar fundamental de la [[calidad-de-codigo|calidad de código]] en nuestro sistema de ticketera:

-   **Detección Temprana de Errores**: Identifican bugs en las etapas más tempranas del desarrollo, donde son más fáciles y económicos de corregir.
-   **Confianza en el Código**: Proporcionan una red de seguridad que permite a los desarrolladores refactorizar o añadir nuevas funcionalidades con la confianza de que no romperán el código existente.
-   **Documentación Ejecutable**: Sirven como una forma de documentación del comportamiento esperado de cada unidad de código.
-   **Mejora del Diseño**: Fomentan un diseño de código más modular, desacoplado y fácil de probar.
-   **Facilitan el [[tdd|TDD]]**: Son la base del desarrollo guiado por pruebas.

## Cuándo Usar Pruebas Unitarias

-   Para probar funciones puras.
-   Para verificar la lógica de negocio compleja en servicios.
-   Para probar componentes de UI de forma aislada (sin interacción con el DOM real).
-   Para validar el comportamiento de clases y métodos individuales.

## Herramientas y Frameworks

-   **Jest**: Nuestro framework de pruebas principal para JavaScript/TypeScript en el backend [[nestjs]] y el frontend [[nextjs]].
-   **React Testing Library**: Para probar componentes de React de una manera que se asemeje más a cómo los usuarios interactúan con ellos.

## Mejores Prácticas

### [!tip] Una Prueba, Una Afirmación (Idealmente)
-   Cada prueba debe enfocarse en verificar un único comportamiento.

### [!tip] AAA (Arrange-Act-Assert)
-   **Arrange**: Configurar el estado inicial y las dependencias.
-   **Act**: Ejecutar la unidad de código bajo prueba.
-   **Assert**: Verificar que el resultado sea el esperado.

### [!tip] Mocks y Stubs
-   Utilizar mocks y stubs para aislar la unidad de código y controlar el comportamiento de sus dependencias.
-   Asegurarse de que los mocks se limpien después de cada prueba.

### [!tip] Nombres Descriptivos
-   Los nombres de las pruebas deben ser claros y concisos, describiendo qué se está probando y cuál es el resultado esperado.

## Relación con Otros Conceptos

- [[calidad-de-codigo]] - Contribuyen directamente a la calidad del código.
- [[tdd]] - Metodología que se basa en pruebas unitarias.
- [[ci-cd]] - Las pruebas unitarias se ejecutan en el pipeline de CI/CD.
- [[javascript-typescript-jest]] - Framework de pruebas utilizado.
- [[regresion]] - Ayudan a prevenir y detectar regresiones.
- [[nestjs]] / [[nextjs]] - Frameworks donde se implementan.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*