---
title: URL Firmada
date: 2026-04-27
tags: [seguridad, r2, cloudflare, acceso, autenticación]
---

# URL Firmada

Este documento explica el concepto de URL firmada y su aplicación en el contexto de [[Cloudflare R2]].

## Definición

Una **URL Firmada** (Signed URL) es una URL generada dinámicamente que otorga acceso temporal y limitado a un recurso específico (como un archivo en un bucket de almacenamiento) que normalmente estaría protegido o sería privado. La URL contiene información de autenticación y autorización incrustada, como una firma criptográfica, una fecha de expiración y, opcionalmente, permisos específicos.

## Propósito Principal

El objetivo principal de las URLs firmadas es permitir el acceso seguro a recursos privados sin necesidad de hacerlos públicos. Son ideales para escenarios donde se requiere un acceso controlado y de corta duración, como:

-   Permitir a un usuario descargar un archivo específico que ha comprado.
-   Permitir la subida directa de un archivo a un bucket de almacenamiento sin exponer credenciales de acceso a largo plazo.
-   Compartir temporalmente un archivo con un tercero.

## Funcionamiento

1.  **Generación**: Una entidad con permisos de acceso (generalmente el backend de la aplicación) genera la URL firmada.
2.  **Inclusión de Parámetros**: La URL incluye parámetros como:
    -   La clave del objeto (ruta del archivo).
    -   La fecha y hora de expiración.
    -   Una firma criptográfica calculada a partir de las credenciales secretas del generador, la clave del objeto y la fecha de expiración.
3.  **Distribución**: La URL firmada se comparte con el cliente (navegador, aplicación móvil).
4.  **Acceso**: El cliente utiliza la URL para acceder al recurso. El servidor de almacenamiento verifica la firma y la fecha de expiración antes de conceder el acceso. Si la firma es válida y la URL no ha expirado, se permite el acceso.

## Uso con Cloudflare R2

[[Cloudflare R2]] es compatible con la API S3, lo que significa que se pueden utilizar herramientas y bibliotecas estándar de AWS S3 (como `@aws-sdk/s3-request-presigner`) para generar URLs firmadas.

### Ejemplo de Generación (Backend NestJS)

```typescript
// src/common/providers/r2-storage.provider.ts (método getSignedUrl)
import { S3Client, GetObjectCommand } from '@aws-sdk/client-s3';
import { getSignedUrl } from '@aws-sdk/s3-request-presigner';

// ... (inicialización de s3Client como se mostró en el ejemplo de R2StorageService)

getSignedUrl(key: string, expiresIn: number = 3600): string {
  const command = new GetObjectCommand({
    Bucket: this.bucketName,
    Key: key,
  });

  // Generar URL firmada con expiración (por defecto 1 hora)
  return getSignedUrl(this.s3Client, command, { expiresIn });
}
```

### Ejemplo de Uso (Frontend Next.js)

```typescript
// pages/api/r2-upload-sign.ts (para subida)
// ... (código para generar URL de subida PUT)

// components/EventCard.tsx (para descarga/visualización)
async function fetchEventImageUrl(eventId: string) {
  const response = await fetch(`/api/r2-get-signed-url?key=events/${eventId}/image.jpg`);
  const data = await response.json();
  return data.url; // URL firmada para acceder a la imagen
}
```

## Beneficios

-   **Seguridad Mejorada**: Acceso temporal y limitado, reduciendo la ventana de exposición de recursos privados.
-   **Control de Acceso Granular**: Permite definir permisos específicos y duraciones para el acceso.
-   **Simplificación de Arquitectura**: Evita la necesidad de implementar sistemas de autenticación complejos para cada recurso.
-   **Eficiencia**: Permite subidas directas a almacenamiento sin pasar por el servidor de aplicaciones, liberando ancho de banda y recursos.

## Relación con Otros Conceptos

- [[Cloudflare R2]] - Servicio de almacenamiento que soporta URLs firmadas.
- [[SDK-de-AWS]] - Bibliotecas utilizadas para generar URLs firmadas.
- [[Seguridad-de-datos]] - Parte fundamental de las prácticas de seguridad.
- [[Gestión-de-credenciales]] - Cómo se manejan las claves secretas para firmar las URLs.
- [[Backend (NestJS)]] / [[Frontend (Next.js)]] - Dónde se generan y utilizan las URLs firmadas.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*