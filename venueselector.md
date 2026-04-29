---
title: VenueSelector (Componente)
date: 2026-04-27
tags: [react, componente, frontend, ui, ux, venue, ubicacion]
---

# VenueSelector (Componente)

## Definición

**VenueSelector** es un componente de interfaz de usuario (UI) de [[react|React]] que proporciona una forma interactiva y unificada para que los usuarios seleccionen una [[venue|ubicación]] (región, ciudad y [[venue|venue]]) en nuestro sistema de ticketera. Encapsula la lógica de selección y la presentación visual, ofreciendo una experiencia de usuario consistente.

## Responsabilidades Clave

-   **Presentación de UI**: Renderiza los elementos visuales para la selección de región, ciudad y [[venue|venue]] (ej. dropdowns, campos de búsqueda).
-   **Interacción con el Usuario**: Maneja los eventos de usuario (clics, entradas de texto) y los comunica al hook [[usevenueselector|useVenueSelector]].
-   **Visualización de Estado**: Muestra la región, ciudad y [[venue|venue]] seleccionados, así como mensajes de inconsistencia o estados de carga.
-   **Integración con Lógica**: Se conecta al hook [[usevenueselector|useVenueSelector]] para obtener el estado y las funciones de manejo de lógica.

## Interfaz del Componente (Props)

```typescript
interface VenueSelectorProps {
  region: string | undefined;
  ciudad: string | undefined;
  venue: Venue | undefined;
  onRegionChange: (region: string | undefined) => void;
  onCiudadChange: (ciudad: string | undefined) => void;
  onVenueChange: (venue: Venue | undefined) => void;
  venues: Venue[]; // Lista de venues filtrados
  inconsistency: Inconsistency | null; // Información de inconsistencia
  isLoadingVenues: boolean;
  errorLoadingVenues: any;
  // ... otras props para personalización de UI
}

const VenueSelector: React.FC<VenueSelectorProps> = ({ /* ... */ }) => {
  // ... implementación
};
```

## Uso en el Proyecto

El componente `VenueSelector` se utiliza en formularios de creación/edición de [[eventos|eventos]] o en filtros de búsqueda, donde los usuarios necesitan especificar una [[venue|ubicación]].

```typescript
import React from 'react';
import { useVenueSelector } from '../hooks/useVenueSelector';
import { VenueSelector } from '../components/VenueSelector'; // Este componente

const EventCreationPage: React.FC = () => {
  const { region, ciudad, venue, setRegion, setCiudad, setVenue, filteredVenues, inconsistency, isLoadingVenues } = useVenueSelector();

  const handleSave = () => {
    console.log('Evento guardado con ubicación:', { region, ciudad, venue });
    // ... lógica para guardar
  };

  return (
    <div>
      <h1>Crear Nuevo Evento</h1>
      <VenueSelector
        region={region}
        ciudad={ciudad}
        venue={venue}
        onRegionChange={setRegion}
        onCiudadChange={setCiudad}
        onVenueChange={setVenue}
        venues={filteredVenues}
        inconsistency={inconsistency}
        isLoadingVenues={isLoadingVenues}
        errorLoadingVenues={null} // Manejo de errores más sofisticado en la app real
      />
      <button onClick={handleSave}>Guardar</button>
    </div>
  );
};
```

## Relación con Otros Conceptos

- [[react]] - La librería base para el componente.
- [[venue]] - La entidad principal que se selecciona.
- [[usevenueselector]] - El hook que proporciona la lógica al componente.
- [[comunas-chile]] - Datos estáticos utilizados para poblar las opciones de región y ciudad.
- [[nextjs]] - El framework frontend donde se utiliza este componente.
- [[ui-ux-design]] - El componente es una implementación directa del diseño UI/UX.

> [!note] Documento creado siguiendo las mejores prácticas de Obsidian Flavored Markdown
> *Última actualización: 2026-04-27*