# Observabilidad

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Estrategia de observabilidad del sistema de horarios y trazabilidad formativa del SENA. Aplica a los 16 microservicios y cubre los tres pilares requeridos por RNF-005: logs, métricas y trazas distribuidas.

## Principios

- Todo evento observable lleva `correlation_id` para permitir reconstruir el flujo completo a través de servicios (RNF-004).
- Cada microservicio es responsable de emitir sus propios logs, métricas y trazas; no existe un servicio centralizado que los genere.
- La observabilidad se diseña para detectar problemas antes de que el usuario los reporte.

## Logs estructurados

Todos los servicios emiten logs en formato estructurado (clave-valor o JSON). Cada línea de log incluye como mínimo:

| Campo | Descripción |
|-------|-------------|
| `timestamp` | Momento del evento en ISO 8601. |
| `level` | Nivel del log: `INFO`, `WARN`, `ERROR`. |
| `service` | Nombre del microservicio que emite el log. |
| `correlation_id` | Identificador de trazabilidad de la solicitud (RNF-004). |
| `message` | Descripción legible del evento. |
| `context` | Datos adicionales relevantes (recurso afectado, operación, etc.). |

Los logs de error incluyen el tipo de error y, cuando aplica, el identificador del recurso afectado. Nunca se registran credenciales, tokens ni datos personales sensibles en logs.

## Métricas

Cada servicio expone métricas operativas para monitorear su salud y comportamiento:

| Métrica | Descripción |
|---------|-------------|
| Disponibilidad | Porcentaje de tiempo en que el servicio responde correctamente. |
| Latencia | Tiempo de respuesta por endpoint (percentiles p50, p95, p99). |
| Tasa de errores | Proporción de respuestas 4xx y 5xx sobre el total de solicitudes. |
| Eventos publicados | Cantidad de eventos de dominio publicados y pendientes de entrega. |
| Eventos no entregados | Eventos que fallaron en la entrega después de los reintentos configurados. |

Los SLA de disponibilidad y latencia no están definidos aún. Ver [`15-project-control/open-questions.md`](../15-project-control/open-questions.md) Q-15.

## Trazas distribuidas

Las trazas conectan las llamadas entre servicios para un mismo flujo de negocio. El `correlation_id` propagado en el encabezado `X-Correlation-ID` de cada solicitud REST y en cada evento de dominio es el identificador de traza.

- Ante un incidente, el `correlation_id` permite filtrar todos los logs y eventos asociados a una operación específica a través de múltiples servicios.
- Los servicios propagan el `correlation_id` tanto en llamadas síncronas (REST) como en eventos asíncronos publicados.

## Healthchecks

Cada microservicio expone un endpoint de salud:

```
GET /health
```

El endpoint devuelve el estado operativo del servicio: disponible, degradado o fuera de servicio. El sistema de monitoreo consulta este endpoint periódicamente para detectar servicios caídos o con problemas de conectividad a MongoDB.

## Qué se monitorea

| Dimensión | Qué se observa |
|-----------|----------------|
| Disponibilidad | Resultado del `GET /health` por servicio. |
| Latencia | Tiempo de respuesta de endpoints críticos (horarios, asistencia, avance). |
| Errores | Tasa de 5xx por servicio; errores de conexión a MongoDB. |
| Eventos | Eventos no entregados o acumulados en la cola sin procesar. |
| Auditoría | Acciones sensibles registradas en `audit-compliance-service` (RNF-002). |
