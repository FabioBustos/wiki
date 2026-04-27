---
title: DSN
date: 2026-04-27
tags:
  - sentry
  - configuración
  - monitoreo
---

# DSN (Data Source Name)

Un **DSN** (Data Source Name) es una cadena de configuración que le dice al SDK de Sentry a dónde enviar los eventos capturados. Contiene información esencial como el ID del proyecto, la clave de autenticación y la URL del servidor de Sentry.

## Formato de un DSN

Un DSN típico tiene este formato:
```
https://<public_key>@o<organization_id>.ingest.sentry.io/<project_id>
```

## Uso en Nuestro Sistema

En nuestro sistema de ticketera, utilizamos DSNs diferentes para cada entorno:

- **Frontend**: `NEXT_PUBLIC_SENTRY_DSN` (expuesto al cliente)
- **Backend**: `SENTRY_DSN` (mantenerse privado en el servidor)

## Seguridad

Aunque el DSN del frontend es público por diseño (necesario para que el SDK funcione en el navegador), es importante:
- Nunca exponer el DSN del backend en el frontend
- Rotar los DSNs periódicamente como medida de seguridad
- Usar proyectos separados en Sentry para diferentes entornos cuando sea apropiado

## Relación con Otros Conceptos

- [[Sentry]] - Plataforma que utiliza el DSN para recibir eventos
- [[Variables-de-entorno]] - Cómo gestionamos los DSNs de forma segura
- [[Release]] - Información de versión que se envía junto con los eventos
- [[Environment]] - Indicador de entorno que se incluye en los eventos