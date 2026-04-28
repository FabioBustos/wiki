---
title: Base de Datos MongoDB
date: 2026-04-27
tags: [mongodb, base-de-datos, nosql, persistencia, backend]
alias: [MongoDB, Mongo DB]
---

# Base de Datos MongoDB

## Definición

**MongoDB** es una base de datos NoSQL orientada a documentos, de código abierto, que almacena datos en documentos flexibles tipo JSON (BSON). Es conocida por su escalabilidad, flexibilidad y alto rendimiento, lo que la hace adecuada para aplicaciones modernas que requieren manejar grandes volúmenes de datos no estructurados o semiestructurados.

## Conceptos Clave

-   **Documento**: La unidad básica de datos en MongoDB, similar a una fila en una base de datos relacional, pero con una estructura más flexible. Los documentos son objetos BSON (una representación binaria de JSON).
-   **Colección**: Un grupo de documentos. Similar a una tabla en una base de datos relacional. Las colecciones no imponen un esquema fijo a los documentos que contienen.
-   **Base de Datos**: Un contenedor físico para colecciones. Un servidor MongoDB puede alojar múltiples bases de datos.
-   **BSON**: Binary JSON, el formato de almacenamiento de documentos en MongoDB.
-   **Escalabilidad Horizontal**: MongoDB está diseñado para escalar horizontalmente mediante sharding, distribuyendo los datos entre múltiples servidores.
-   **Índices**: Utilizados para mejorar el rendimiento de las consultas, similar a las bases de datos relacionales.

## Uso en el Sistema de Ticketera

MongoDB es nuestra base de datos principal para el backend [[NestJS]]. La utilizamos para almacenar información sobre usuarios, eventos, tickets, venues y otras entidades del sistema.

### Integración con NestJS

Utilizamos el paquete `@nestjs/mongoose` para integrar MongoDB con NestJS, lo que nos permite definir esquemas (Schemas) y modelos (Models) de forma declarativa.

```typescript
// src/events/schemas/event.schema.ts
import { Prop, Schema, SchemaFactory } from '@nestjs/mongoose';
import { Document } from 'mongoose';

export type EventDocument = Event & Document;

@Schema({ timestamps: true })
export class Event {
  @Prop({ required: true })
  name: string;

  @Prop()
  description: string;

  @Prop({ type: String, ref: 'Venue', required: true })
  venue: string; // Referencia al ID del Venue

  @Prop({ required: true })
  date: Date;

  @Prop({ default: true })
  isActive: boolean;
}

export const EventSchema = SchemaFactory.createForClass(Event);
```

### Gestión de la Base de Datos

-   **Desarrollo Local**: Ejecutamos MongoDB en un contenedor [[Docker]] a través de `docker-compose`.
-   **Producción/Staging**: Utilizamos servicios de bases de datos gestionadas proporcionados por [[Railway]] o [[Seenode]].

## Beneficios para el Proyecto

### [!success] Flexibilidad del Esquema
-   **Desarrollo Ágil**: Permite un desarrollo más rápido y flexible, ya que el esquema de los documentos puede evolucionar sin interrupciones.
-   **Datos Heterogéneos**: Facilita el manejo de datos que no encajan perfectamente en una estructura relacional rígida.

### [!success] Escalabilidad
-   **Escalabilidad Horizontal**: Diseñado para escalar horizontalmente, lo que es crucial para manejar el crecimiento de usuarios y eventos.
-   **Alto Rendimiento**: Ofrece un alto rendimiento para operaciones de lectura y escritura.

### [!success] Integración con Node.js
-   **Nativa con JSON**: Almacena datos en formato JSON (BSON), lo que se alinea perfectamente con el ecosistema JavaScript/Node.js.
-   **Mongoose**: La librería Mongoose facilita la interacción con MongoDB en entornos Node.js/TypeScript.

## Integración con Otros Servicios

-   **[[NestJS]]**: Framework backend principal que interactúa con MongoDB.
-   **[[Docker]]**: Para la ejecución de MongoDB en entornos de desarrollo local.
-   **[[Railway]] / [[Seenode]]**: Plataformas de despliegue que ofrecen addons de MongoDB gestionados.
-   **[[Sentry]]**: Para monitorear errores relacionados con la base de datos.
-   **[[APM]]**: Para monitorear el rendimiento de las consultas a la base de datos.

## Mejores Prácticas de Implementación

### [!tip] Diseño de Esquemas
-   **Modelado de Datos**: Aunque es NoSQL, un buen diseño de esquema es crucial para el rendimiento y la mantenibilidad.
-   **Referencias vs. Embebido**: Decidir cuándo embeber documentos y cuándo usar referencias a otros documentos.

### [!tip] Índices
-   **Optimización de Consultas**: Crear índices en los campos que se utilizan frecuentemente en las consultas para mejorar el rendimiento.
-   **Índices Compuestos**: Utilizar índices compuestos para consultas que involucran múltiples campos.

### [!tip] Seguridad
-   **Autenticación y Autorización**: Configurar la autenticación y autorización de usuarios de la base de datos.
-   **Cifrado en Reposo y en Tránsito**: Asegurar que los datos estén cifrados.
-   **Backups Regulares**: Implementar una estrategia de backup y recuperación.

## Solución de Problemas Comunes

### [!warning] Rendimiento Lento de Consultas
-   **Síntoma**: Las consultas a la base de datos tardan mucho tiempo.
-   **Solución**:
    -   Verificar el uso de índices.
    -   Analizar el plan de ejecución de las consultas (`.explain()`).
    -   Optimizar el diseño del esquema.

### [!warning] Errores de Conexión
-   **Síntoma**: La aplicación no puede conectarse a la base de datos.
-   **Solución**:
    -   Verificar la cadena de conexión (`DATABASE_URL`).
    -   Asegurarse de que la base de datos esté en ejecución y accesible.
    -   Comprobar las reglas de firewall o seguridad de red.

## Glosario de Términos

-   **NoSQL**: Tipo de base de datos que no utiliza el modelo relacional tradicional.
-   **BSON**: Binary JSON, el formato de almacenamiento de documentos en MongoDB.
-   **Sharding**: Técnica para distribuir datos entre múltiples servidores para escalar horizontalmente.
-   **Mongoose**: Librería ODM (Object Data Modeling) para MongoDB en Node.js.

## Relación con Otros Conceptos del Sistema

- [[NestJS]] - Backend que utiliza MongoDB.
- [[Docker]] - Contenerización de MongoDB en desarrollo.
- [[Railway]] / [[Seenode]] - Proveedores de bases de datos gestionadas.
- [[APM]] - Monitoreo del rendimiento de la base de datos.
- [[Seguridad-de-datos]] - Cifrado y protección de datos en la base de datos.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*