---
title: Amazon S3
date: 2026-04-27
tags: [aws, s3, almacenamiento, objetos, cloud, infraestructura]
alias: [AWS S3, Amazon Simple Storage Service]
---

# Amazon S3

## Definición

**Amazon S3** (Amazon Simple Storage Service) es un servicio de almacenamiento de objetos altamente escalable, duradero y disponible ofrecido por Amazon Web Services (AWS). Es uno de los servicios de almacenamiento en la nube más populares y se utiliza para almacenar y recuperar cualquier cantidad de datos desde cualquier lugar de la web.

## Conceptos Clave

-   **[[bucket|Bucket]]**: El contenedor fundamental para los [[objeto|objetos]] almacenados en S3. Los nombres de los buckets deben ser únicos globalmente.
-   **[[objeto|Objeto]]**: La unidad básica de almacenamiento en S3. Un objeto es un archivo y sus [[metadata|metadatos]] asociados.
-   **[[clave-key|Clave (Key)]]**: El identificador único de un [[objeto|objeto]] dentro de un [[bucket|bucket]].
-   **[[prefix|Prefijo]]**: Una cadena de caracteres al principio de la [[clave-key|clave]] de un [[objeto|objeto]] que simula una estructura de carpetas.
-   **[[versioning|Versionamiento]]**: Permite mantener múltiples versiones de un [[objeto|objeto]] en el mismo [[bucket|bucket]].
-   **[[politica-de-ciclo-de-vida|Políticas de Ciclo de Vida]]**: Reglas para automatizar la gestión de [[objeto|objetos]] a lo largo del tiempo (ej. mover a almacenamiento de archivo, eliminar).
-   **[[multipart-upload|Multipart Upload]]**: Permite subir [[objeto|objetos]] grandes dividiéndolos en partes.

## Características Principales

-   **Escalabilidad**: S3 puede almacenar una cantidad ilimitada de datos.
-   **Durabilidad**: Diseñado para una durabilidad del 99.999999999% (once nueves) de los [[objeto|objetos]].
-   **Disponibilidad**: Ofrece alta disponibilidad.
-   **Seguridad**: Control de acceso granular, cifrado en reposo y en tránsito.
-   **Clases de Almacenamiento**: Diferentes clases de almacenamiento para optimizar costos y rendimiento (ej. S3 Standard, S3 Intelligent-Tiering, S3 Glacier).
-   **Compatibilidad con API S3**: La API de S3 se ha convertido en un estándar de facto para el almacenamiento de objetos.

## Comparación con [[cloudflare-r2]]

Aunque nuestro proyecto utiliza [[cloudflare-r2]] como servicio principal de almacenamiento de objetos, es importante entender Amazon S3 debido a su posición como estándar de la industria y porque [[cloudflare-r2]] es compatible con su API.

La principal diferencia para nuestro proyecto es el modelo de precios:
-   **Amazon S3**: Cobra por almacenamiento, operaciones y, significativamente, por la [[egress|salida de datos]].
-   **[[cloudflare-r2]]**: Cobra por almacenamiento y operaciones, pero **no cobra por la [[egress|salida de datos]]**, lo que lo hace más económico para aplicaciones con alto tráfico de lectura.

## Uso en el Proyecto (Indirecto)

Aunque no usamos S3 directamente, la compatibilidad de [[cloudflare-r2]] con la API de S3 nos permite utilizar el [[sdk-de-aws|SDK de AWS]] y herramientas diseñadas para S3, lo que simplifica la integración.

## Relación con Otros Conceptos

- [[cloudflare-r2]] - Nuestro servicio de almacenamiento de objetos, compatible con la API de S3.
- [[sdk-de-aws]] - Utilizado para interactuar con servicios compatibles con S3.
- [[egress]] - Un factor de costo clave en S3.
- [[bucket]] - Contenedor de objetos.
- [[objeto]] - Unidad de almacenamiento.
- [[clave-key]] - Identificador de objeto.
- [[prefix]] - Organización de objetos.
- [[versioning]] - Gestión de versiones de objetos.
- [[politica-de-ciclo-de-vida]] - Automatización de la gestión de objetos.
- [[multipart-upload]] - Subida de archivos grandes.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*