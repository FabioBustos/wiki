---
title: COMUNAS_CHILE (Datos Estáticos)
date: 2026-04-27
tags: [chile, comunas, regiones, datos-estaticos, ubicacion]
alias: [Comunas de Chile, Regiones de Chile]
---

# COMUNAS_CHILE (Datos Estáticos)

## Definición

**COMUNAS_CHILE** se refiere a un conjunto de datos estáticos que contiene la información geográfica y administrativa de las regiones y comunas (ciudades) de Chile. Estos datos son fundamentales para la funcionalidad de selección de [[venue|ubicación]] en nuestro sistema de ticketera, permitiendo a los usuarios filtrar eventos por región y ciudad.

## Estructura de Datos

El conjunto de datos se organiza típicamente en dos estructuras principales:

1.  **`REGIONES_CHILE`**: Un array de strings que lista todas las regiones administrativas de Chile.
2.  **`CIUDADES_POR_REGION`**: Un objeto (o mapa) donde las claves son los nombres de las regiones y los valores son arrays de strings con las comunas (ciudades) que pertenecen a esa región.

### Ejemplo de Estructura

```typescript
// COMUNAS_CHILE.ts
export const REGIONES_CHILE = [
  'Arica y Parinacota',
  'Tarapacá',
  'Antofagasta',
  'Atacama',
  'Coquimbo',
  'Valparaíso',
  'Metropolitana',
  'O\'Higgins',
  'Maule',
  'Ñuble',
  'Biobío',
  'La Araucanía',
  'Los Ríos',
  'Los Lagos',
  'Aysén',
  'Magallanes',
] as const;

export type Region = typeof REGIONES_CHILE[number];

export const CIUDADES_POR_REGION: Record<Region, string[]> = {
  'Metropolitana': ['Santiago', 'Providencia', 'Las Condes', 'Ñuñoa', 'Maipú', 'La Florida', /* ... */],
  'Valparaíso': ['Valparaíso', 'Viña del Mar', 'Reñaca', 'Concón', 'Quilpué', /* ... */],
  // ... otras regiones
};
```

## Importancia en el Proyecto

Estos datos estáticos son críticos para la funcionalidad de [[venue|selección de ubicación]] en el frontend [[nextjs]]:

-   **Filtrado de Eventos**: Permite a los usuarios buscar eventos por región y ciudad.
-   **Creación de Eventos**: Los organizadores pueden seleccionar la región y ciudad de un [[venue|venue]] de forma estandarizada.
-   **Consistencia de Datos**: Asegura que los nombres de regiones y ciudades sean consistentes en toda la aplicación.
-   **Derivación Automática**: Facilita la derivación automática de la región cuando se selecciona una ciudad, o viceversa.

## Uso en el Frontend

El componente [[venueselector|VenueSelector]] y el hook [[usevenueselector|useVenueSelector]] utilizan estos datos para poblar los dropdowns de selección de región y ciudad, y para realizar validaciones y derivaciones.

## Relación con Otros Conceptos

- [[venue]] - La entidad de ubicación que utiliza estos datos.
- [[usevenueselector]] - Hook que consume estos datos.
- [[venueselector]] - Componente UI que utiliza estos datos.
- [[nextjs]] - Frontend donde se utilizan estos datos.
- [[eventos]] - Los eventos se filtran por estas ubicaciones.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*