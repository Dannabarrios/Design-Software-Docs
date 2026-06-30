# Gestión de incidentes

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Lineamientos para detectar, diagnosticar, resolver y registrar incidentes en el sistema. El `correlation_id` es la herramienta principal para rastrear un incidente a través de múltiples servicios (RNF-004). Todo incidente con impacto en datos sensibles o acciones de sistema se registra en `audit-compliance-service` (RNF-002).

## Clasificación de severidades

| Severidad | Descripción | Ejemplo |
|-----------|-------------|---------|
| **S1 — Crítico** | El sistema o un servicio P0 está completamente caído. Impacto directo en la operación formativa. | `schedule-service` o `auth-service` no responden. |
| **S2 — Alto** | Una funcionalidad principal está degradada o con errores frecuentes. | Asistencia no se puede registrar; evidencias no se entregan. |
| **S3 — Medio** | Una funcionalidad secundaria falla o hay degradación de rendimiento notable. | Reportes PDF no se generan; notificaciones no llegan. |
| **S4 — Bajo** | Error puntual, cosmético o con baja frecuencia. No bloquea operación. | Un endpoint retorna un mensaje de error incorrecto. |

## Flujo de gestión

### 1. Detección

El incidente se detecta por alguno de estos canales:

- Alerta automática del sistema de monitoreo (healthcheck fallido, tasa de errores elevada, eventos no entregados).
- Reporte de un usuario o actor del sistema.
- Revisión proactiva de logs o métricas.

### 2. Diagnóstico

Una vez detectado el incidente:

1. Obtener el `correlation_id` de la solicitud o evento fallido.
2. Filtrar todos los logs del sistema usando ese `correlation_id` para reconstruir el flujo completo.
3. Identificar en qué servicio se originó el fallo: revisar el `GET /health` de cada servicio afectado.
4. Consultar el runbook del servicio correspondiente en `09-microservices/services/<servicio>/runbook.md` para diagnosticar fallos comunes.

### 3. Resolución

- Aplicar la acción correctiva indicada en el runbook del servicio afectado.
- Si el fallo no está cubierto en el runbook, escalar al equipo de arquitectura.
- Verificar que el servicio recuperado responde correctamente en `GET /health`.
- Confirmar que los eventos pendientes se reprocessan o se marcan adecuadamente.

### 4. Registro y cierre

- Registrar el incidente, su causa raíz, la acción tomada y el tiempo de resolución.
- Si el incidente involucró acciones sobre datos sensibles o errores de autorización, verificar que `audit-compliance-service` registró los eventos correspondientes (RNF-002).
- Actualizar el runbook del servicio afectado si se identificó un nuevo patrón de fallo no documentado.

## Runbooks por servicio

Cada microservicio tiene su propio runbook con los fallos comunes y acciones recomendadas:

| Ruta | Servicios cubiertos |
|------|-------------------|
| `09-microservices/services/<servicio>/runbook.md` | Los 16 microservicios del sistema. |

Los runbooks son el primer punto de consulta ante cualquier incidente. Ante un S1 o S2, el diagnóstico comienza siempre por el runbook del servicio afectado y por los logs filtrados por `correlation_id`.

## Registro en auditoría

`audit-compliance-service` mantiene un registro append-only de acciones sensibles del sistema (RNF-002). Durante la gestión de un incidente:

- Cualquier acción correctiva manual sobre datos debe quedar registrada en auditoría.
- Los intentos de acceso no autorizados detectados durante el incidente se registran como eventos de seguridad.
- El registro de auditoría no puede modificarse ni eliminarse; es inmutable.
