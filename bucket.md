---
title: Bucket (Almacenamiento de Objetos)
date: 2026-04-27
tags: [bucket, almacenamiento, objetos, r2, s3, cloud]
alias: [Object Storage Bucket]
---

# Bucket (Almacenamiento de Objetos)

## Definición

Un **Bucket** es un contenedor lógico fundamental en los servicios de almacenamiento de objetos, como [[cloudflare-r2]] y Amazon S3. Actúa como una carpeta de nivel superior donde se almacenan los [[objeto|objetos]] (archivos) y sus [[metadata|metadatos]]. Los buckets proporcionan un espacio de nombres único a nivel global o por cuenta, y son la unidad principal para aplicar políticas de acceso, configuración de CORS y gestión del ciclo de vida.

## Características Clave

-   **Nombre Único**: Cada bucket debe tener un nombre único dentro del espacio de nombres del proveedor de almacenamiento (ej. globalmente para S3, o por cuenta para R2).
-   **Contenedor de Objetos**: Almacena una cantidad ilimitada de [[objeto|objetos]].
-   **Políticas de Acceso**: Se pueden aplicar políticas de acceso a nivel de bucket para controlar quién puede leer, escribir o eliminar [[objeto|objetos]] dentro de él.
-   **Configuración de CORS**: Permite definir reglas de [[cors|CORS]] para controlar el acceso de origen cruzado.
-   **Gestión del Ciclo de Vida**: Se pueden configurar [[politica-de-ciclo-de-vida|políticas de ciclo de vida]] para automatizar la transición o eliminación de [[objeto|objetos]].
-   **Versionamiento**: Opcionalmente, se puede habilitar el [[versioning|versionamiento]] para mantener múltiples versiones de un [[objeto]].

## Uso en el Sistema de Ticketera

En nuestro proyecto, utilizamos buckets en [[cloudflare-r2]] para organizar y almacenar diferentes tipos de activos:

-   **`event-assets`**: Para imágenes, videos y documentos relacionados con eventos.
-   **`user-uploads`**: Para fotos de perfil de usuarios o documentos de verificación.
-   **`ticket-data`**: Para códigos QR de tickets generados y plantillas.
-   **`backups`**: Para copias de seguridad de la base de datos o logs.

## Mejores Prácticas

### [!tip] Nombres Descriptivos
-   Utilizar nombres de bucket que reflejen su propósito (ej. `mi-app-imagenes-eventos`, `mi-app-backups`).

### [!tip] Principio de Mínimo Privilegio
-   Configurar políticas de acceso a nivel de bucket para otorgar solo los permisos necesarios a las aplicaciones o usuarios.

### [!tip] Organización con Prefixes
-   Dentro de un bucket, utilizar [[prefix|prefixes]] para organizar lógicamente los [[objeto|objetos]] (ej. `event-assets/event-id-123/poster.jpg`).

### [!tip] Seguridad
-   Mantener los buckets privados por defecto y utilizar [[url-firmada|URLs firmadas]] para acceso temporal y controlado.
-   Habilitar el cifrado en reposo para todos los [[objeto|objetos]].

## Relación con Otros Conceptos

- [[cloudflare-r2]] - Nuestro proveedor de almacenamiento de objetos.
- [[objeto]] - La unidad fundamental de almacenamiento dentro de un bucket.
- [[prefix]] - Para organizar objetos dentro de un bucket.
- [[politica-de-ciclo-de-vida]] - Reglas aplicadas a los objetos dentro de un bucket.
- [[cors]] - Configuración de seguridad a nivel de bucket.
- [[versioning]] - Característica opcional de los buckets.
- [[seguridad-de-datos]] - Las políticas de bucket son clave para la seguridad.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*