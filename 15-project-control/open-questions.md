# Preguntas abiertas

> Estado: 🟡 En progreso | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura / Gestión

## Flujo de resolución

1. **Registrar:** cualquier equipo puede agregar una pregunta abierta con estado `ABIERTA`.
2. **Asignar:** el equipo de arquitectura o gestión asigna un responsable y una fecha límite de respuesta.
3. **Resolver:** el responsable responde y cambia el estado a `RESUELTA`.
4. **Escalar si aplica:** si la resolución genera una decisión técnica relevante, crear un ADR en `05-architecture/decisions/records/`. Si afecta requisitos, actualizar `04-requirements/`.
5. **Cerrar:** preguntas resueltas se mantienen en el historial (no eliminar). Mover a sección `## Resueltas` cuando el registro sea largo.

## Formato de registro

| # | Pregunta | Área | Responsable | Fecha límite | Estado | Resolución / ADR |
|---|----------|------|-------------|--------------|--------|------------------|

## Estados válidos

| Estado | Significado |
|--------|-------------|
| `ABIERTA` | Sin respuesta aún |
| `EN REVISIÓN` | Responsable asignado, trabajando en ella |
| `RESUELTA` | Tiene respuesta, puede generar ADR o actualización |
| `CANCELADA` | Ya no aplica (indicar por qué) |

---

## Preguntas abiertas

| # | Pregunta | Área | Responsable | Fecha límite | Estado | Resolución / ADR |
|---|----------|------|-------------|--------------|--------|------------------|
| 1 | ¿Cuál es la fuente maestra autorizada para fichas, aprendices, instructores y programas? | Arquitectura | Por definir | Por definir | ABIERTA | — |
| 2 | ¿La plataforma se integrará con SOFIA Plus, Zajuna, LMS u otros sistemas? ¿Con qué mecanismo? | Arquitectura | Por definir | Por definir | ABIERTA | — |
| 3 | ¿Qué roles institucionales pueden ver información de aprendices? | Seguridad | Por definir | Por definir | ABIERTA | — |
| 4 | ¿Qué datos personales son estrictamente necesarios para el seguimiento? | Seguridad | Por definir | Por definir | ABIERTA | — |
| 5 | ¿Cuál es la política de retención documental para evidencias, reportes y actas? | Gestión | Por definir | Por definir | ABIERTA | — |
| 6 | ¿Qué se considera ejecución real de una sesión: asistencia, evidencia, firma, geolocalización, confirmación instructor u otro? | Dominio | Por definir | Por definir | ABIERTA | — |
| 7 | ¿Qué nivel de granularidad se requiere para avance runtime: ficha, aprendiz, RAP, evidencia, proyecto, sesión? | Dominio | Por definir | Por definir | ABIERTA | — |
| 8 | ¿Los horarios se sincronizan desde una fuente externa o se crean dentro del sistema? | Arquitectura | Por definir | Por definir | ABIERTA | — |
| 9 | ¿Qué estados oficiales debe tener un proyecto formativo? | Dominio | Por definir | Por definir | ABIERTA | — |
| 10 | ¿Cómo se define una dependencia entre proyectos formativos? | Dominio | Por definir | Por definir | ABIERTA | — |
| 11 | ¿Qué reportes PDF son obligatorios y quién los firma? | Gestión | Por definir | Por definir | ABIERTA | — |
| 12 | ¿Qué acciones requieren aprobación humana? | Arquitectura | Por definir | Por definir | ABIERTA | — |
| 13 | ¿Qué ambientes y sedes deben modelarse en la primera versión? | Dominio | Por definir | Por definir | ABIERTA | — |
| 14 | ¿Se requiere operación offline o solo en línea? | Arquitectura | Por definir | Por definir | ABIERTA | — |
| 15 | ¿Qué SLA espera coordinación para carga de horarios, trazas y reportes? | Gestión | Por definir | Por definir | ABIERTA | — |
| 16 | ¿Qué métricas son indicadores oficiales y cuáles son solo analítica interna? | Gestión | Por definir | Por definir | ABIERTA | — |
| 17 | ¿Qué reglas internas SENA no están en documentación pública y deben entregarse como insumo? | Gestión | Por definir | Por definir | ABIERTA | — |

---

## Resueltas

| # | Pregunta | Área | Resolución | ADR / Doc relacionado |
|---|----------|------|------------|-----------------------|