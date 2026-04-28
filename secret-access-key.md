---
title: Secret Access Key
date: 2026-04-27
tags: [credenciales, seguridad, autenticación, r2, s3, aws]
alias: [Clave de Acceso Secreta]
---

# Secret Access Key

## Definición

La **Secret Access Key** (Clave de Acceso Secreta) es la parte confidencial de un par de credenciales de seguridad que se utiliza para firmar criptográficamente las solicitudes programáticas a servicios en la nube, como [[cloudflare-r2]] (compatible con S3) o Amazon S3. Funciona como una contraseña para el acceso programático y debe mantenerse estrictamente confidencial.

## Componentes de las Credenciales

Un par de credenciales de acceso típicamente consiste en:

1.  **[[access-key-id|Access Key ID]]**: Un identificador único y no secreto.
2.  **Secret Access Key**: Una clave secreta que debe mantenerse confidencial (ej. `wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY`).

Ambos componentes son necesarios para firmar solicitudes criptográficamente y autenticar la identidad del solicitante. La Secret Access Key se utiliza para generar una firma única para cada solicitud, que el servicio en la nube verifica para asegurar que la solicitud proviene de una fuente autorizada.

## Importancia en el Proyecto

En nuestro sistema, la Secret Access Key se utiliza junto con el [[access-key-id|Access Key ID]] para que el backend [[nestjs]] pueda interactuar de forma segura con [[cloudflare-r2]] para operaciones de almacenamiento de objetos (subir, descargar, eliminar archivos). Su compromiso podría permitir a un atacante realizar operaciones no autorizadas en nuestro almacenamiento.

## Gestión y Seguridad

-   **Confidencialidad Absoluta**: La Secret Access Key **nunca debe ser expuesta en el código fuente, en logs, en el frontend o en cualquier lugar público**.
-   **Almacenamiento Seguro**: Debe almacenarse de forma segura, preferiblemente como [[variables-de-entorno]] en entornos de despliegue (ej. [[Railway]], [[Seenode]]) o en un gestor de secretos.
-   **Principio de Mínimo Privilegio**: Las credenciales deben tener solo los permisos necesarios para realizar las tareas requeridas.
-   **Rotación Regular**: Es una práctica de seguridad crítica rotar periódicamente las claves de acceso para reducir el riesgo en caso de compromiso.

## Configuración en el SDK de AWS

Cuando se utiliza el [[sdk-de-aws|SDK de AWS]] para interactuar con [[cloudflare-r2]], la Secret Access Key se configura en el objeto `credentials`:

```typescript
import { S3Client } from '@aws-sdk/client-s3';

const s3Client = new S3Client({
  endpoint: process.env.CLOUDFLARE_R2_ENDPOINT,
  region: 'auto',
  credentials: {
    accessKeyId: process.env.CLOUDFLARE_R2_ACCESS_KEY_ID,
    secretAccessKey: process.env.CLOUDFLARE_R2_SECRET_ACCESS_KEY, // Aquí se usa la Secret Access Key
  },
});
```

## Relación con Otros Conceptos

- [[access-key-id]] - El componente público del par de credenciales.
- [[gestion-de-credenciales]] - Prácticas para manejar estas claves de forma segura.
- [[variables-de-entorno]] - Método preferido para almacenar estas claves.
- [[cloudflare-r2]] - Servicio que requiere estas credenciales para acceso programático.
- [[sdk-de-aws]] - Biblioteca utilizada para configurar y usar estas claves.
- [[seguridad-de-datos]] - La protección de estas claves es fundamental para la seguridad.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*