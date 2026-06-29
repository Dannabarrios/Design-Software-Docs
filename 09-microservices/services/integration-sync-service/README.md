# integration-sync-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Sincroniza datos desde fuentes maestras externas (como SOFIA Plus) hacia los servicios internos del sistema, sin reemplazar las fuentes externas.

## Bounded context

Dominio de coordinación e integración. Es dueño del proceso de sincronización y del registro de trabajos. No almacena ni replica la base de datos de SOFIA Plus; transforma y publica eventos para que cada servicio interno actualice su propio estado.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| auth-service | Síncrona (API) | Autenticación y autorización de operaciones administrativas. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos de sincronización para trazabilidad normativa. |
| actor-service | Asíncrona (evento) | Publica eventos de sincronización de instructores y aprendices. |
| cohort-offering-service | Asíncrona (evento) | Publica eventos de sincronización de fichas y grupos. |
| program-catalog-service | Asíncrona (evento) | Publica eventos de sincronización de programas. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
