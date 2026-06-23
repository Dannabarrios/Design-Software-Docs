# parameter-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Gestiona catálogos base, reglas configurables, calendarios institucionales y tipos.

## Bounded context

Parametrización transversal del sistema. Es dueño de los catálogos y reglas que otros servicios consumen, sin contener lógica de dominio de esos servicios.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| auth-service | Síncrona (API) | Autenticación y autorización. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos para auditoría. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
