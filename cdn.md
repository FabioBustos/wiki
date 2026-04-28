---
title: CDN (Content Delivery Network)
date: 2026-04-27
tags: [cdn, red, rendimiento, web, cloudflare, entrega]
alias: [Content Delivery Network]
---

# CDN (Content Delivery Network)

## Definición

Una **CDN** (Content Delivery Network, o Red de Entrega de Contenidos) es una red distribuida geográficamente de servidores proxy y sus centros de datos. Su objetivo principal es acelerar la entrega de contenido web (imágenes, videos, hojas de estilo, scripts, etc.) a los usuarios, sirviéndolos desde la ubicación más cercana al usuario final.

## Cómo Funciona

1.  **Caché**: Cuando un usuario solicita contenido, la CDN lo sirve desde el servidor de borde (edge server) más cercano que tenga una copia en caché.
2.  **Origen**: Si el contenido no está en caché, el servidor de borde lo solicita al servidor de origen (donde reside el contenido original), lo almacena en caché y luego lo sirve al usuario.
3.  **Distribución Global**: La red de servidores de la CDN está distribuida por todo el mundo, reduciendo la latencia al minimizar la distancia física entre el usuario y el contenido.

## Beneficios Clave

-   **Mejora del Rendimiento**: Reduce significativamente los tiempos de carga de la página al servir contenido desde ubicaciones cercanas al usuario.
-   **Reducción de la Latencia**: Minimiza el tiempo que tardan los datos en viajar entre el servidor y el cliente.
-   **Mayor Disponibilidad**: Distribuye el contenido en múltiples servidores, lo que significa que si un servidor falla, otros pueden seguir sirviendo el contenido.
-   **Escalabilidad**: Puede manejar picos de tráfico y grandes volúmenes de solicitudes sin sobrecargar el servidor de origen.
-   **Reducción de Costos**: Al descargar el tráfico del servidor de origen, puede reducir los costos de ancho de banda y procesamiento.

## Uso en el Sistema de Ticketera

En nuestro proyecto, la CDN de Cloudflare es fundamental para la entrega eficiente de activos estáticos y contenido multimedia.

-   **Activos Estáticos**: Imágenes de eventos, logos, hojas de estilo CSS, scripts JavaScript del frontend [[nextjs]].
-   **Contenido Multimedia**: Videos promocionales o trailers de eventos (especialmente si se usa [[implementacion-de-cloudflare-stream|Cloudflare Stream]]).
-   **Origen de Contenido**: [[cloudflare-r2]] actúa como un origen ideal para la CDN de Cloudflare, ya que no cobra por la salida de datos.

## Relación con Otros Conceptos

- [[cloudflare-r2]] - Nuestro origen de almacenamiento de objetos.
- [[cloudflare-workers]] - Pueden interactuar con la CDN para lógica en el edge.
- [[optimizacion-de-imagenes]] - La CDN es clave para la entrega optimizada de imágenes.
- [[nextjs]] - Nuestro frontend se beneficia de la entrega rápida de activos.
- [[rendimiento]] - La CDN es una herramienta fundamental para mejorar el rendimiento web.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*