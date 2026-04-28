---
title: Métricas
date: 2026-04-27
tags: [metricas, observabilidad, monitoreo, rendimiento, apm]
---

# Métricas

## Definición

Las **Métricas** son valores numéricos que se recopilan a lo largo del tiempo para representar el comportamiento o el rendimiento de un sistema, una aplicación o un proceso. Son una forma cuantificable de medir el estado de un sistema y son fundamentales para el monitoreo y la [[Observabilidad|observabilidad]].

## Tipos de Métricas

1.  **Métricas de Rendimiento**: Miden la eficiencia y la velocidad del sistema.
    -   **Latencia**: Tiempo que tarda una operación en completarse (ej. tiempo de respuesta de una API).
    -   **Throughput**: Número de operaciones por unidad de tiempo (ej. solicitudes por segundo).
    -   **Utilización**: Porcentaje de un recurso que está siendo usado (ej. uso de CPU, memoria).
    -   **Errores**: Tasa de errores o fallos en las operaciones.

2.  **Métricas de Negocio**: Miden el impacto del sistema en los objetivos de negocio.
    -   Número de ventas de tickets.
    -   Usuarios activos.
    -   Tasa de conversión.

3.  **Métricas de Infraestructura**: Miden el rendimiento de los componentes subyacentes del hardware o la plataforma.
    -   Uso de CPU, memoria, disco, red de los servidores o contenedores.

## Importancia en el Proyecto

Las métricas son esenciales para nuestro sistema de ticketera porque nos permiten:

-   **Monitorear la Salud del Sistema**: Obtener una visión en tiempo real del estado operativo de la aplicación.
-   **Detectar Anomalías**: Identificar desviaciones del comportamiento normal que podrían indicar problemas.
-   **Optimizar el Rendimiento**: Analizar tendencias para encontrar cuellos de botella y áreas de mejora.
-   **Tomar Decisiones Informadas**: Basar las decisiones de escalabilidad, optimización o desarrollo en datos concretos.
-   **Configurar Alertas**: Recibir notificaciones cuando las métricas superan umbrales predefinidos.

## Recopilación y Visualización

-   **Recopilación**: Las métricas se recopilan a través de la instrumentación del código de la aplicación, los servicios de infraestructura (ej. [[Railway]], [[Seenode]]) y herramientas de monitoreo como [[Sentry]] (para métricas de rendimiento y errores).
-   **Visualización**: Se utilizan dashboards (ej. en Sentry, Grafana) para visualizar las métricas a lo largo del tiempo, permitiendo identificar tendencias y correlaciones.

## Relación con Otros Conceptos

- [[Observabilidad]] - Las métricas son uno de los tres pilares de la observabilidad.
- [[APM]] - Application Performance Monitoring, que se basa en la recopilación y análisis de métricas.
- [[Sentry]] - Herramienta que utilizamos para recopilar métricas de rendimiento y errores.
- [[Costo-de-infraestructura]] - Las métricas de utilización de recursos son clave para optimizar costos.
- [[Mejoras-de-capacidad]] - Las métricas guían las decisiones sobre cómo mejorar la capacidad del sistema.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*