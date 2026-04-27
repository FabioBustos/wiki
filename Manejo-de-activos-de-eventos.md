---
title: Manejo de Activos de Eventos
date: 2026-04-27
tags: [eventos, activos, gestión, r2, backend, frontend]
---

# Manejo de Activos de Eventos

Este documento describe cómo se gestionan los activos (imágenes, videos, etc.) asociados a los eventos en el sistema.

## Definición

Los **Activos de Eventos** son todos los archivos multimedia y documentos relacionados con un evento específico, que necesitan ser almacenados, gestionados y servidos a los usuarios o al personal del evento.

## Tipos de Activos

-   **Imágenes**:
    -   Carteles y banners promocionales.
    -   Fotos de artistas, ponentes o lugares.
    -   Logos de patrocinadores y organizadores.
    -   Imágenes de asientos o planos del venue.
-   **Videos**:
    -   Videos promocionales o teasers.
    -   Grabaciones de eventos anteriores (para archivo o VOD).
-   **Documentos**:
    -   Programas del evento en PDF.
    -   Mapas del recinto.
    -   Información de acceso o instrucciones especiales.
-   **Tickets Digitales**:
    -   Códigos QR o de barras generados.
    -   Plantillas de tickets personalizadas.

## Arquitectura de Almacenamiento

Utilizamos [[Cloudflare R2]] para el almacenamiento de todos los activos de eventos debido a su [[Egress|ausencia de cargos por salida de datos]] y su integración con la red de Cloudflare para una entrega de alto rendimiento.

### Estructura de Almacenamiento (Prefijos)

Los activos se organizan dentro del bucket R2 utilizando prefixes para facilitar la gestión y el control de acceso:

-   `event-images/{eventId}/{timestamp}-{randomString}.{ext}`: Para imágenes promocionales y carteles.
-   `event-videos/{eventId}/{timestamp}-{randomString}.{ext}`: Para videos.
-   `event-documents/{eventId}/{filename}.{ext}`: Para PDFs y otros documentos.
-   `venue-assets/{venueId}/{type}/{filename}.{ext}`: Para planos o imágenes de venues.
-   `tickets/{ticketId}.png`: Para los códigos QR/barras de los tickets generados.

## Flujo de Gestión

1.  **Subida**: Los activos son subidos por organizadores de eventos o personal autorizado, generalmente a través de una interfaz en el backend o directamente al frontend con URLs firmadas.
2.  **Almacenamiento**: Los archivos se guardan en [[Cloudflare R2]] con una clave (incluyendo prefix) y metadata relevante.
3.  **Referencia**: La URL pública o la clave del activo se almacena en la base de datos, asociada al evento correspondiente.
4.  **Entrega**:
    -   El frontend solicita la URL del activo al backend o la obtiene directamente si es pública.
    -   Los activos se sirven eficientemente a través del CDN de Cloudflare.
    -   Para imágenes, se pueden aplicar optimizaciones al vuelo usando [[Cloudflare Images]] o [[Cloudflare Workers]].

## Consideraciones de Seguridad

-   **Acceso Controlado**: Los activos sensibles (ej. datos de pago, información privada) deben ser privados y accesibles solo mediante [[URL Firmada]] o a través de endpoints de backend protegidos.
-   **Validación de Archivos**: Validar tipos de archivo y tamaños para prevenir subidas maliciosas.
-   **[[Políticas de Ciclo de Vida]]**: Configurar reglas para eliminar activos obsoletos o temporales.

## Relación con Otros Conceptos

- [[Cloudflare R2]]
- [[Entradas y E-Tickets]]
- [[Venue (Recinto/Espacio)]]
- [[Optimización de Imágenes]]
- [[URL Firmada]]
- [[Prefix]]
- [[Metadata]]
- [[Seguridad-de-datos]]
- [[Backend (NestJS)]]
- [[Frontend (Next.js)]]

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*