# API

> Estado: 🟡 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

## Contenido

Define lineamientos de API, autenticación y ubicación de contratos OpenAPI.

## Archivos

| Archivo | Descripción | Estado |
|---------|-------------|--------|
| [guidelines.md](./guidelines.md) | Convenciones de diseño de APIs REST: recursos, versionado, métodos, errores, paginación y correlation_id. | 🟢 |
| [authentication.md](./authentication.md) | Estrategia de autenticación y autorización: auth-service, tokens, roles, mínimo privilegio. | 🟢 |
| [contracts/openapi/](./contracts/openapi/) | Contratos OpenAPI formales por servicio (aún no escritos). | 🟡 |

## Dónde va cada contrato

| Tipo de contrato | Dónde vive | Cuándo se usa |
|-----------------|------------|---------------|
| Contrato de implementación (borrador, en evolución) | `09-microservices/services/<svc>/api-contract.md` | Durante el desarrollo del servicio |
| Contrato OpenAPI publicable (estable, revisado) | `07-api/contracts/openapi/<svc>.yaml` | Cuando el contrato es estable y puede compartirse con consumidores externos |

**Regla:** el contrato en `07-api/contracts/openapi/` es la versión aprobada por arquitectura. Si hay diferencia entre ambos, el de `07-api/` tiene precedencia para consumidores externos.
