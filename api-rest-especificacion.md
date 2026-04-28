---
title: API REST - Especificación
date: 2026-04-27
tags: [api, rest, especificacion, backend, comunicacion, estandar]
alias: [API RESTful, REST API Specification]
---

# API REST - Especificación

## Definición

Una **API REST** (Representational State Transfer Application Programming Interface) es un conjunto de principios arquitectónicos para diseñar servicios web. Se basa en el protocolo HTTP y utiliza métodos estándar (GET, POST, PUT, DELETE) para interactuar con recursos identificados por URLs. Una **Especificación de API REST** es un documento que describe de manera formal y detallada cómo interactuar con esta API, incluyendo sus endpoints, métodos, parámetros, formatos de datos y códigos de respuesta.

## Principios Clave de REST

-   **Cliente-Servidor**: Separación de preocupaciones entre la interfaz de usuario (cliente) y el almacenamiento de datos (servidor).
-   **Sin Estado (Stateless)**: Cada solicitud del cliente al servidor debe contener toda la información necesaria para entender la solicitud. El servidor no debe almacenar ningún contexto del cliente entre solicitudes.
-   **Cacheable**: Las respuestas deben ser definidas como cacheables o no cacheables para mejorar el rendimiento.
-   **Sistema de Capas**: Un cliente no puede saber si está conectado directamente al servidor final o a un intermediario.
-   **Interfaz Uniforme**: Un conjunto de restricciones de diseño que simplifican la arquitectura y mejoran la visibilidad. Incluye:
    -   **Identificación de Recursos**: Los recursos se identifican por URLs únicas.
    -   **Manipulación de Recursos a través de Representaciones**: Los clientes interactúan con los recursos a través de representaciones (ej. JSON, XML).
    -   **Mensajes Auto-descriptivos**: Cada mensaje contiene suficiente información para que el receptor lo entienda.
    -   **HATEOAS (Hypermedia As The Engine Of Application State)**: Los clientes interactúan con la aplicación a través de hipervínculos proporcionados dinámicamente por el servidor.

## Importancia en el Proyecto

Nuestra API REST es el principal punto de comunicación entre el frontend [[nextjs]] y el backend [[nestjs]]. Una especificación clara y detallada es crucial para:

-   **Colaboración**: Permite a los equipos de frontend y backend trabajar de forma independiente pero coordinada.
-   **Consistencia**: Asegura que todos los desarrolladores entiendan cómo interactuar con la API.
-   **Documentación**: Sirve como documentación viva para la API, facilitando el onboarding y el mantenimiento.
-   **Testing**: Facilita la creación de pruebas automatizadas para la API.
-   **Integración Externa**: Permite que terceros (ej. socios, otras aplicaciones) se integren con nuestro sistema.

## Herramientas de Especificación

-   **OpenAPI (anteriormente Swagger)**: Un estándar para describir APIs RESTful. Permite generar documentación interactiva, SDKs de cliente y stubs de servidor.
-   **Postman/Insomnia**: Herramientas para probar y documentar APIs.

## Ejemplos de Endpoints en Nuestro Sistema

| Recurso | Método | URL | Descripción |
|---|---|---|---|
| Usuarios | `POST` | `/auth/register` | Registra un nuevo usuario |
| Usuarios | `POST` | `/auth/login` | Autentica un usuario y devuelve un [[jwt|JWT]] |
| Eventos | `GET` | `/events` | Obtiene una lista de eventos (con filtros opcionales) |
| Eventos | `GET` | `/events/{id}` | Obtiene los detalles de un evento específico |
| Eventos | `POST` | `/events` | Crea un nuevo evento |
| Tickets | `GET` | `/users/{userId}/tickets` | Obtiene los tickets de un usuario |
| Tickets | `POST` | `/events/{eventId}/tickets/purchase` | Compra tickets para un evento |
| Venues | `GET` | `/venues` | Obtiene una lista de [[venue|venues]] |

## Relación con Otros Conceptos

- [[nestjs]] - El framework backend que implementa la API REST.
- [[nextjs]] - El frontend que consume la API REST.
- [[http]] - Protocolo subyacente de la API REST.
- [[jwt]] - Utilizado para la autenticación y autorización en la API.
- [[integracion-con-backend]] - La API REST es el corazón de esta integración.
- [[endpoint]] - Cada recurso de la API se expone a través de uno o más endpoints.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*