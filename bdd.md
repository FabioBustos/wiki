---
title: BDD (Behavior-Driven Development)
date: 2026-04-27
tags: [bdd, desarrollo, testing, metodologia, agil, negocio]
alias: [Behavior-Driven Development, Desarrollo Guiado por Comportamiento]
---

# BDD (Behavior-Driven Development)

## Definición

**BDD** (Behavior-Driven Development, o Desarrollo Guiado por Comportamiento) es una metodología de desarrollo de software ágil que extiende el [[tdd|Test-Driven Development (TDD)]] al enfocar el proceso de desarrollo en el comportamiento esperado del sistema desde la perspectiva del usuario final. Utiliza un lenguaje ubicuo y natural para describir los requisitos en forma de escenarios ejecutables, facilitando la colaboración entre roles técnicos y no técnicos.

## Lenguaje Gherkin (Given-When-Then)

BDD a menudo utiliza un formato de lenguaje estructurado y legible por humanos llamado **Gherkin** para describir los escenarios de comportamiento. Este formato sigue la estructura "Dado-Cuando-Entonces" (Given-When-Then):

-   **Dado (Given)**: Describe el contexto inicial o el estado del sistema antes de que ocurra la acción.
-   **Cuando (When)**: Describe la acción o el evento que desencadena el comportamiento.
-   **Entonces (Then)**: Describe el resultado esperado o el cambio en el estado del sistema después de la acción.

### Ejemplo de Escenario Gherkin

```gherkin
Característica: Compra de Tickets para Eventos

  Como asistente a un evento
  Quiero poder comprar tickets
  Para asegurar mi lugar en el evento

  Escenario: Compra exitosa de un ticket
    Dado que estoy en la página de detalles del evento "Concierto de Rock"
    Y el evento tiene tickets disponibles
    Cuando selecciono 1 ticket y procedo al pago
    Y completo el pago con éxito
    Entonces debería ver una confirmación de mi compra
    Y debería recibir un [[entradas-e-ticket|e-ticket]] en mi correo electrónico
```

## Importancia y Beneficios en el Proyecto

La implementación de BDD en nuestro sistema de ticketera ofrece varios beneficios:

-   **Colaboración Mejorada**: Fomenta la comunicación y el entendimiento compartido entre product owners, QA y desarrolladores.
-   **Claridad en los Requisitos**: Los escenarios Gherkin son requisitos claros y ejecutables, reduciendo ambigüedades.
-   **Enfoque en el Valor de Negocio**: Asegura que el desarrollo se centre en entregar el comportamiento que realmente importa al usuario final.
-   **Documentación Viva**: Los escenarios Gherkin sirven como documentación actualizada del comportamiento del sistema.
-   **Prevención de Errores**: Ayuda a identificar y corregir malentendidos en los requisitos antes de escribir código.

## Flujo de Trabajo con BDD

```mermaid
graph TD
    A[Discusión (3 Amigos)] --> B[Escribir Escenario Gherkin]
    B --> C[Automatizar Escenario (Prueba Fallida)]
    C --> D[Escribir Código de Implementación]
    D --> E[Ejecutar Pruebas]
    E -->|Pasa| F[Refactorizar Código y Escenario]
    E -->|Falla| D
    F --> G[Nuevo Comportamiento]
```

## Integración con Otros Conceptos

-   **[[tdd|TDD]]**: BDD se construye sobre los principios de TDD, pero a un nivel de abstracción más alto (comportamiento vs. unidad).
-   **[[calidad-de-codigo|Calidad de Código]]**: Mejora la calidad al asegurar que el código cumpla con los requisitos de negocio.
-   **[[ci-cd|CI/CD]]**: Los escenarios BDD automatizados se ejecutan en el pipeline de CI/CD como pruebas de aceptación.
-   **[[retroalimentacion-de-usuarios|Retroalimentación de Usuarios]]**: Los escenarios BDD pueden ser derivados de la retroalimentación de usuarios.
-   **[[procesos-de-validacion|Procesos de Validación]]**: Los escenarios pueden describir el comportamiento esperado de la validación de tickets.

## Herramientas Comunes para BDD

-   **Cucumber**: Framework popular para ejecutar escenarios Gherkin en varios lenguajes.
-   **SpecFlow**: Versión de Cucumber para .NET.
-   **Behave**: Framework BDD para Python.

## Glosario de Términos

-   **Característica (Feature)**: Una funcionalidad de alto nivel del sistema.
-   **Escenario (Scenario)**: Un ejemplo concreto del comportamiento de una característica.
-   **Gherkin**: Lenguaje de dominio específico para describir escenarios.
-   **Lenguaje Ubicuo**: Lenguaje compartido y entendido por todos los miembros del equipo.

## Relación con Otros Conceptos del Sistema

- [[tdd]] - Metodología base.
- [[calidad-de-codigo]] - Mejora la calidad del software.
- [[ci-cd]] - Integración en pipelines de entrega.
- [[entradas-e-ticket]] - Comportamiento de compra y recepción de tickets.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*