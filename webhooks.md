---
title: Webhooks
date: 2026-04-27
tags: [webhooks, integracion, api, comunicacion, asincrono, backend]
---

# Webhooks

## Definición

Un **Webhook** es un método para que una aplicación proporcione a otras aplicaciones información en tiempo real. Es un "callback HTTP" definido por el usuario, lo que significa que cuando ocurre un evento específico en una aplicación, esta envía una solicitud HTTP POST a una URL preconfigurada (el endpoint del webhook) en otra aplicación.

A diferencia de las APIs tradicionales donde la aplicación cliente tiene que "preguntar" (polling) al servidor por actualizaciones, con los webhooks el servidor "notifica" a la aplicación cliente cuando algo sucede.

## Cómo Funcionan

1.  **Registro**: La aplicación cliente (nuestro backend [[nestjs]]) registra una URL de webhook en la aplicación de origen (ej. una pasarela de pago).
2.  **Evento**: Cuando ocurre un evento específico en la aplicación de origen (ej. un pago exitoso), esta genera una carga útil (payload) con la información del evento.
3.  **Notificación**: La aplicación de origen envía una solicitud HTTP POST con la carga útil del evento a la URL de webhook registrada en la aplicación cliente.
4.  **Procesamiento**: La aplicación cliente recibe la solicitud POST, procesa la carga útil y realiza las acciones correspondientes (ej. actualizar el estado de una orden, generar un ticket).

## Importancia en el Sistema de Ticketera

Los webhooks son cruciales para la [[integracion-de-sistemas-pago|integración de sistemas de pago]] y otras comunicaciones asíncronas en nuestro sistema:

-   **Confirmación de Pagos**: Las pasarelas de pago nos notifican sobre el estado final de una transacción (éxito, fallo, reembolso), lo que nos permite actualizar el estado de las órdenes y generar [[entradas-e-ticket|tickets]] de forma fiable.
-   **Actualizaciones Asíncronas**: Permiten que nuestro sistema reaccione a eventos externos sin necesidad de polling constante, reduciendo la carga y la latencia.

## Consideraciones de Seguridad

-   **Validación de Firmas**: Verificar la autenticidad de los webhooks recibidos. Las pasarelas de pago suelen incluir una firma en los encabezados de la solicitud que nuestro backend puede verificar utilizando una clave secreta compartida.
-   **HTTPS**: El endpoint del webhook en nuestro backend debe ser HTTPS para proteger la carga útil en tránsito.
-   **Idempotencia**: El endpoint del webhook debe ser idempotente, es decir, procesar la misma notificación varias veces no debe causar efectos secundarios no deseados.
-   **Respuestas Rápidas**: El endpoint del webhook debe responder rápidamente (ej. con un `200 OK`) para evitar reintentos innecesarios por parte del remitente.

## Implementación en el Backend ([[nestjs]])

Nuestro backend [[nestjs]] expondrá endpoints específicos para recibir webhooks.

```typescript
// src/payments/payments.controller.ts
import { Controller, Post, Body, Headers } from '@nestjs/common';
import { PaymentsService } from './payments.service';

@Controller('webhooks/stripe') // Ejemplo para Stripe
export class PaymentsWebhookController {
  constructor(private readonly paymentsService: PaymentsService) {}

  @Post()
  async handleStripeWebhook(
    @Body() payload: any,
    @Headers('stripe-signature') signature: string,
  ) {
    // 1. Verificar la firma del webhook para asegurar su autenticidad
    // this.paymentsService.verifyStripeWebhook(payload, signature);

    // 2. Procesar el evento del webhook
    switch (payload.type) {
      case 'checkout.session.completed':
        await this.paymentsService.handleCheckoutSessionCompleted(payload.data.object);
        break;
      case 'payment_intent.succeeded':
        await this.paymentsService.handlePaymentIntentSucceeded(payload.data.object);
        break;
      // ... otros tipos de eventos
      default:
        console.log(`Unhandled event type ${payload.type}`);
    }

    return { received: true };
  }
}
```

## Relación con Otros Conceptos

- [[integracion-de-sistemas-pago]] - Los webhooks son clave para la confirmación asíncrona de pagos.
- [[nestjs]] - Nuestro backend que implementa los endpoints de webhooks.
- [[http]] - Protocolo subyacente para las notificaciones de webhooks.
- [[seguridad-de-datos]] - La validación de firmas es crucial para la seguridad de los webhooks.

> [!note] Documento creado como placeholder.
> *Última actualización: 2026-04-27*