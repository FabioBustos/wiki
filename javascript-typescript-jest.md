---
title: JavaScript/TypeScript Jest Best Practices
date: 2026-04-27
tags: [javascript, typescript, jest, testing, calidad-codigo, desarrollo]
alias: [Jest Best Practices, JS/TS Testing]
---

# JavaScript/TypeScript Jest Best Practices

## Definición

Este documento describe las mejores prácticas para escribir pruebas unitarias y de integración en proyectos JavaScript y TypeScript utilizando el framework de pruebas **Jest**. El objetivo es asegurar la calidad del código, facilitar el mantenimiento y acelerar el ciclo de desarrollo.

## Conceptos Clave de Jest

-   **`describe`**: Agrupa pruebas relacionadas.
-   **`test` / `it`**: Define una prueba individual.
-   **`expect`**: Afirmaciones para verificar el comportamiento del código.
-   **Matchers**: Funciones que se usan con `expect` para probar valores (ej. `toBe`, `toEqual`, `toHaveBeenCalled`).
-   **Mocks**: Sustitutos de objetos o funciones reales para aislar el código bajo prueba.
-   **Spies**: Observadores de funciones que permiten verificar si una función fue llamada y con qué argumentos.
-   **Hooks**: Funciones que se ejecutan antes o después de las pruebas (ej. `beforeEach`, `afterAll`).

## Mejores Prácticas

### [!tip] Estructura de Pruebas
-   **Organización**: Colocar los archivos de prueba (`.test.ts` o `.spec.ts`) junto al código que prueban o en una carpeta `__tests__`.
-   **`describe` claro**: Utilizar `describe` para agrupar lógicamente las pruebas, reflejando la estructura del código o la funcionalidad.
-   **`test` descriptivo**: Cada `test` debe describir claramente qué funcionalidad está probando.

### [!tip] Afirmaciones (Assertions)
-   **`expect` específico**: Usar los matchers más específicos posibles para evitar pruebas frágiles.
-   **Evitar `toBeCalled` sin `toHaveBeenCalledWith`**: Siempre que sea posible, verificar los argumentos con los que se llamó a un mock.

### [!tip] Mocks y Spies
-   **Mocks de Módulos**: Utilizar `jest.mock()` para simular módulos externos (ej. servicios de API, bases de datos).
-   **Mocks de Funciones**: Usar `jest.fn()` para crear funciones mock y controlar su comportamiento.
-   **Spies**: Emplear `jest.spyOn()` para observar llamadas a funciones existentes sin cambiar su implementación.
-   **Limpieza de Mocks**: Asegurarse de limpiar los mocks después de cada prueba (`jest.clearAllMocks()`, `jest.restoreAllMocks()`).

### [!tip] Cobertura de Código
-   **Objetivo**: Apuntar a una alta cobertura de código, pero priorizar la calidad de las pruebas sobre el porcentaje.
-   **Configuración**: Configurar Jest para generar informes de cobertura.

### [!tip] Pruebas Asíncronas
-   **`async/await`**: Utilizar `async/await` para probar código asíncrono.
-   **`waitFor` / `waitForElement`**: Para pruebas de UI, usar utilidades de `testing-library` para esperar que los elementos aparezcan o cambien.

### [!tip] Integración con TypeScript
-   **Tipado de Mocks**: Tipar los mocks para asegurar la seguridad de tipos en las pruebas.
-   **Configuración `tsconfig.json`**: Asegurarse de que `tsconfig.json` esté configurado para Jest.

## Relación con Otros Conceptos

- [[typescript]] / [[javascript]] - Lenguajes de programación.
- [[calidad-de-codigo]] - Las pruebas son fundamentales para la calidad del código.
- [[ci-cd]] - Las pruebas Jest se ejecutan en el pipeline de CI/CD.
- [[nestjs]] / [[nextjs]] - Frameworks donde se escriben las pruebas.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*