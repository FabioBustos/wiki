---
title: Pruebas End-to-End (E2E)
date: 2026-04-27
tags: [pruebas, testing, e2e, calidad-software, desarrollo, metodologia]
alias: [End-to-End Tests]
---

# Pruebas End-to-End (E2E)

## Definición

Las **Pruebas End-to-End (E2E)**, o pruebas de extremo a extremo, son un tipo de prueba de software que simula el flujo completo de un usuario a través de una aplicación, desde la interfaz de usuario hasta la base de datos y los servicios externos. Su objetivo es verificar que todo el sistema funcione correctamente como un todo integrado, cubriendo todos los componentes y subsistemas involucrados en un escenario de usuario.

## Características Clave

-   **Simulación de Usuario Real**: Interactúan con la aplicación de la misma manera que lo haría un usuario real (clics, entradas de texto, navegación).
-   **Cobertura Amplia**: Prueban la integración de todos los componentes (frontend, backend, base de datos, APIs externas).
-   **Entorno Cercano a Producción**: Se ejecutan en un entorno que se asemeja lo más posible al entorno de producción.
-   **Lentas**: Son las pruebas más lentas de ejecutar debido a que involucran toda la pila tecnológica.
-   **Detección de Problemas de Flujo**: Revelan errores en la integración entre sistemas, problemas de UI/UX y fallos en el flujo de negocio.

## Importancia y Beneficios en el Proyecto

Las pruebas E2E son vitales para nuestro sistema de ticketera porque:

-   **Confianza en el Flujo de Negocio**: Aseguran que los escenarios críticos de usuario (ej. registro, compra de tickets, validación de acceso) funcionen sin problemas.
-   **Validación de la Experiencia Completa**: Verifican la [[experiencia-de-usuario|experiencia de usuario]] desde el inicio hasta el final.
-   **Detección de Errores de Integración**: Capturan problemas que las [[pruebas-unitarias|pruebas unitarias]] y [[pruebas-de-integracion|pruebas de integración]] podrían pasar por alto.
-   **Prevención de [[regresion|Regresiones]]**: Proporcionan una red de seguridad contra regresiones en el sistema completo.
-   **Reducción de Riesgos**: Minimizan el riesgo de desplegar funcionalidades rotas en producción.

## Cuándo Usar Pruebas E2E

-   Para escenarios de usuario críticos y de alto valor.
-   Para verificar flujos de negocio complejos que involucran múltiples servicios.
-   Para asegurar la compatibilidad entre el frontend y el backend.
-   Como una capa final de validación antes del despliegue a producción.

## Herramientas y Frameworks

-   **Cypress**: Un framework popular para pruebas E2E de aplicaciones web, conocido por su facilidad de uso y depuración.
-   **Playwright**: Otro framework potente para pruebas E2E, desarrollado por Microsoft, que soporta múltiples navegadores y lenguajes.
-   **Selenium**: Un framework más antiguo y ampliamente utilizado para la automatización de navegadores.

## Mejores Prácticas

### [!tip] Enfocarse en Flujos Críticos
-   No intentar cubrir cada detalle con pruebas E2E; priorizar los escenarios de usuario más importantes.

### [!tip] Datos de Prueba Aislados
-   Asegurarse de que cada prueba E2E utilice datos de prueba limpios y aislados para evitar efectos secundarios entre pruebas.
-   Considerar la creación y limpieza de datos de prueba antes y después de cada suite de pruebas.

### [!tip] Entorno Consistente
-   Ejecutar pruebas E2E en un entorno que sea lo más parecido posible a producción (ej. un entorno de staging).
-   Utilizar [[docker]] para asegurar la consistencia del entorno de pruebas.

### [!tip] Velocidad y Fiabilidad
-   Optimizar las pruebas para que sean lo más rápidas y fiables posible.
-   Minimizar las esperas (`cy.wait()`) y utilizar selectores robustos.

## Relación con Otros Conceptos

- [[pruebas-unitarias]] - Complementan las pruebas unitarias.
- [[pruebas-de-integracion]] - Complementan las pruebas de integración.
- [[calidad-de-codigo]] - Contribuyen a la calidad general del software.
- [[ci-cd]] - Se ejecutan en el pipeline de CI/CD, a menudo en un paso de despliegue a staging.
- [[regresion]] - Ayudan a prevenir y detectar regresiones en el sistema completo.
- [[experiencia-de-usuario]] - Validar la experiencia del usuario final.
- [[docker]] - Para entornos de pruebas aislados.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*