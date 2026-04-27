---
title: Metadata (Objetos de Almacenamiento)
date: 2026-04-27
tags: [almacenamiento, r2, s3, objetos, datos]
---

# Metadata (Objetos de Almacenamiento)

Este documento explica el concepto de "Metadata" asociado a los objetos en servicios de almacenamiento como [[Cloudflare R2]] y Amazon S3.

## Definición

**Metadata** se refiere a los datos que describen otros datos. En el contexto del almacenamiento de objetos, la metadata es información adicional asociada a cada objeto (archivo) que proporciona contexto sobre él, pero que no forma parte del contenido del objeto en sí.

## Tipos de Metadata

Existen dos categorías principales de metadata en el almacenamiento de objetos:

1.  **Metadata del Sistema**: Información gestionada por el servicio de almacenamiento para operar y organizar los objetos. Incluye:
    -   **Clave (Key)**: El nombre único del objeto dentro del bucket.
    -   **Tamaño (Size)**: El tamaño del objeto en bytes.
    -   **Tipo de Contenido (Content-Type)**: El tipo MIME del objeto (ej. `image/jpeg`, `application/pdf`).
    -   **Fecha de Modificación**: Timestamp de la última vez que se modificó el objeto.
    -   **ETag**: Un identificador único para la versión del objeto.
    -   **Versiones**: Si el versionamiento está habilitado, información sobre las versiones del objeto.

2.  **Metadata Definida por el Usuario (User-Defined Metadata)**: Pares clave-valor personalizados que el usuario puede adjuntar a un objeto para almacenar información adicional relevante para su aplicación.
    -   **Ejemplos**:
        -   `eventId`: "concert-123" (para asociar una imagen a un evento específico)
        -   `userId`: "usr_abc" (para indicar quién subió el archivo)
        -   `purpose`: "event-poster" (para describir el uso del archivo)
        -   `customTag`: "featured"
    -   **Formato**: Generalmente se envían como encabezados HTTP personalizados (ej. `x-amz-meta-userId: usr_abc`).

## Uso y Beneficios

-   **Organización y Búsqueda**: La metadata definida por el usuario puede facilitar la búsqueda y el filtrado de objetos sin necesidad de descargar su contenido.
-   **Contexto de Aplicación**: Proporciona información crucial para la lógica de negocio (ej. asociar un archivo a un evento o usuario).
-   **Control de Acceso**: Aunque la metadata del sistema como la clave es fundamental para el acceso, la metadata definida por el usuario puede usarse en políticas de acceso más complejas (dependiendo del servicio).
-   **Optimización de Entrega**: El `Content-Type` es esencial para que los navegadores y clientes interpreten correctamente el contenido del objeto.

## Implementación con Cloudflare R2

Cloudflare R2 soporta la adición de metadata definida por el usuario al subir objetos. Esta metadata se puede leer junto con la información del objeto y se puede utilizar en [[Cloudflare Workers]] para lógica personalizada o para servir contenido de manera más inteligente.

## Relación con Otros Conceptos

- [[Cloudflare R2]] / [[Amazon S3]] - Servicios que manejan objetos y su metadata.
- [[Prefix]] - La clave del objeto, que a menudo incluye prefixes para organización.
- [[Políticas de Ciclo de Vida]] - Pueden basarse en metadata del sistema (ej. fecha de modificación).
- [[Gestión-de-credenciales]] - La metadata del sistema es clave para la autenticación y autorización.
- [[Backend (NestJS)]] - Cómo el backend puede leer y escribir metadata definida por el usuario.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*