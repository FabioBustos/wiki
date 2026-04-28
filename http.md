---
title: HTTP (Hypertext Transfer Protocol)
date: 2026-04-27
tags: [http, protocolo, web, comunicación, frontend, backend]
alias: [Hypertext Transfer Protocol]
---

# HTTP (Hypertext Transfer Protocol)

## Definición

**HTTP** (Hypertext Transfer Protocol) es el protocolo de comunicación fundamental de la World Wide Web. Es un protocolo sin estado (stateless) basado en texto que permite la transferencia de información entre clientes (generalmente navegadores web) y servidores. HTTP es la base sobre la cual se construyen las interacciones web, incluyendo la carga de páginas, el envío de formularios y las llamadas a APIs.

## Conceptos Clave

-   **Cliente y Servidor**: La comunicación HTTP siempre ocurre entre un cliente que inicia una solicitud y un servidor que responde a esa solicitud.
-   **Solicitud (Request)**: Un mensaje enviado por el cliente al servidor, que incluye:
    -   **Método HTTP**: Indica la acción deseada (ej. GET, POST, PUT, DELETE).
    -   **URL**: El recurso al que se dirige la solicitud.
    -   **Encabezados (Headers)**: Metadatos sobre la solicitud (ej. `Content-Type`, `Authorization`).
    -   **Cuerpo (Body)**: Datos adicionales enviados con la solicitud (ej. datos de un formulario).
-   **Respuesta (Response)**: Un mensaje enviado por el servidor al cliente en respuesta a una solicitud, que incluye:
    -   **Código de Estado**: Indica el resultado de la solicitud (ej. 200 OK, 404 Not Found, 500 Internal Server Error).
    -   **Encabezados (Headers)**: Metadatos sobre la respuesta (ej. `Content-Type`, `Cache-Control`).
    -   **Cuerpo (Body)**: Los datos solicitados o un mensaje de error.
-   **Sin Estado (Stateless)**: Cada solicitud HTTP es independiente de las anteriores. El servidor no "recuerda" el estado de las solicitudes previas. Para mantener el estado, se utilizan mecanismos como cookies o tokens.

## Métodos HTTP Comunes

-   **GET**: Solicita una representación de un recurso específico. No debe tener efectos secundarios.
-   **POST**: Envía datos para ser procesados a un recurso específico. Causa efectos secundarios en el servidor.
-   **PUT**: Reemplaza todas las representaciones actuales del recurso de destino con la carga útil de la solicitud.
-   **DELETE**: Elimina un recurso específico.
-   **PATCH**: Aplica modificaciones parciales a un recurso.
-   **OPTIONS**: Se utiliza para describir las opciones de comunicación para el recurso de destino (usado en [[cors|CORS]]).

## HTTP vs HTTPS

-   **HTTP**: Las comunicaciones se envían en texto plano, lo que las hace vulnerables a la interceptación.
-   **HTTPS**: HTTP sobre TLS/SSL. Las comunicaciones están cifradas, proporcionando seguridad, integridad y autenticación. **Siempre se debe usar HTTPS en producción.**

## Uso en el Sistema de Ticketera

HTTP (y especialmente HTTPS) es el protocolo principal para la comunicación entre nuestro frontend [[nextjs]] y el backend [[nestjs]].

-   **API RESTful**: El backend expone una [[api-rest-especificacion|API RESTful]] que el frontend consume a través de solicitudes HTTP.
-   **[[cors|CORS]]**: La política de CORS se aplica a las solicitudes HTTP de origen cruzado.
-   **[[etag|ETags]]**: Utilizados para la validación de caché en respuestas HTTP.

## Relación con Otros Conceptos

- [[cors]] - Mecanismo de seguridad para solicitudes HTTP cross-origin.
- [[etag]] - Encabezado HTTP para caché y detección de cambios.
- [[nextjs]] - Frontend que realiza solicitudes HTTP.
- [[nestjs]] - Backend que responde a solicitudes HTTP.
- [[api-rest-especificacion]] - Define la estructura de las solicitudes y respuestas HTTP.
- [[seguridad-de-datos]] - HTTPS es fundamental para la seguridad en tránsito.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*