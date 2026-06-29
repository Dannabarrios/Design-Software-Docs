# data-model — audit-compliance-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios. La tabla de auditoría es append-only: no se ejecutan UPDATE ni DELETE sobre registros existentes.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| RegistroAuditoria | Evento inmutable que captura quién hizo qué, sobre qué recurso y cuándo. |
| PoliticaRetencion | Define el período mínimo de conservación de registros por tipo de evento. |

## Relaciones

- Una `PoliticaRetencion` aplica a uno o más tipos de `RegistroAuditoria`.
- Los `RegistroAuditoria` no tienen relaciones con entidades de otros servicios; referencias externas se almacenan como atributos planos (id, tipo).
