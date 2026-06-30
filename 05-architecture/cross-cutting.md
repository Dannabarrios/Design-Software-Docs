# Aspectos transversales

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Aspectos que aplican a todos los microservicios del sistema, independientemente de su dominio. Cada servicio es responsable de implementarlos en su propio contexto.

## Seguridad

La seguridad sigue el principio de **mínimo privilegio** (RNF-001). `auth-service` es el único responsable de emitir y validar tokens de acceso; ningún otro servicio gestiona credenciales.

- Toda solicitud debe incluir un token de acceso válido en el encabezado `Authorization: Bearer <token>`.
- Los roles agrupan permisos por función institucional; los permisos controlan acciones específicas sobre recursos concretos.
- Un actor solo accede a los recursos que su rol permite. No existe acceso implícito.
- Los servicios validan el token y el permiso requerido antes de ejecutar cualquier operación.

Ver estrategia completa en [`07-api/authentication.md`](../07-api/authentication.md).

## Auditoría

`audit-compliance-service` registra de forma inmutable cada acción sensible del sistema (RNF-002).

- La colección de auditoría es **append-only**: no se ejecutan `UPDATE` ni `DELETE` sobre registros existentes.
- Cada registro incluye: actor, acción, recurso afectado, resultado y timestamp.
- Las políticas de retención definen el período mínimo de conservación por tipo de evento.
- Ningún otro servicio puede eliminar ni modificar registros de auditoría.

## Observabilidad

Todos los servicios implementan los tres pilares de observabilidad (RNF-005):

| Pilar | Descripción |
|-------|-------------|
| **Logs** | Cada servicio emite logs estructurados con nivel (INFO, WARN, ERROR), timestamp, `correlation_id` y contexto de la operación. |
| **Métricas** | Cada servicio expone métricas de salud, latencia, tasa de errores y uso de recursos. |
| **Trazas distribuidas** | Las trazas conectan llamadas entre servicios usando el `correlation_id` propagado en cada request y evento. |

## Correlation ID (RNF-004)

El `correlation_id` es obligatorio en todas las operaciones del sistema. Permite reconstruir el flujo completo de una solicitud a través de múltiples servicios.

- El cliente lo envía en el encabezado `X-Correlation-ID`.
- Si el cliente no lo incluye, el receptor lo genera automáticamente.
- Cada servicio lo propaga en todas sus llamadas salientes (síncronas y asíncronas).
- Aparece en logs, cuerpos de error y eventos de dominio publicados.

## Manejo de errores

Todos los servicios devuelven errores en un formato JSON estándar:

```json
{
  "error": {
    "code": "CODIGO_MAQUINA",
    "message": "Descripción legible del error.",
    "correlation_id": "uuid-del-request",
    "timestamp": "2026-06-22T10:00:00Z"
  }
}
```

- Los errores de cliente usan códigos 4xx; los errores internos usan 5xx.
- Los errores de negocio se expresan con `422 Unprocessable Entity` y un `code` descriptivo.
- Nunca se exponen detalles internos de implementación (stack traces, nombres de colecciones) en las respuestas de error.

## Protección de datos personales

El sistema maneja datos personales de aprendices e instructores y debe cumplir la Ley 1581 de 2012 (RNF-006).

- Solo se recolectan los datos estrictamente necesarios para la operación formativa.
- El acceso a datos personales está restringido por rol y por el principio de mínimo privilegio.
- `audit-compliance-service` registra toda operación sobre datos personales sensibles.
- Las políticas de retención y eliminación de datos personales se definen en `audit-compliance-service`.
- La pregunta Q-04 de [`15-project-control/open-questions.md`](../15-project-control/open-questions.md) (qué datos personales son estrictamente necesarios) está abierta y debe resolverse antes de la implementación.
