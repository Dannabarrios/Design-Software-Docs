# notification-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Gestiona el envío de mensajes, alertas, recordatorios y eventos de seguimiento a usuarios del sistema.

## Bounded context

Dominio de comunicaciones transversales. Es dueño de las notificaciones y sus plantillas. No genera los eventos que disparan las notificaciones (otros servicios los producen); solo los recibe y decide cómo y cuándo comunicarlos según plantilla y canal.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| auth-service | Síncrona (API) | Autenticación, autorización y resolución de datos del usuario destinatario. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos de envío para trazabilidad. |
| schedule-service | Asíncrona (evento) | Consume eventos de cambio de horario para notificar afectados. |
| attendance-trace-service | Asíncrona (evento) | Consume eventos de inasistencia para enviar alertas. |
| learner-progress-service | Asíncrona (evento) | Consume alertas de riesgo de aprendices para notificar coordinadores. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
