# institutional-structure-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Gestiona regionales, centros de formación, sedes, ambientes y ubicaciones de la estructura institucional.

## Bounded context

Estructura organizativa física e institucional del SENA. Es dueño de la jerarquía territorial (regional, centro, sede) y de los ambientes. No gestiona inventario operativo ni reservas.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| parameter-service | Síncrona (API) | Consume catálogos y tipos institucionales. |
| auth-service | Síncrona (API) | Autenticación y autorización. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos para auditoría. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
