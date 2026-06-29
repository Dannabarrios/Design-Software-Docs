# api-contract — audit-compliance-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| POST | /audit-logs | Inserta un nuevo registro de auditoría (solo inserción). |
| GET | /audit-logs | Consulta registros de auditoría con filtros (fecha, usuario, recurso). |
| GET | /audit-logs/{id} | Consulta un registro de auditoría por su identificador. |
| GET | /retention-policies | Lista las políticas de retención vigentes. |
| POST | /retention-policies | Crea una política de retención. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
- Los registros de auditoría son inmutables: no existen endpoints PUT, PATCH ni DELETE sobre `audit-logs`.
- La política de retención determina el período mínimo de conservación antes de cualquier purga autorizada.
