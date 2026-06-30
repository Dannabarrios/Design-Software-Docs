# Estrategia de pruebas

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Estrategia de pruebas del sistema de horarios y trazabilidad formativa del SENA. Este repositorio es documental; la estrategia describe cómo se probará el sistema cuando se implemente. Cada microservicio es responsable de validar su propia frontera.

## Principios

- Cada microservicio prueba su propia frontera: ninguna prueba cruza colecciones ni llama internamente a otro servicio sin pasar por su contrato de API.
- Los contratos de API y eventos son la fuente de verdad para las pruebas de integración y contractuales.
- Toda prueba que involucre identidad propaga un `correlation_id` de prueba para trazabilidad.
- Las pruebas de contrato son obligatorias por microservicio (RNF-009).

## Niveles de prueba

### Pruebas unitarias

Verifican la lógica interna de cada microservicio de forma aislada: reglas de negocio, validaciones, transformaciones y cálculos.

- Alcance: lógica de dominio dentro de un servicio, sin dependencias externas reales.
- Aislamiento: las dependencias externas (BD, otros servicios) se simulan.
- Cobertura esperada: todas las reglas de negocio y variantes de entrada relevantes.

### Pruebas de integración

Verifican que cada servicio interactúa correctamente con su base de datos y con los contratos que consume de otros servicios.

- Alcance: un servicio con su colección MongoDB real en ambiente de prueba.
- No se realizan joins ni accesos directos a colecciones de otros servicios.
- Se valida que las referencias a entidades externas (ids planos) son coherentes con lo esperado.

### Pruebas contractuales (RNF-009)

Verifican que el contrato de API de cada microservicio se cumple en ambos lados: el servicio que lo publica y el servicio que lo consume.

- Cada microservicio tiene pruebas contractuales para sus endpoints REST.
- Los contratos se especifican en OpenAPI y se ubican en `07-api/contracts/openapi/` (RNF-008).
- Las pruebas validan: estructura de respuesta, códigos de estado, formato de errores y propagación de `correlation_id`.
- Un cambio en el contrato de un servicio requiere actualizar las pruebas contractuales de todos sus consumidores antes de integrarse.

### Pruebas de contratos AsyncAPI (RNF-008)

Verifican los eventos de dominio publicados y consumidos entre servicios.

- Cada evento tiene un esquema definido en AsyncAPI.
- Las pruebas validan que el evento publicado cumple el esquema: campos obligatorios (`event_id`, `event_type`, `occurred_at`, `source`, `correlation_id`, `data`), tipos y estructura.
- Los consumidores de eventos tienen pruebas que verifican el comportamiento esperado ante cada evento recibido.

### Pruebas end-to-end

Verifican flujos completos del sistema a través de múltiples microservicios, desde la acción del actor hasta el efecto final observable.

- Alcance: flujos de negocio críticos (ej: programar un horario → ejecutar una sesión → registrar asistencia → actualizar avance del aprendiz).
- Se ejecutan sobre un ambiente integrado con todos los servicios activos.
- No reemplazan las pruebas contractuales; las complementan validando la orquestación completa.

## Resumen por nivel

| Nivel | Alcance | Obligatorio |
|-------|---------|-------------|
| Unitarias | Lógica interna de un servicio | Sí |
| Integración | Servicio + colección MongoDB | Sí |
| Contractuales REST (RNF-009) | Contrato OpenAPI por servicio | Sí |
| Contractuales AsyncAPI (RNF-008) | Eventos de dominio publicados/consumidos | Sí |
| End-to-end | Flujos completos multi-servicio | Sí (flujos críticos) |

## Validación de eventos de dominio

Los eventos de dominio definidos en [`09-microservices/communication-patterns.md`](../09-microservices/communication-patterns.md) deben validarse con pruebas de contrato AsyncAPI antes de considerarse estables. Un evento sin prueba de contrato no puede usarse como dependencia de otro servicio.
