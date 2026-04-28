---
title: Base de Datos
date: 2026-04-27
tags: [base-de-datos, persistencia, datos, backend, mongodb, postgresql]
---

# Base de Datos

## Definición

Una **Base de Datos** es un conjunto organizado de datos que se almacena y se accede electrónicamente desde un sistema informático. Son fundamentales para cualquier aplicación moderna, ya que permiten la persistencia, recuperación y gestión eficiente de la información.

## Tipos de Bases de Datos

En el contexto de nuestro proyecto, consideramos principalmente dos tipos:

1.  **Bases de Datos NoSQL (Orientadas a Documentos)**:
    -   **Ejemplo**: [[base-de-datos-mongodb|MongoDB]]
    -   **Características**: Almacenan datos en documentos flexibles tipo JSON, no requieren un esquema fijo, son altamente escalables horizontalmente y adecuadas para datos semiestructurados o no estructurados.
    -   **Uso en el Proyecto**: Nuestra elección actual para la base de datos principal.

2.  **Bases de Datos Relacionales (SQL)**:
    -   **Ejemplo**: [[base-de-datos-postgresql|PostgreSQL]], MySQL
    -   **Características**: Almacenan datos en tablas con filas y columnas, requieren un esquema predefinido, garantizan la integridad de los datos a través de transacciones ACID y son ideales para datos estructurados con relaciones complejas.
    -   **Uso en el Proyecto**: Considerada como una alternativa potencial si los requisitos de consistencia o relaciones se vuelven más estrictos.

## Importancia en el Sistema de Ticketera

La base de datos es el corazón de nuestro sistema, ya que almacena toda la información crítica:

-   **Usuarios**: Perfiles, credenciales, historial de compras.
-   **Eventos**: Detalles, fechas, ubicaciones, organizadores.
-   **Tickets**: Información de tickets, estado, códigos de validación.
-   **Venues**: Datos de recintos, direcciones.
-   **Transacciones**: Registros de pagos, reembolsos.

## Gestión de la Base de Datos

-   **Desarrollo Local**: Utilizamos [[Docker]] para ejecutar instancias de bases de datos (ej. MongoDB) en entornos de desarrollo local, asegurando consistencia.
-   **Producción/Staging**: Nos apoyamos en servicios de bases de datos gestionadas ofrecidos por plataformas como [[Railway]] o [[Seenode]]. Estos servicios se encargan de la alta disponibilidad, backups, parches y escalabilidad.

## Integración con el Backend

El backend [[NestJS]] es el principal consumidor y productor de datos en la base de datos. Utiliza ORMs (Object-Relational Mappers) o ODMs (Object-Document Mappers) para interactuar con la base de datos de manera programática.

## Consideraciones Clave

-   **Diseño de Esquemas**: Fundamental para el rendimiento y la mantenibilidad, independientemente del tipo de base de datos.
-   **Índices**: Cruciales para optimizar la velocidad de las consultas.
-   **Seguridad**: Cifrado en reposo y en tránsito, control de acceso, backups regulares.
-   **Escalabilidad**: La capacidad de la base de datos para manejar el crecimiento de datos y usuarios.
-   **Consistencia**: Garantizar que los datos sean precisos y fiables.

## Relación con Otros Conceptos

- [[NestJS]] - Backend que interactúa con la base de datos.
- [[Docker]] - Contenerización de bases de datos en desarrollo.
- [[Railway]] / [[Seenode]] - Proveedores de bases de datos gestionadas.
- [[APM]] - Monitoreo del rendimiento de la base de datos.
- [[Seguridad-de-datos]] - Protección de la información almacenada.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*