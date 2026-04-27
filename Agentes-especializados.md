---
title: Agentes Especializados
date: 2026-04-27
tags: [agentes, ia, opencode, arquitectura]
---

# Agentes Especializados

Este documento describe el concepto de agentes especializados dentro de la plataforma OpenCode.

## Definición

Los **Agentes Especializados** son componentes de inteligencia artificial diseñados para realizar tareas específicas dentro de un dominio particular. A diferencia de un agente generalista, un agente especializado posee conocimientos, herramientas y flujos de trabajo optimizados para su área de experticia, lo que le permite operar con mayor eficiencia y precisión.

## Características

-   **Dominio Específico**: Cada agente se enfoca en un área particular (ej. desarrollo backend, frontend, documentación, QA).
-   **Conocimiento Profundo**: Incorpora mejores prácticas, patrones de diseño y convenciones específicas de su dominio.
-   **Herramientas Integradas**: Puede acceder y utilizar herramientas relevantes para su especialidad (ej. compiladores, linters, frameworks, bases de datos).
-   **Flujos de Trabajo Optimizados**: Sigue secuencias de pasos predefinidas para resolver problemas comunes en su dominio.
-   **Colaboración**: Pueden interactuar entre sí o con agentes humanos para resolver tareas más complejas.

## Agentes en Nuestro Proyecto

En nuestro proyecto, utilizamos los siguientes agentes especializados a través de la plataforma [[OpenCode]]:

| Agente | Descripción | Uso Principal |
|---|---|---|
| `@nest-developer` | Desarrollador NestJS | Implementación de lógica de negocio, APIs, integración con bases de datos. |
| `@next-developer` | Desarrollador Next.js/React | Creación de interfaces de usuario, componentes, integración con APIs. |
| `@architect` | Arquitecto e Investigador | Diseño de sistemas, análisis de patrones, resolución de problemas complejos. |
| `@doc-writer` | Especialista en Documentación | Creación y actualización de la wiki, manuales técnicos y de usuario. |
| `@code-reviewer` | Revisor de Código | Análisis de código para identificar mejoras de calidad, seguridad y rendimiento. |
| `@systems-analyst` | Analista de Sistemas | Análisis técnico de requisitos, diseño de arquitecturas, especificación de integración. |
| `@security-officer` | Oficial de Seguridad | Análisis de vulnerabilidades, recomendaciones de protección, revisión de políticas de seguridad. |
| `@qa` | Control de Calidad | Diseño y ejecución de pruebas, identificación y reporte de defectos. |
| `@product-owner` | Product Owner | Priorización de funcionalidades, definición de roadmap, gestión del backlog. |
| `@business-analyst` | Analista de Negocio | Análisis de requisitos de negocio, modelado de procesos, documentación funcional. |

## Relación con Otros Conceptos

- [[OpenCode]]
- [[Skills]]
- [[Modelo de Contexto (MCP)]]
- [[comunicacion-equipo]]

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*