---
title: Access Key ID
date: 2026-04-27
tags: [credenciales, seguridad, autenticación, r2, s3, aws]
alias: [ID de Clave de Acceso]
---

# Access Key ID

## Definición

El **Access Key ID** (ID de Clave de Acceso) es una parte de un par de credenciales de seguridad que se utiliza para identificar de forma programática a un usuario o una aplicación que intenta acceder a un servicio en la nube, como [[cloudflare-r2]] (compatible con S3) o Amazon S3. Funciona como un nombre de usuario para el acceso programático.

## Componentes de las Credenciales

Un par de credenciales de acceso típicamente consiste en:

1.  **Access Key ID**: Un identificador único y no secreto (ej. `AKIAIOSFODNN7EXAMPLE`).
2.  **Secret Access Key**: Una clave secreta que debe mantenerse confidencial (ej. `wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY`).

Ambos componentes son necesarios para firmar solicitudes criptográficamente y autenticar la identidad del solicitante.

## Importancia en el Proyecto

En nuestro sistema, el Access Key ID se utiliza junto con el Secret Access Key para que el backend [[nestjs]] pueda interactuar de forma segura con [[cloudflare-r2]] para operaciones de almacenamiento de objetos (subir, descargar, eliminar archivos).

## Gestión y Seguridad

-   **Confidencialidad**: Aunque el Access Key ID no es secreto por sí mismo, siempre debe tratarse como parte de un par de credenciales sensibles.
-   **Almacenamiento Seguro**: Tanto el Access Key ID como el Secret Access Key deben almacenarse de forma segura, preferiblemente como [[variables-de-entorno]] en entornos de despliegue (ej. [[Railway]], [[Seenode]]) o en un gestor de secretos.
-   **Principio de Mínimo Privilegio**: Las credenciales deben tener solo los permisos necesarios para realizar las tareas requeridas.
-   **Rotación Regular**: Es una buena práctica rotar periódicamente las claves de acceso para reducir el riesgo en caso de compromiso.

## Configuración en el SDK de AWS

Cuando se utiliza el [[sdk-de-aws|SDK de AWS]] para interactuar con [[cloudflare-r2]], el Access Key ID se configura en el objeto `credentials`:

```typescript
import { S3Client } from '@aws-sdk/client-s3';

const s3Client = new S3Client({
  endpoint: process.env.CLOUDFLARE_R2_ENDPOINT,
  region: 'auto',
  credentials: {
    accessKeyId: process.env.CLOUDFLARE_R2_ACCESS_KEY_ID, // Aquí se usa el Access Key ID
    secretAccessKey: process.env.CLOUDFLARE_R2_SECRET_ACCESS_KEY,
  },
});
```

## Relación con Otros Conceptos

- [[secret-access-key]] - El componente secreto del par de credenciales.
- [[gestion-de-credenciales]] - Prácticas para manejar estas claves de forma segura.
- [[variables-de-entorno]] - Método preferido para almacenar estas claves.
- [[cloudflare-r2]] - Servicio que requiere estas credenciales para acceso programático.
- [[sdk-de-aws]] - Biblioteca utilizada para configurar y usar estas claves.
- [[seguridad-de-datos]] - La protección de estas claves es fundamental para la seguridad.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*