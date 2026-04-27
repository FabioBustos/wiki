---
title: Almacenamiento de Archivos
date: 2026-04-27
tags: [almacenamiento, archivos, backend, frontend, r2]
---

# Almacenamiento de Archivos

Este documento describe las estrategias y consideraciones para el almacenamiento de archivos en el sistema.

## Definición

El **Almacenamiento de Archivos** se refiere a la gestión y persistencia de datos en forma de archivos, que pueden incluir imágenes, documentos, videos, tickets digitales, etc. En nuestro sistema, esto se integra con servicios de almacenamiento de objetos como [[Cloudflare R2]].

## Casos de Uso Principales

-   **Activos de Eventos**: Imágenes, videos, logos asociados a eventos.
-   **Tickets Digitales**: Generación y almacenamiento de e-tickets (ej. QR codes).
-   **Contenido Generado por Usuarios**: Fotos de perfil, documentos de verificación, adjuntos en reportes.
-   **Backups y Logs**: Copias de seguridad de bases de datos, logs de auditoría a largo plazo.
-   **Assets Estáticos del Frontend**: Fuentes, iconos, imágenes de la interfaz de usuario.

## Arquitectura de Almacenamiento

Utilizamos [[Cloudflare R2]] como nuestro servicio principal de almacenamiento de objetos debido a su modelo de precios sin cargos por salida de datos (egress), lo que lo hace ideal para servir activos a escala global.

### Componentes Clave

-   **Bucket R2**: Contenedor lógico donde se almacenan los archivos.
-   **Prefijos**: Utilizados para organizar los archivos de manera lógica (ej. `event-images/{eventId}/`, `tickets/{ticketId}/`).
-   **Claves de Objeto**: Nombres únicos para cada archivo, a menudo incluyendo timestamps o identificadores únicos para evitar colisiones.
-   **Metadata**: Información adicional adjunta a cada objeto (ej. `userId`, `eventId`, `contentType`).
-   **URLs Firmadas**: Para acceso seguro y temporal a archivos privados.

### Flujo de Carga de Archivos (Ejemplo: Imágenes de Eventos)

1.  **Frontend**: El usuario selecciona una imagen.
2.  **Frontend → Backend**: Solicita una URL firmada al backend para subir el archivo.
3.  **Backend → R2**: Genera una URL firmada con tiempo de expiración limitado.
4.  **Backend → Frontend**: Devuelve la URL firmada y la clave del objeto.
5.  **Frontend → R2**: Sube el archivo directamente a R2 usando la URL firmada.
6.  **Frontend → Backend**: Notifica el éxito de la subida y proporciona la URL pública del archivo.
7.  **Backend**: Guarda la URL pública en la base de datos asociada al evento.

## Consideraciones Técnicas

-   **SDK de AWS**: Se utiliza para interactuar con la API S3 de R2.
-   **Variables de Entorno**: Credenciales de R2 y endpoint se configuran de forma segura.
-   **CORS**: Configuración adecuada si se requiere acceso directo desde el frontend.
-   **Políticas de Ciclo de Vida**: Para gestionar la retención y eliminación automática de archivos.
-   **Monitoreo**: Integración con [[Sentry]] para rastrear errores en operaciones de almacenamiento.

## Relación con Otros Conceptos

- [[Cloudflare R2]]
- [[Prefix]]
- [[Metadata]]
- [[URL Firmada]]
- [[Políticas de Ciclo de Vida]]
- [[SDK-de-AWS]]
- [[Variables-de-entorno]]
- [[Sentry]]
- [[NestJS]] / [[Next.js]]

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*