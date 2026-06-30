# Lineamientos de API

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Lineamientos de diseño de APIs REST del sistema. Todos los microservicios deben seguir estas convenciones para garantizar consistencia, trazabilidad y validación de contratos (RNF-004, RNF-008).

## Convenciones de recursos

- Los nombres de recursos van en **plural y lowercase**: `/programs`, `/schedules`, `/learners`.
- Separador de palabras: **kebab-case**: `/formative-projects`, `/attendance-traces`.
- Las rutas de recursos anidados expresan la jerarquía del dominio: `/programs/{id}/competencies`, `/competencies/{id}/raps`.
- No usar verbos en las rutas; la acción la expresa el método HTTP.

## Versionado

- Todas las APIs incluyen la versión en la ruta base: `/v1/programs`, `/v1/schedules`.
- Un cambio de contrato que rompa compatibilidad requiere una nueva versión mayor (`/v2/`).
- Las versiones anteriores se mantienen activas el tiempo necesario para que los consumidores migren.

## Métodos HTTP y semántica

| Método | Semántica | Idempotente |
|--------|-----------|-------------|
| GET | Lectura de recurso o colección. | Sí |
| POST | Creación de un recurso nuevo. | No |
| PUT | Reemplazo completo de un recurso existente. | Sí |
| PATCH | Actualización parcial de un recurso. | No necesariamente |
| DELETE | Eliminación de un recurso. | Sí |

## Códigos de estado HTTP

| Código | Situación |
|--------|-----------|
| 200 OK | Operación exitosa con cuerpo de respuesta. |
| 201 Created | Recurso creado exitosamente. |
| 204 No Content | Operación exitosa sin cuerpo de respuesta (ej. DELETE). |
| 400 Bad Request | Solicitud malformada o con datos inválidos. |
| 401 Unauthorized | Token ausente o inválido. |
| 403 Forbidden | Token válido pero sin permiso suficiente. |
| 404 Not Found | Recurso no encontrado. |
| 409 Conflict | Conflicto de estado (ej. recurso duplicado). |
| 422 Unprocessable Entity | Datos estructuralmente válidos pero que violan reglas de negocio. |
| 500 Internal Server Error | Error interno no controlado. |

## Formato de error estándar

Todos los errores devuelven un cuerpo JSON con la siguiente estructura:

```json
{
  "error": {
    "code": "RESOURCE_NOT_FOUND",
    "message": "El recurso solicitado no existe.",
    "correlation_id": "uuid-de-la-solicitud",
    "timestamp": "2026-06-22T10:00:00Z"
  }
}
```

- `code`: identificador de máquina del tipo de error (uppercase, snake_case).
- `message`: descripción legible del error.
- `correlation_id`: identificador de trazabilidad de la solicitud (ver RNF-004).
- `timestamp`: momento en que ocurrió el error (ISO 8601).

## Paginación

Las colecciones devuelven resultados paginados. Parámetros estándar de query:

| Parámetro | Descripción | Valor por defecto |
|-----------|-------------|-------------------|
| `page` | Número de página (base 1). | 1 |
| `page_size` | Cantidad de resultados por página. | 20 |

La respuesta incluye metadatos de paginación:

```json
{
  "data": [...],
  "pagination": {
    "page": 1,
    "page_size": 20,
    "total": 150,
    "total_pages": 8
  }
}
```

## Correlation ID (RNF-004)

Toda solicitud debe propagar un `correlation_id` para permitir la trazabilidad distribuida entre servicios. Las reglas son:

- El cliente incluye el `correlation_id` en el encabezado HTTP `X-Correlation-ID`.
- Si el cliente no lo envía, el gateway o el servicio receptor lo genera automáticamente.
- El servicio lo propaga en todas las llamadas a servicios dependientes y en los eventos que publique.
- El `correlation_id` aparece en los logs, en el cuerpo de error y en los eventos de dominio.

## Contratos OpenAPI (RNF-008)

Los contratos formales de cada servicio se especifican en formato OpenAPI y se ubican en [`07-api/contracts/openapi/`](./contracts/openapi/). El contrato en esa carpeta es la versión aprobada por arquitectura y tiene precedencia para consumidores externos sobre los borradores en `09-microservices/services/<servicio>/api-contract.md`.
