---
title: Next.js
date: 2026-04-27
tags: [nextjs, react, frontend, framework, desarrollo, web, ssr, ssg, rsc]
alias: [NextJS, Next.js Framework]
obsidian_ui: true
---

# Next.js

## Definición

**Next.js** es un framework de React de código abierto que permite construir aplicaciones web full-stack con renderizado del lado del servidor (SSR), generación de sitios estáticos (SSG) y renderizado de componentes del servidor (RSC). Es conocido por su enfoque en el rendimiento, la experiencia del desarrollador y la optimización para la producción.

> [!info] Conceptos Clave
> -   **Renderizado del Lado del Servidor (SSR)**: Las páginas se renderizan en el servidor en cada solicitud, lo que mejora el SEO y el tiempo de carga inicial.
> -   **Generación de Sitios Estáticos (SSG)**: Las páginas se pre-renderizan en tiempo de construcción y se sirven como archivos estáticos, ideal para contenido que no cambia frecuentemente.
> -   **Renderizado de Componentes del Servidor (RSC)**: Permite renderizar componentes de React en el servidor, reduciendo el JavaScript enviado al cliente y mejorando el rendimiento.
> -   **Enrutamiento Basado en Archivos**: Las rutas se definen automáticamente por la estructura de archivos en el directorio `app` o `pages`.
> -   **Optimización de Imágenes**: Componente `next/image` para optimización automática de imágenes.
> -   **Optimización de Fuentes**: Componente `next/font` para optimización automática de fuentes.
> -   **API Routes**: Permite crear endpoints de API directamente dentro del proyecto Next.js, facilitando la construcción de aplicaciones full-stack.

## Uso en el Sistema de Ticketera

Next.js es el framework principal para el desarrollo de nuestro frontend. Lo utilizamos para construir la interfaz de usuario de cara al cliente y, en algunos casos, para pequeñas APIs internas a través de sus API Routes.

### Estructura del Proyecto Frontend

Nuestro proyecto frontend se encuentra en `desarrollo/venta-entradas-v2-frontend` y sigue la estructura del App Router de Next.js.

```
venta-entradas-v2-frontend/
├── app/                  # App Router
│   ├── (auth)/           # Grupos de rutas para autenticación
│   │   ├── login/
│   │   └── register/
│   ├── (main)/           # Grupos de rutas principales
│   │   ├── events/
│   │   ├── tickets/
│   │   └── profile/
│   ├── api/              # API Routes
│   │   ├── auth/
│   │   └── webhooks/
│   ├── layout.tsx        # Layouts compartidos
│   └── page.tsx          # Páginas raíz
├── components/           # Componentes reutilizables
├── lib/                  # Utilidades y funciones de ayuda
├── public/               # Archivos estáticos
├── styles/               # Estilos globales y Tailwind
├── next.config.js        # Configuración de Next.js
├── package.json
└── tsconfig.json
```

### Renderizado y Estrategias

-   **Páginas de Eventos y Listados**: Utilizan SSG (`generateStaticParams`, `generateStaticProps` o `getStaticProps` en Pages Router) para un rendimiento óptimo, ya que el contenido no cambia constantemente.
-   **Páginas de Usuario (Perfil, Mis Tickets)**: Utilizan SSR (`getServerSideProps` en Pages Router o Server Components en App Router) para mostrar contenido dinámico y personalizado.
-   **API Routes**: Para manejar la autenticación, webhooks y otras lógicas de backend ligeras que no requieren un servicio NestJS completo.

## Beneficios para el Proyecto

### [!success] Rendimiento y SEO
-   **Tiempos de Carga Rápidos**: Gracias a SSR, SSG y optimizaciones automáticas (imágenes, fuentes).
-   **Mejor SEO**: El contenido pre-renderizado es fácilmente indexable por los motores de búsqueda.
-   **Core Web Vitals**: Facilita el cumplimiento de las métricas de rendimiento de Google.

### [!success] Experiencia de Desarrollador
-   **Desarrollo Rápido**: Hot Module Replacement (HMR) y Fast Refresh para una experiencia de desarrollo fluida.
-   **Enrutamiento Intuitivo**: Basado en la estructura de archivos, simplificando la gestión de rutas.
-   **Ecosistema React**: Aprovecha la vasta comunidad y librerías de React.

