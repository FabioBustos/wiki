---
title: NestJS
date: 2026-04-27
tags: [nestjs, backend, framework, typescript, nodejs, desarrollo, api, microservicios]
alias: [Nest.js, Nest Framework]
obsidian_ui: true
---

# NestJS

## Definición

**NestJS** es un framework progresivo de Node.js para construir aplicaciones del lado del servidor eficientes, escalables y confiables. Está construido con [[typescript]] y combina elementos de programación orientada a objetos (OOP), programación funcional reactiva (FRP) y programación funcional. Utiliza una arquitectura modular inspirada en Angular, lo que facilita la organización del código y la creación de aplicaciones empresariales.

> [!info] Conceptos Clave
> -   **Módulos**: Clases decoradas con `@Module()` que organizan la aplicación en bloques funcionales.
> -   **Controladores**: Manejan las solicitudes entrantes y devuelven respuestas al cliente.
> -   **Servicios (Providers)**: Clases que contienen la lógica de negocio y pueden ser inyectadas en otros componentes.
> -   **Inyección de Dependencias**: Mecanismo central de NestJS para gestionar las dependencias entre componentes.
> -   **Decoradores**: Utilizados para añadir metadatos a clases, métodos y propiedades (ej. `@Controller()`, `@Injectable()`).
> -   **Pipes**: Transforman los datos de entrada o validan su formato.
> -   **Guards**: Protegen las rutas basándose en la lógica de autorización.
> -   **Interceptors**: Permiten interceptar y modificar solicitudes y respuestas.
> -   **Filtros de Excepciones**: Capturan y manejan excepciones no controladas.
> -   **Microservicios**: Soporte nativo para construir arquitecturas de microservicios con diferentes transportes (TCP, Redis, gRPC, Kafka, etc.).

## Uso en el Sistema de Ticketera

NestJS es el framework principal para el desarrollo de nuestro backend. Lo utilizamos para construir la [[api-rest-especificacion|API RESTful]] que sirve al frontend [[nextjs]], así como para manejar la lógica de negocio, la interacción con la base de datos y la integración con servicios externos.

### Estructura del Proyecto Backend

Nuestro proyecto backend se encuentra en `desarrollo/venta-entradas-v2-backend` y sigue una estructura modular y limpia.

```
venta-entradas-v2-backend/
├── src/
│   ├── app.module.ts       # Módulo raíz
│   ├── main.ts             # Punto de entrada de la aplicación
│   ├── auth/               # Módulo de autenticación
│   │   ├── auth.controller.ts
│   │   ├── auth.service.ts
│   │   └── auth.module.ts
│   ├── events/             # Módulo de eventos
│   │   ├── events.controller.ts
│   │   ├── events.service.ts
│   │   ├── events.module.ts
│   │   └── schemas/
│   ├── users/              # Módulo de usuarios
│   ├── common/             # Módulo de utilidades compartidas (pipes, guards, interceptors)
│   ├── config/             # Configuración de la aplicación
│   └── database/           # Conexión a la base de datos
├── test/                   # Pruebas e2e
├── nest-cli.json           # Configuración de Nest CLI
├── package.json
└── tsconfig.json
```

### Implementación de la API

-   **Controladores**: Definen los endpoints de la API (ej. `/events`, `/users`, `/auth`).
-   **Servicios**: Contienen la lógica de negocio para cada entidad (ej. `EventsService`, `AuthService`).
-   **Módulos**: Agrupan funcionalidades relacionadas (ej. `AuthModule`, `EventsModule`).
-   **Pipes de Validación**: Utilizados para validar los datos de entrada de las solicitudes HTTP.
-   **Guards de Autenticación/Autorización**: Protegen los endpoints de la API.

## Beneficios para el Proyecto

### [!success] Arquitectura Robusta y Escalable
-   **Modularidad**: Facilita la organización del código en módulos reutilizables y mantenibles.
-   **Escalabilidad**: Diseñado para construir aplicaciones que pueden crecer y escalar horizontalmente.
-   **Microservicios**: Soporte nativo para arquitecturas de microservicios, permitiendo dividir la aplicación en servicios más pequeños y manejables.

### [!success] Productividad del Desarrollador
-   **[[typescript]] de Primera Clase**: Aprovecha las ventajas de TypeScript para un código más seguro y fácil de mantener.
-   **CLI Potente**: Nest CLI acelera el desarrollo con generadores de código para módulos, controladores, servicios, etc.
-   **Documentación Excelente**: La documentación oficial es exhaustiva y fácil de seguir.

