---
title: Pruebas de Integración
date: 2026-04-27
tags: [pruebas, testing, integracion, calidad-codigo, desarrollo, metodologia]
alias: [Integration Tests]
---

# Pruebas de Integración

## Definición

Las **Pruebas de Integración** son un tipo de prueba de software que verifica la interacción entre diferentes módulos, componentes o servicios de una aplicación. Su objetivo es asegurar que las unidades de código, que han sido probadas individualmente (con [[pruebas-unitarias|pruebas unitarias]]), funcionen correctamente cuando se combinan, y que las interfaces entre ellas sean correctas.

## Características Clave

-   **Interacción**: Se enfocan en la comunicación y el flujo de datos entre componentes.
-   **Alcance Medio**: Prueban un grupo de unidades o un subsistema, no la aplicación completa.
-   **Dependencias Reales (o Mockeadas Parcialmente)**: A menudo interactúan con dependencias reales (ej. una base de datos real o un servicio externo) o con mocks más sofisticados que simulan el comportamiento de esas dependencias.
-   **Automatización**: Son automatizadas, aunque suelen ser más lentas que las [[pruebas-unitarias|pruebas unitarias]].
-   **Detección de Problemas de Interfaz**: Revelan errores en la comunicación, el formato de datos o los contratos entre componentes.

## Importancia y Beneficios en el Proyecto

Las pruebas de integración son cruciales para nuestro sistema de ticketera porque:

-   **Validación de Flujos**: Aseguran que los flujos de negocio que involucran múltiples componentes (ej. autenticación de usuario, creación de evento, compra de ticket) funcionen correctamente.
-   **Confianza en el Sistema**: Proporcionan confianza en que los diferentes módulos de nuestro backend [[nestjs]] y la comunicación con el frontend [[nextjs]] funcionan como un todo.
-   **Detección de Errores de Contrato**: Identifican problemas cuando un componente espera un formato de datos diferente al que otro componente proporciona.
-   **Reducción de Bugs**: Capturan errores que las [[pruebas-unitarias|pruebas unitarias]] no pueden detectar debido a su aislamiento.

## Cuándo Usar Pruebas de Integración

-   Para probar la interacción entre un controlador y un servicio en el backend.
-   Para verificar la comunicación entre un servicio y la base de datos.
-   Para probar la integración de un componente de UI con su lógica de fetching de datos.
-   Para validar la comunicación con APIs externas (usando mocks para las APIs externas).

## Herramientas y Frameworks

-   **Jest**: Puede utilizarse para pruebas de integración, especialmente con mocks de módulos.
-   **Supertest**: Para probar APIs HTTP en Node.js/NestJS.
-   **TypeORM / Mongoose**: Los ORMs/ODMs pueden ser utilizados en pruebas de integración para interactuar con bases de datos reales o en memoria.

## Mejores Prácticas

### [!tip] Alcance Definido
-   Definir claramente el alcance de cada prueba de integración: qué componentes se están integrando y qué dependencias se están utilizando (reales o mockeadas).

### [!tip] Entorno de Pruebas
-   Utilizar un entorno de base de datos limpio y aislado para cada ejecución de pruebas de integración para evitar efectos secundarios.
-   Considerar bases de datos en memoria o contenedores [[docker]] efímeros para las pruebas.

### [!tip] Mocks Estratégicos
-   Mockear solo las dependencias externas que son lentas, costosas o no fiables (ej. servicios de pago externos, APIs de terceros).
-   No mockear las dependencias internas que son el objetivo de la integración.

## Relación con Otros Conceptos

- [[pruebas-unitarias]] - Complementan las pruebas unitarias.
- [[pruebas-end-to-end]] (I will create this file later if it doesn't exist) - Son de menor alcance que las pruebas E2E.
- [[calidad-de-codigo]] - Contribuyen a la calidad del código.
- [[ci-cd]] - Se ejecutan en el pipeline de CI/CD.
- [[nestjs]] / [[nextjs]] - Frameworks donde se implementan.
- [[docker]] - Para entornos de pruebas aislados.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*