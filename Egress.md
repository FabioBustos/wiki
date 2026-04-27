---
title: Egress (Salida de Datos)
date: 2026-04-27
tags: [costos, red, almacenamiento, cloudflare, r2]
---

# Egress (Salida de Datos)

Este documento explica el concepto de "Egress" y su relevancia en el contexto de servicios de almacenamiento y red.

## Definición

**Egress** (o salida de datos) se refiere a la transferencia de datos desde un servidor, centro de datos o servicio de nube hacia una red externa, como Internet. Esencialmente, es la cantidad de datos que "salen" de la infraestructura del proveedor.

## Importancia en Costos de Infraestructura

Muchos proveedores de servicios en la nube (AWS, Google Cloud, Azure) cobran por la salida de datos (egress fees). Estos cargos pueden ser significativos, especialmente para aplicaciones que sirven grandes cantidades de datos a usuarios finales, como:

-   Descargas de archivos
-   Streaming de video
-   Entrega de activos estáticos (imágenes, CSS, JS)
-   Consultas a bases de datos que devuelven grandes volúmenes de información

## Cloudflare R2 y Egress

Una de las ventajas clave de [[Cloudflare R2]] es que **no cobra por la salida de datos**. Esto lo convierte en una opción muy atractiva para aplicaciones que manejan grandes volúmenes de activos, como:

-   Almacenamiento de imágenes y videos de eventos.
-   Entrega de tickets digitales.
-   Servir activos estáticos del frontend.

Al eliminar los costos de egress, R2 puede ofrecer ahorros sustanciales en comparación con otros servicios de almacenamiento de objetos como Amazon S3.

## Relación con Otros Conceptos

- [[Cloudflare R2]] - Servicio que elimina los cargos por egress.
- [[Costo-de-infraestructura]] - El egress es un componente importante del costo total.
- [[Almacenamiento-de-archivos]] - Cómo se manejan los datos salientes.
- [[CDN]] - Los CDNs ayudan a reducir la latencia y a veces los costos de egress al servir contenido desde ubicaciones cercanas.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*