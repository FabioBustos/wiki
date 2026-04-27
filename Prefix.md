---
title: Prefix (R2/S3)
date: 2026-04-27
tags: [r2, s3, almacenamiento, organización, nomenclatura]
---

# Prefix (R2/S3)

Este documento explica el concepto de "Prefix" en el contexto de servicios de almacenamiento de objetos como [[Cloudflare R2]] y Amazon S3.

## Definición

Un **Prefix** es una cadena de texto que se utiliza para organizar objetos dentro de un bucket de almacenamiento. Funciona de manera similar a una carpeta en un sistema de archivos tradicional, permitiendo agrupar objetos relacionados bajo un nombre común. Los prefixes se aplican a la "clave" (nombre completo) de un objeto.

## Funcionamiento

Cuando se almacena un objeto en un bucket S3 o R2, se le asigna una clave única. Un prefix forma parte de esta clave, generalmente al principio, y se separa de otras partes de la clave mediante un carácter delimitador (comúnmente una barra `/`).

**Ejemplo de Claves con Prefixes:**

-   `event-images/concert-123/poster.jpg`
    -   **Bucket**: `my-event-assets`
    -   **Prefix**: `event-images/concert-123/`
    -   **Objeto**: `poster.jpg`
-   `user-uploads/usr_abc/profile-pic.png`
    -   **Prefix**: `user-uploads/usr_abc/`
    -   **Objeto**: `profile-pic.png`
-   `tickets/event_xyz/vip-ticket-1a2b3c.pdf`
    -   **Prefix**: `tickets/event_xyz/`
    -   **Objeto**: `vip-ticket-1a2b3c.pdf`

## Beneficios de Usar Prefixes

1.  **Organización Lógica**: Facilita la gestión y localización de objetos relacionados.
2.  **Control de Acceso Granular**: Permite aplicar políticas de seguridad (IAM en AWS, o configuraciones de acceso en R2) a nivel de prefix, controlando quién puede acceder a qué grupos de objetos.
3.  **Listado y Filtrado Eficiente**: Permite listar objetos que pertenecen a un prefix específico, similar a listar archivos en una carpeta.
4.  **Gestión de Costos**: Ayuda a monitorear el uso de almacenamiento por categoría de objeto.
5.  **Estrategias de Ciclo de Vida**: Se pueden definir políticas para mover o eliminar objetos basados en sus prefixes y antigüedad.

## Mejores Prácticas

-   **Nomenclatura Clara**: Utilizar prefixes descriptivos que indiquen el tipo de contenido, el ID del objeto asociado (evento, usuario), y opcionalmente fechas o versiones.
    -   Ejemplo: `event-images/{eventId}/{timestamp}-{randomString}.{ext}`
-   **Consistencia**: Mantener un esquema de nomenclatura uniforme en todo el bucket.
-   **Evitar Prefixes Demasiado Largos o Complejos**: Puede dificultar la gestión y el rendimiento en algunos sistemas.
-   **Usar Delimitadores Correctamente**: Generalmente `/` para simular estructura de carpetas.

## Relación con Otros Conceptos

- [[Cloudflare R2]] / [[Amazon S3]] - Servicios que implementan el concepto de buckets y claves con prefixes.
- [[Almacenamiento-de-archivos]] - Cómo se organizan los datos.
- [[Seguridad-de-datos]] - Control de acceso a través de prefixes.
- [[Gestión-de-credenciales]] - Cómo se aplican permisos a nivel de prefix.
- [[Políticas de Ciclo de Vida]] - Reglas que pueden aplicarse a objetos dentro de un prefix.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*