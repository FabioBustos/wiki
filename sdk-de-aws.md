---
title: SDK de AWS
date: 2026-04-27
tags: [aws, sdk, desarrollo, cloud, r2, s3, javascript, typescript]
alias: [AWS SDK, AWS-SDK]
---

# SDK de AWS

## Definición

El **SDK de AWS (Software Development Kit de Amazon Web Services)** es un conjunto de bibliotecas, herramientas, documentación y ejemplos de código que facilitan la interacción con los servicios de AWS desde diferentes lenguajes de programación. Permite a los desarrolladores integrar sus aplicaciones con servicios de AWS como S3, EC2, Lambda, DynamoDB, entre otros, de manera programática.

## Importancia en el Proyecto

Aunque nuestro servicio principal de almacenamiento de objetos es [[cloudflare-r2]], que no es un servicio de AWS, Cloudflare R2 es compatible con la API de S3. Esto significa que podemos utilizar el SDK de AWS para JavaScript/TypeScript para interactuar con Cloudflare R2, aprovechando la familiaridad y robustez de este SDK.

### Uso con Cloudflare R2

Para interactuar con [[cloudflare-r2]], configuramos el `S3Client` del SDK de AWS para que apunte al endpoint de R2 y utilice las credenciales de R2.

```typescript
// Ejemplo de inicialización del S3Client para Cloudflare R2
import { S3Client } from '@aws-sdk/client-s3';

const s3Client = new S3Client({
  endpoint: process.env.CLOUDFLARE_R2_ENDPOINT, // URL del endpoint de R2
  region: 'auto', // R2 usa 'auto' como región
  credentials: {
    accessKeyId: process.env.CLOUDFLARE_R2_ACCESS_KEY_ID,
    secretAccessKey: process.env.CLOUDFLARE_R2_SECRET_ACCESS_KEY,
  },
});
```

### Funcionalidades Clave Utilizadas

-   **`@aws-sdk/client-s3`**: Para realizar operaciones CRUD (PutObject, GetObject, DeleteObject) en objetos almacenados en R2.
-   **`@aws-sdk/s3-request-presigner`**: Para generar [[url-firmada|URLs firmadas]] que permiten acceso temporal y seguro a objetos privados en R2, o para permitir subidas directas desde el frontend.

## Beneficios

-   **Compatibilidad**: Permite interactuar con [[cloudflare-r2]] a pesar de no ser un servicio de AWS.
-   **Familiaridad**: Muchos desarrolladores ya están familiarizados con el SDK de AWS, lo que reduce la curva de aprendizaje.
-   **Robustez**: El SDK está bien mantenido y es robusto, con manejo de reintentos, errores y otras características.
-   **Generación de URLs Firmadas**: Facilita la implementación de patrones de subida y descarga segura de archivos.

## Relación con Otros Conceptos

- [[cloudflare-r2]] - Servicio de almacenamiento de objetos con el que interactuamos.
- [[variables-de-entorno]] - Utilizadas para configurar las credenciales y el endpoint del SDK.
- [[url-firmada]] - Funcionalidad clave implementada con el SDK.
- [[integracion-con-backend]] - El backend [[nestjs]] utiliza el SDK para gestionar archivos.
- [[seguridad-de-datos]] - El SDK ayuda a implementar prácticas de seguridad.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*