# auth-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Gestiona identidad, autenticación, autorización, roles y permisos de todos los usuarios del sistema.

## Bounded context

Dominio de seguridad transversal del SENA. Es dueño de las credenciales, sesiones y el modelo de roles y permisos. Todos los demás servicios delegan en auth-service para validar acceso. No gestiona datos académicos ni operativos.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| audit-compliance-service | Asíncrona (evento) | Publica eventos de autenticación y cambios de permisos para trazabilidad. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
