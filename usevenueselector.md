---
title: useVenueSelector (Hook)
date: 2026-04-27
tags: [react, hook, frontend, venue, ubicacion, logica]
---

# useVenueSelector (Hook)

## Definición

`useVenueSelector` es un hook personalizado de [[react|React]] diseñado para encapsular la lógica de selección de [[venue|ubicación]] (región, ciudad, [[venue|venue]]) en nuestro sistema de ticketera. Proporciona un estado centralizado y funciones para manejar la cascada bidireccional de selecciones, la detección de inconsistencias y la interacción con la API de [[venue|venues]].

## Responsabilidades Clave

-   **Manejo de Estado**: Gestiona el estado de la región seleccionada, la ciudad seleccionada y el [[venue|venue]] seleccionado.
-   **Lógica de Cascada Bidireccional**:
    -   Cuando se selecciona una región, limpia la ciudad y el [[venue|venue]].
    -   Cuando se selecciona una ciudad, deriva la región y limpia el [[venue|venue]].
    -   Cuando se selecciona un [[venue|venue]], deriva la región y la ciudad.
-   **Detección de Inconsistencias**: Identifica si la región/ciudad seleccionada no coincide con la ubicación del [[venue|venue]] elegido.
-   **Filtrado de [[venue|Venues]]**: Filtra la lista de [[venue|venues]] disponibles basándose en la región y ciudad seleccionadas.
-   **Interacción con API**: Proporciona funciones para cargar [[venue|venues]] desde el backend.

## Interfaz del Hook

```typescript
interface UseVenueSelectorProps {
  initialRegion?: string;
  initialCiudad?: string;
  initialVenueId?: string;
  onRegionChange?: (region: string | undefined) => void;
  onCiudadChange?: (ciudad: string | undefined) => void;
  onVenueChange?: (venue: Venue | undefined) => void;
}

interface UseVenueSelectorReturn {
  region: string | undefined;
  ciudad: string | undefined;
  venue: Venue | undefined;
  filteredVenues: Venue[];
  inconsistency: Inconsistency | null;
  setRegion: (region: string | undefined) => void;
  setCiudad: (ciudad: string | undefined) => void;
  setVenue: (venue: Venue | undefined) => void;
  applyVenueLocation: () => void; // Resuelve inconsistencia usando ubicación del venue
  clearVenue: () => void;
  isLoadingVenues: boolean;
  errorLoadingVenues: any;
  // ... otras propiedades y métodos
}

function useVenueSelector(props?: UseVenueSelectorProps): UseVenueSelectorReturn;
```

## Uso en el Proyecto

El hook `useVenueSelector` es utilizado por el componente [[venueselector|VenueSelector]] para proporcionar la lógica subyacente de la interfaz de selección de ubicación.

```typescript
import React from 'react';
import { useVenueSelector } from './useVenueSelector';
import { VenueSelectorUI } from './VenueSelectorUI'; // Componente UI

const MyEventForm: React.FC = () => {
  const { region, ciudad, venue, setRegion, setCiudad, setVenue, filteredVenues, inconsistency } = useVenueSelector();

  const handleSubmit = () => {
    console.log({ region, ciudad, venue });
    // ... enviar datos
  };

  return (
    <div>
      <VenueSelectorUI
        region={region}
        ciudad={ciudad}
        venue={venue}
        onRegionChange={setRegion}
        onCiudadChange={setCiudad}
        onVenueChange={setVenue}
        venues={filteredVenues}
        inconsistency={inconsistency}
      />
      <button onClick={handleSubmit}>Guardar Evento</button>
    </div>
  );
};
```

## Relación con Otros Conceptos

- [[react]] - La librería base para el hook.
- [[venue]] - La entidad principal que se selecciona.
- [[venueselector]] - El componente UI que utiliza este hook.
- [[comunas-chile]] - Datos estáticos utilizados para la derivación de región/ciudad.
- [[nextjs]] - El framework frontend donde se utiliza este hook.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*