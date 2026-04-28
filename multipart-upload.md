---
title: Multipart Upload
date: 2026-04-27
tags: [almacenamiento, r2, s3, optimización, rendimiento, archivos-grandes]
alias: [Subida Multipart, Carga Multipart]
---

# Multipart Upload

## Definición

**Multipart Upload** es una funcionalidad ofrecida por servicios de almacenamiento de objetos como [[cloudflare-r2]] y Amazon S3 que permite subir un único [[objeto|objeto]] grande dividiéndolo en partes más pequeñas. Estas partes se suben de forma independiente, y una vez que todas las partes han sido subidas, el servicio de almacenamiento las ensambla para formar el [[objeto|objeto]] completo.

## Beneficios Clave

-   **Mejora del Rendimiento**: Al subir partes en paralelo, se puede reducir significativamente el tiempo total de subida para archivos grandes.
-   **Mayor Fiabilidad**: Si una parte falla al subirse, solo esa parte necesita ser reintentada, no el [[objeto|objeto]] completo.
-   **Pausar y Reanudar Subidas**: Permite pausar y reanudar subidas de archivos grandes, ya que cada parte se gestiona de forma independiente.
-   **Subidas de Archivos Grandes**: Es el método recomendado para subir archivos que superan un cierto tamaño (generalmente 100 MB o más).

## Proceso de Multipart Upload

El proceso general de una subida multipart consta de tres pasos principales:

1.  **Iniciar la Subida Multipart**: Se envía una solicitud al servicio de almacenamiento para iniciar una subida multipart. El servicio responde con un `Upload ID` único.
2.  **Subir Partes**: Se suben las partes del [[objeto|objeto]] utilizando el `Upload ID` y un número de parte. Cada parte se sube de forma independiente. El servicio devuelve un `ETag` para cada parte subida exitosamente.
3.  **Completar la Subida Multipart**: Una vez que todas las partes han sido subidas, se envía una solicitud final al servicio de almacenamiento con el `Upload ID` y una lista de los números de parte y sus `ETag`s correspondientes. El servicio ensambla las partes y crea el [[objeto|objeto]] final.

## Uso en el Sistema de Ticketera (Potencial)

Aunque actualmente nuestro sistema podría no manejar archivos extremadamente grandes, la funcionalidad de Multipart Upload sería relevante para:

-   **Videos de Eventos**: Si permitimos a los organizadores subir videos de alta resolución.
-   **Backups de Base de Datos**: Para subir archivos de backup grandes a [[cloudflare-r2]].
-   **Documentos Extensos**: Si se manejan documentos con muchos gráficos o contenido multimedia.

## Implementación con el SDK de AWS

El [[sdk-de-aws|SDK de AWS]] proporciona métodos para gestionar subidas multipart, simplificando la implementación de este proceso en el backend [[nestjs]].

## Relación con Otros Conceptos

- [[cloudflare-r2]] - Servicio que soporta Multipart Upload.
- [[objeto]] - La unidad que se sube en partes.
- [[sdk-de-aws]] - Biblioteca utilizada para implementar Multipart Upload.
- [[rendimiento]] - Mejora el rendimiento de subida de archivos grandes.
- [[fiabilidad]] - Aumenta la fiabilidad de las subidas.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*