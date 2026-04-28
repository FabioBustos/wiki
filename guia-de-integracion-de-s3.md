---
title: Guía de Integración con S3
date: 2026-04-27
tags: [s3, r2, integración, backend, sdk, cloudflare]
---

# Guía de Integración con S3

Este documento proporciona una guía sobre cómo integrar aplicaciones con servicios de almacenamiento compatibles con S3, como [[cloudflare-r2]] y Amazon S3.

## Introducción

La API S3 es un estándar de facto para el almacenamiento de objetos. La mayoría de los servicios de almacenamiento en la nube ofrecen compatibilidad con esta API, lo que permite utilizar herramientas y SDKs comunes para interactuar con ellos.

## Principios de Integración

1.  **Configuración del Cliente**: Inicializar un cliente S3 con el [[endpoint]] correcto, [[gestion-de-credenciales|credenciales]] ([[access-key-id]] y [[secret-access-key]]) y [[region]] (si aplica).
2.  **Operaciones CRUD**: Utilizar los comandos S3 para crear (PutObject), leer (GetObject), actualizar (PutObject) y eliminar (DeleteObject) [[objeto|objetos]].
3.  **Gestión de Buckets**: Crear, listar y eliminar [[bucket|buckets]] según sea necesario.
4.  **URLs Firmadas**: Generar [[url-firmada|URLs temporales]] para acceso seguro a [[objeto|objetos]] privados.
5.  **Gestión de Errores**: Implementar manejo robusto de errores para operaciones de almacenamiento.

## Uso del [[sdk-de-aws]] (JavaScript/TypeScript)

El [[sdk-de-aws]] es la forma más común de interactuar con servicios S3-compatible.

### 1. Instalación

```bash
npm install @aws-sdk/client-s3 @aws-sdk/s3-request-presigner
```

### 2. Inicialización del Cliente

```typescript
// src/common/providers/r2-storage.provider.ts (ejemplo con Cloudflare R2)
import { S3Client } from '@aws-sdk/client-s3';

const s3Client = new S3Client({
  endpoint: process.env.CLOUDFLARE_R2_ENDPOINT, // Ej: https://<account_id>.r2.cloudflarestorage.com
  region: 'auto', // R2 usa 'auto'
  credentials: {
    accessKeyId: process.env.CLOUDFLARE_R2_ACCESS_KEY_ID,
    secretAccessKey: process.env.CLOUDFLARE_R2_SECRET_ACCESS_KEY,
  },
});
```

### 3. Operaciones Básicas

```typescript
import { PutObjectCommand, GetObjectCommand, DeleteObjectCommand } from '@aws-sdk/client-s3';
import { getSignedUrl } from '@aws-sdk/s3-request-presigner';

// ... (s3Client inicializado)

const BUCKET_NAME = process.env.CLOUDFLARE_R2_BUCKET;

// Subir archivo
async function uploadFile(key: string, file: Buffer, mimeType: string) {
  await s3Client.send(
    new PutObjectCommand({
      Bucket: BUCKET_NAME,
      Key: key,
      Body: file,
      ContentType: mimeType,
    })
  );
}

// Descargar archivo
async function getFile(key: string): Promise<Buffer> {
  const response = await s3Client.send(
    new GetObjectCommand({
      Bucket: BUCKET_NAME,
      Key: key,
    })
  );
  return Buffer.from(await response.Body.transformToByteArray());
}

// Eliminar archivo
async function deleteFile(key: string): Promise<void> {
  await s3Client.send(
    new DeleteObjectCommand({
      Bucket: BUCKET_NAME,
      Key: key,
    })
  );
}

// Generar URL firmada
async function getSignedUrl(key: string, expiresIn: number = 3600): Promise<string> {
  const command = new GetObjectCommand({ Bucket: BUCKET_NAME, Key: key });
  return getSignedUrl(s3Client, command, { expiresIn });
}
```

## Consideraciones para [[cloudflare-r2]]

-   **Endpoint**: Debe configurarse explícitamente con la URL del [[endpoint]] de R2.
-   **Región**: Generalmente se usa `'auto'` ya que R2 es global.
-   **Credenciales**: Se obtienen desde las [[variables-de-entorno]] configuradas en la plataforma de despliegue (ej. [[railway]]).
-   **Bucket Name**: Debe coincidir con el nombre del [[bucket]] creado en R2.

## Relación con Otros Conceptos

- [[cloudflare-r2]] - El servicio de almacenamiento objetivo.
- [[sdk-de-aws]] - La biblioteca utilizada para la integración.
- [[variables-de-entorno]] - Cómo se gestionan las credenciales y configuraciones.
- [[url-firmada]] - Técnica para acceso temporal y seguro.
- [[prefix]] - Cómo se organizan los [[objeto]]s dentro del [[bucket]].
- [[metadata]] - Cómo se asocia información adicional a los [[objeto]]s.
- [[politica-de-ciclo-de-vida]] - Reglas para gestionar [[objeto]]s a lo largo del tiempo.
- [[nestjs]] / [[nextjs]] - Frameworks donde se implementa la lógica de integración.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*