### [!success] Mantenibilidad y Calidad de Código
-   **Patrones de Diseño**: Fomenta el uso de patrones de diseño probados (ej. Inyección de Dependencias, Decoradores).
-   **Testing Integrado**: Facilita la escritura de pruebas unitarias y de integración.
-   **Comunidad Activa**: Gran comunidad y ecosistema de librerías y herramientas.

## Integración con Otros Servicios

-   **[[nextjs]]**: Nuestro frontend se comunica con la API de NestJS.
-   **[[base-de-datos-mongodb|MongoDB]]**: Base de datos principal para la persistencia de datos, integrada a través de `@nestjs/mongoose`.
-   **[[sentry]]**: Para monitoreo de errores y rendimiento en el backend.
-   **[[cloudflare-r2]]**: Integración para el almacenamiento de objetos (imágenes, tickets) a través de un servicio de almacenamiento.
-   **[[docker]]**: Para contenerizar la aplicación NestJS en desarrollo y producción.
-   **[[railway]] / [[seenode]]**: Plataformas de despliegue para la aplicación NestJS.
-   **[[jwt]]**: Utilizado para la autenticación y autorización de usuarios.
-   **[[ollama]]**: Potencial integración para tareas de procesamiento de lenguaje natural internas.

## Mejores Prácticas de Implementación

### [!tip] Estructura Modular
-   Organizar la aplicación en módulos lógicos (ej. `AuthModule`, `EventsModule`, `UsersModule`).
-   Mantener los módulos pequeños y con una única responsabilidad.

### [!tip] Inyección de Dependencias
-   Utilizar la inyección de dependencias de NestJS para gestionar las dependencias entre servicios y controladores.
-   Evitar la creación manual de instancias de clases.

### [!tip] Validación de Datos
-   Utilizar `class-validator` y `class-transformer` junto con `ValidationPipe` para validar automáticamente los datos de entrada de las solicitudes.

### [!tip] Manejo de Errores
-   Implementar filtros de excepciones globales o a nivel de controlador para manejar errores de forma consistente.
-   Reportar errores a [[sentry]] con contexto relevante.

### [!tip] Seguridad
-   Implementar guards para proteger las rutas y asegurar la autenticación y autorización.
-   Validar y sanitizar todas las entradas del usuario para prevenir ataques de inyección.
-   Utilizar [[jwt]] para la autenticación basada en tokens.

## Solución de Problemas Comunes

### [!warning] Problemas de Inyección de Dependencias
-   **Síntoma**: Errores como `Nest can't resolve dependencies of the ...`.
-   **Solución**:
    -   Asegurarse de que los `providers` estén listados en el `module` correcto.
    -   Verificar que los `exports` estén definidos si un `provider` se usa en otro módulo.
    -   Comprobar que no haya dependencias circulares.

### [!warning] Rendimiento Lento de la API
-   **Síntoma**: Las solicitudes a la API tardan mucho en responder.
-   **Solución**:
    -   Optimizar consultas a la base de datos (índices, evitar N+1).
    -   Implementar caching (ej. con Redis).
    -   Utilizar interceptors para medir el tiempo de respuesta y detectar cuellos de botella.
    -   Monitorear con [[sentry]] y [[apm]].

### [!warning] Errores de CORS
-   **Síntoma**: El frontend no puede hacer solicitudes al backend debido a errores de CORS.
-   **Solución**: Configurar CORS en la aplicación NestJS para permitir solicitudes desde el dominio del frontend.

## Glosario de Términos

-   **Módulo**: Unidad organizativa fundamental en NestJS.
-   **Controlador**: Maneja las solicitudes HTTP.
-   **Servicio (Provider)**: Contiene la lógica de negocio.
-   **Inyección de Dependencias**: Patrón para gestionar dependencias.
-   **Decorador**: Función que añade metadatos a clases, métodos o propiedades.
-   **Pipe**: Transforma o valida datos de entrada.
-   **Guard**: Protege rutas con lógica de autorización.
-   **Interceptor**: Permite lógica antes/después de la ejecución de un método.
-   **Filtro de Excepciones**: Maneja errores de forma centralizada.

## Relación con Otros Conceptos del Sistema

- [[nodejs]] - Entorno de ejecución de NestJS.
- [[typescript]] - Lenguaje de programación de NestJS.
- [[base-de-datos-mongodb]] - Base de datos principal.
- [[nextjs]] - Frontend que consume la API de NestJS.
- [[docker]] - Contenerización de la aplicación.
- [[railway]] / [[seenode]] - Plataformas de despliegue.
- [[sentry]] / [[apm]] - Monitoreo de errores y rendimiento.
- [[cloudflare-r2]] - Almacenamiento de objetos.
- [[jwt]] - Autenticación y autorización.
- [[api-rest-especificacion]] - Diseño de la API.
- [[arquitectura-de-microservicios]] - Soporte nativo de NestJS.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*