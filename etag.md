---
title: ETag
date: 2026-04-27
tags: [etag, http, cache, almacenamiento, r2, s3, optimización]
alias: [Entity Tag]
---

# ETag

## Definición

Un **ETag** (Entity Tag) es un identificador único que se asigna a una versión específica de un recurso web. Es un mecanismo utilizado por el protocolo HTTP para la validación de caché y la detección de cambios en los recursos. Permite a los navegadores y servidores determinar si un recurso en caché es idéntico al recurso en el servidor, evitando la necesidad de descargar el recurso completo si no ha cambiado.

## Cómo Funciona

1.  **Primera Solicitud**: Cuando un cliente solicita un recurso por primera vez, el servidor lo envía junto con un encabezado `ETag` en la respuesta HTTP. El cliente almacena el recurso y su ETag en su caché.
2.  **Solicitudes Posteriores**: En solicitudes subsiguientes del mismo recurso, el cliente envía el ETag almacenado en un encabezado `If-None-Match`.
3.  **Validación del Servidor**:
    -   Si el ETag del cliente coincide con el ETag actual del recurso en el servidor, el servidor responde con un estado `304 Not Modified`, indicando que el cliente puede usar su versión en caché.
    -   Si los ETags no coinciden (el recurso ha cambiado), el servidor envía el nuevo recurso completo junto con su nuevo ETag y un estado `200 OK`.

## Uso en Almacenamiento de Objetos (R2/S3)

En servicios de almacenamiento de objetos como [[cloudflare-r2]] y Amazon S3, un ETag se genera automáticamente para cada [[objeto|objeto]] almacenado. Este ETag es típicamente un hash MD5 del contenido del [[objeto|objeto]] (o de las partes en el caso de [[multipart-upload|Multipart Upload]]).

-   **Detección de Cambios**: El ETag permite verificar si el contenido de un [[objeto|objeto]] ha cambiado.
-   **Integridad de Datos**: En el contexto de [[multipart-upload|Multipart Upload]], los ETags de las partes se utilizan para verificar la integridad de cada parte antes de ensamblar el [[objeto|objeto]] final.

## Beneficios

-   **Reducción del Ancho de Banda**: Evita la descarga innecesaria de recursos que no han cambiado.
-   **Mejora del Rendimiento**: Acelera la carga de páginas web al servir recursos desde la caché del cliente.
-   **Detección de Concurrencia**: Puede usarse para prevenir que múltiples clientes sobrescriban los cambios de otros en un recurso.

## Relación con Otros Conceptos

- [[http]] - Protocolo que utiliza ETags.
- [[cache]] - Mecanismo de optimización que se beneficia de ETags.
- [[cloudflare-r2]] - Servicio de almacenamiento que genera ETags para objetos.
- [[objeto]] - La entidad a la que se le asigna un ETag.
- [[multipart-upload]] - Los ETags son cruciales para la integridad en este proceso.
- [[versioning]] - Aunque relacionado con cambios, ETag se enfoca en la versión actual del contenido.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*