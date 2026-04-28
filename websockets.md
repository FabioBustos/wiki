---
title: WebSockets
date: 2026-04-27
tags: [websockets, comunicación, tiempo-real, frontend, backend, red]
alias: [Web Socket]
---

# WebSockets

## Definición

**WebSockets** es un protocolo de comunicación que proporciona un canal de comunicación bidireccional y full-duplex sobre una única conexión TCP. A diferencia de HTTP, que es un protocolo sin estado basado en solicitudes y respuestas, WebSockets permite que tanto el cliente como el servidor envíen mensajes en cualquier momento, lo que lo hace ideal para aplicaciones en tiempo real.

## Cómo Funcionan

1.  **Handshake HTTP**: La conexión WebSocket se inicia con un handshake HTTP estándar. El cliente envía una solicitud HTTP con un encabezado `Upgrade: websocket` y `Connection: Upgrade`.
2.  **Conexión Establecida**: Si el servidor soporta WebSockets, responde con un handshake HTTP exitoso, y la conexión se "actualiza" de HTTP a WebSocket.
3.  **Comunicación Bidireccional**: Una vez establecida la conexión WebSocket, el cliente y el servidor pueden intercambiar mensajes de forma asíncrona y en tiempo real, sin la sobrecarga de los encabezados HTTP en cada mensaje.
4.  **Conexión Persistente**: La conexión WebSocket permanece abierta hasta que el cliente o el servidor la cierran explícitamente.

## Importancia en el Sistema de Ticketera

WebSockets son cruciales para funcionalidades que requieren actualizaciones instantáneas en nuestro sistema de ticketera:

-   **Notificaciones en Tiempo Real**: Notificar a los usuarios sobre cambios en el estado de sus tickets, eventos, o mensajes importantes.
-   **Chat en Vivo**: Si se implementa una funcionalidad de chat para soporte o comunicación entre usuarios/organizadores.
-   **Actualizaciones de Disponibilidad**: Mostrar la disponibilidad de asientos o tickets en tiempo real.
-   **Monitoreo de Eventos en Vivo**: Actualizaciones en vivo sobre el progreso de un evento.

## Implementación en el Proyecto

### Backend ([[nestjs]])

[[nestjs]] tiene un módulo `@nestjs/platform-socket.io` o `@nestjs/websockets` que facilita la implementación de gateways WebSocket.

```typescript
// src/events/events.gateway.ts
import { WebSocketGateway, SubscribeMessage, MessageBody, WebSocketServer } from '@nestjs/websockets';
import { Server } from 'socket.io';

@WebSocketGateway({ cors: true }) // Habilitar CORS para WebSockets
export class EventsGateway {
  @WebSocketServer() server: Server;

  @SubscribeMessage('joinEventRoom')
  handleJoinEventRoom(@MessageBody() data: { eventId: string, userId: string }): void {
    // Lógica para unir al usuario a una sala de evento
    this.server.socketsJoin(`event-${data.eventId}`);
    this.server.to(`event-${data.eventId}`).emit('userJoined', `${data.userId} joined event ${data.eventId}`);
  }

  // Método para emitir eventos a clientes conectados
  sendEventUpdate(eventId: string, update: any) {
    this.server.to(`event-${eventId}`).emit('eventUpdate', update);
  }
}
```

### Frontend ([[nextjs]])

El frontend [[nextjs]] utilizaría una librería cliente de WebSocket (ej. `socket.io-client`) para conectarse al backend.

```typescript
// components/EventLiveUpdates.tsx
import React, { useEffect, useState } from 'react';
import io from 'socket.io-client';

const socket = io('http://localhost:3001'); // URL del backend WebSocket

interface EventLiveUpdatesProps {
  eventId: string;
}

const EventLiveUpdates: React.FC<EventLiveUpdatesProps> = ({ eventId }) => {
  const [updates, setUpdates] = useState<string[]>([]);

  useEffect(() => {
    socket.emit('joinEventRoom', { eventId, userId: 'user123' });

    socket.on('eventUpdate', (data: any) => {
      setUpdates((prev) => [...prev, `Update: ${JSON.stringify(data)}`]);
    });

    socket.on('userJoined', (message: string) => {
      setUpdates((prev) => [...prev, message]);
    });

    return () => {
      socket.off('eventUpdate');
      socket.off('userJoined');
      // socket.disconnect(); // Desconectar si es necesario
    };
  }, [eventId]);

  return (
    <div>
      <h3>Actualizaciones en Vivo para Evento {eventId}</h3>
      <ul>
        {updates.map((update, index) => (
          <li key={index}>{update}</li>
        ))}
      </ul>
    </div>
  );
};

export default EventLiveUpdates;
```

## Relación con Otros Conceptos

- [[integracion-con-backend]] - Un patrón de comunicación entre frontend y backend.
- [[nestjs]] - Framework backend para implementar servidores WebSocket.
- [[nextjs]] - Frontend que consume servicios WebSocket.
- [[http]] - Protocolo utilizado para el handshake inicial.
- [[tiempo-real]] (I will create this file later if it doesn't exist) - Característica principal de las aplicaciones que usan WebSockets.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*