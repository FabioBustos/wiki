---
title: Caché
date: 2026-04-27
tags: [cache, rendimiento, optimización, web, datos]
alias: [Caching]
---

# Caché

## Definición

La **Caché** es un mecanismo de almacenamiento temporal de datos que se utilizan con frecuencia. Su objetivo principal es acelerar el acceso a esos datos, ya que recuperarlos de la caché es mucho más rápido que volver a generarlos o solicitarlos desde su fuente original (ej. una base de datos o un servidor remoto).

## Tipos de Caché

La caché puede implementarse en diferentes niveles de una aplicación o sistema:

1.  **Caché del Navegador (Browser Cache)**:
    -   Almacena recursos estáticos (imágenes, CSS, JavaScript) en el navegador del usuario.
    -   Controlado por encabezados HTTP como `Cache-Control` y `Expires`, y validado con `ETag` o `Last-Modified`.

2.  **Caché de CDN (Content Delivery Network Cache)**:
    -   Almacena contenido estático o dinámico en servidores distribuidos globalmente, cerca de los usuarios.
    -   Reduce la latencia y la carga en el servidor de origen.
    -   Ejemplo: La [[cdn|CDN]] de Cloudflare.

3.  **Caché de Aplicación (Application Cache)**:
    -   Almacena resultados de consultas a bases de datos, respuestas de API o datos computados en la memoria del servidor de la aplicación.
    -   Reduce la carga en la base de datos y acelera las respuestas del backend.
    -   Ejemplo: Usar Redis o una caché en memoria en el backend [[nestjs]].

4.  **Caché de Base de Datos (Database Cache)**:
    -   Algunas bases de datos tienen mecanismos de caché internos para consultas frecuentes.
    -   También se puede implementar una capa de caché entre la aplicación y la base de datos.

## Importancia en el Sistema de Ticketera

La implementación estratégica de la caché es vital para el rendimiento y la escalabilidad de nuestro sistema de ticketera:

-   **Páginas de Eventos**: Las páginas de listado y detalle de eventos pueden beneficiarse enormemente de la caché de CDN y del navegador, ya que su contenido no cambia constantemente.
-   **Activos Estáticos**: Imágenes, CSS, JavaScript se sirven rápidamente desde la caché del navegador o la CDN.
-   **Respuestas de API**: Las respuestas de API para datos que no cambian con frecuencia (ej. categorías de eventos, información de [[venue|venues]]) pueden ser cacheadas en el backend.
-   **Reducción de Carga**: Disminuye la carga en el backend y la base de datos, lo que es crucial durante picos de tráfico (ej. venta de entradas).

## Mecanismos de Caché en Next.js

[[nextjs]] tiene mecanismos de caché integrados para mejorar el rendimiento:

-   **Caché de Datos**: En el App Router, las funciones de fetching de datos (`fetch`) son cacheadas por defecto.
-   **Caché de Solicitudes**: La caché de solicitudes de Next.js almacena los resultados de las solicitudes de datos.
-   **Caché de Componentes**: Los Server Components se pueden cachear.

## Mejores Prácticas

### [!tip] Estrategia de Invalidación
-   Definir una estrategia clara para invalidar la caché cuando los datos cambian (ej. revalidación bajo demanda en Next.js, TTL en Redis).

### [!tip] Caché en Múltiples Niveles
-   Implementar caché en todos los niveles relevantes (navegador, CDN, aplicación, base de datos) para maximizar el rendimiento.

### [!tip] Monitoreo
-   Monitorear las tasas de acierto de la caché (cache hit ratio) para asegurar que la caché está siendo efectiva.

## Relación con Otros Conceptos

- [[rendimiento]] - La caché es una técnica fundamental para mejorar el rendimiento.
- [[cdn]] - Redes de entrega de contenido que utilizan caché.
- [[etag]] - Encabezado HTTP utilizado para la validación de caché.
- [[nextjs]] - Framework con mecanismos de caché integrados.
- [[nestjs]] - Backend donde se puede implementar caché de aplicación.
- [[cloudflare-r2]] - Origen de contenido para la caché de CDN.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*