### [!success] Escalabilidad y Mantenibilidad
-   **Arquitectura Modular**: Facilita la organización del código y la colaboración en equipos grandes.
-   **Optimización Automática**: Reduce la carga de trabajo manual para optimizar el rendimiento.
-   **Full-Stack Capabilities**: Permite construir APIs ligeras junto al frontend, reduciendo la necesidad de un backend separado para ciertas funcionalidades.

## Integración con Otros Servicios

-   **[[NestJS]]**: Nuestro backend principal, con el que Next.js se comunica a través de [[Integración-con-backend|API RESTful]].
-   **[[Tailwind CSS]]**: Framework de CSS de utilidad para estilizar los componentes de Next.js.
-   **[[Storybook]]**: Para el desarrollo aislado y la documentación de los componentes de UI de Next.js.
-   **[[Sentry]]**: Para monitoreo de errores y rendimiento en el frontend.
-   **[[Cloudflare R2]]**: Para servir activos estáticos y optimizados, a menudo referenciados desde Next.js.
-   **[[Docker]]**: Para contenerizar la aplicación Next.js en desarrollo y producción.
-   **[[Railway]] / [[Seenode]]**: Plataformas de despliegue para la aplicación Next.js.

## Mejores Prácticas de Implementación

### [!tip] Uso del App Router
-   Priorizar el uso del App Router para nuevas funcionalidades, aprovechando Server Components y Server Actions.
-   Entender cuándo usar Server Components (por defecto) y cuándo Client Components (`"use client"`).

### [!tip] Estrategias de Fetching de Datos
-   Utilizar `fetch` nativo en Server Components para fetching de datos en el servidor.
-   Para Client Components, usar librerías como `SWR` o `React Query` para caching y revalidación.

### [!tip] Optimización
-   Siempre usar `next/image` para imágenes y `next/font` para fuentes.
-   Optimizar el tamaño del bundle de JavaScript, usando lazy loading para componentes no críticos.
-   Configurar correctamente el `next.config.js` para optimizaciones específicas.

### [!tip] Manejo de Errores
-   Implementar `error.tsx` para manejar errores a nivel de ruta.
-   Capturar errores en el cliente y servidor con [[Sentry]].

## Solución de Problemas Comunes

### [!warning] Problemas de Hidratación
-   **Síntoma**: Errores de `Mismatching childNodes` o `Text content did not match` en la consola del navegador.
-   **Solución**: Asegurarse de que el HTML renderizado en el servidor sea idéntico al HTML generado en el cliente. Esto a menudo ocurre por diferencias en el estado inicial o por código que se ejecuta solo en el cliente.

### [!warning] Build Lento
-   **Síntoma**: El proceso de `next build` tarda mucho tiempo.
-   **Solución**:
    -   Optimizar el fetching de datos en SSG.
    -   Reducir el tamaño del bundle.
    -   Asegurarse de que no haya bucles infinitos o cálculos pesados en tiempo de construcción.
    -   Utilizar un hardware de construcción más potente o servicios de CI/CD optimizados.

### [!warning] Problemas de SEO con Client Components
-   **Síntoma**: El contenido de los Client Components no aparece en los resultados de búsqueda.
-   **Solución**: Asegurarse de que el contenido crítico para el SEO se renderice en el servidor (SSR o SSG) o que se utilice el App Router con Server Components.

## Glosario de Términos

-   **SSR (Server-Side Rendering)**: Renderizado del lado del servidor.
-   **SSG (Static Site Generation)**: Generación de sitio estático.
-   **RSC (React Server Components)**: Componentes de React que se renderizan en el servidor.
-   **App Router**: Nuevo sistema de enrutamiento de Next.js que permite Server Components.
-   **Pages Router**: Sistema de enrutamiento anterior de Next.js.
-   **Hydration**: Proceso por el cual React "adjunta" el JavaScript a un HTML pre-renderizado.
-   **API Routes**: Funciones de backend que se ejecutan como parte de la aplicación Next.js.

## Relación con Otros Conceptos del Sistema

- [[React]] - La librería base sobre la que se construye Next.js.
- [[NestJS]] - Backend principal del proyecto.
- [[Tailwind CSS]] - Framework de estilos utilizado.
- [[Storybook]] - Para desarrollo y documentación de componentes.
- [[Sentry]] - Monitoreo de errores y rendimiento.
- [[Docker]] - Contenerización de la aplicación.
- [[Railway]] / [[Seenode]] - Plataformas de despliegue.
- [[Integración-con-backend]] - Patrones de comunicación con el backend.
- [[Optimización de Imágenes]] - Uso de `next/image`.
- [[UI/UX Design]] - Implementación de la interfaz de usuario.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*