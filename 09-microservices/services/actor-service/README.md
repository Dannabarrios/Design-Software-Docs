# actor-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Gestiona instructores, aprendices, coordinadores, directivos y sus relaciones institucionales.

## Bounded context

Personas y roles que participan en el proceso formativo. Es dueño de la identidad académica de los actores, no de sus credenciales de acceso (eso es de auth-service).

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| auth-service | Síncrona (API) | Autenticación y autorización. |
| institutional-structure-service | Síncrona (API) | Asocia actores a centros y sedes. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos para auditoría. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
