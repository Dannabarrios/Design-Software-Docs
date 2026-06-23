# attendance-trace-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Registra asistencia, ejecución real de sesiones, novedades e incidencias en tiempo de ejecución.

## Bounded context

Ejecución real de la formación. Es dueño de lo que efectivamente ocurrió en cada sesión. Lo programado es de schedule-service.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| schedule-service | Síncrona (API) | Referencia la sesión programada. |
| actor-service | Síncrona (API) | Referencia instructores y aprendices. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos para auditoría. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
