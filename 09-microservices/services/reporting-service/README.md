# reporting-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Genera indicadores, tableros, exportables en PDF, reportes de avance de fichas y trazabilidad ejecutiva del sistema formativo.

## Bounded context

Dominio de inteligencia operativa. Es dueño de los reportes, indicadores y tableros que consolidan información del sistema. No genera ni modifica datos operativos; los consolida desde los servicios de dominio mediante eventos y consultas autorizadas.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| auth-service | Síncrona (API) | Autenticación y autorización de acceso a reportes. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos de generación de reportes para trazabilidad. |
| learner-progress-service | Asíncrona (evento) | Consume datos de avance de aprendices para indicadores de progreso. |
| attendance-trace-service | Asíncrona (evento) | Consume datos de asistencia para reportes de ejecución. |
| schedule-service | Asíncrona (evento) | Consume datos de sesiones para reportes de horarios. |
| cohort-offering-service | Asíncrona (evento) | Consume datos de fichas para reportes de oferta formativa. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
