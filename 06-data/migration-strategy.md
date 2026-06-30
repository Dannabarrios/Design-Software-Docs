# Estrategia de migración de datos

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

## Principio general

El sistema no tiene acceso a SOFIA Plus ni replica sus datos (ADR-0002, [`01-context/scope.md`](../01-context/scope.md)). No existe migración de datos desde fuentes externas: todos los datos del sistema son generados y gestionados internamente a través de los microservicios. No se importan datos maestros de ninguna fuente institucional externa.

## Datos del sistema

Todos los datos son creados, actualizados y eliminados directamente en el sistema a través de los contratos de cada microservicio. No hay proceso de carga inicial desde sistemas externos ni sincronización automática con fuentes maestras. Los actores autorizados ingresan la información a través de las interfaces del sistema.

## Versionado de esquemas

La base de datos MongoDB única del sistema aplica la siguiente estrategia de versionado por colección:

- Los esquemas se validan con `$jsonSchema` en cada colección desde el inicio.
- Los cambios de esquema son aditivos siempre que sea posible: se agregan campos opcionales antes de renombrar o eliminar.
- Los cambios disruptivos (renombrado, eliminación, cambio de tipo obligatorio) requieren un script de migración versionado, ejecutado y validado en ambiente de desarrollo antes de aplicarse.
- Cada microservicio es responsable de los scripts de migración de sus propias colecciones.
- No existe un proceso de migración global del sistema; las migraciones son por dominio e independientes entre sí.

## Preguntas abiertas con impacto en datos

Las siguientes preguntas de [`15-project-control/open-questions.md`](../15-project-control/open-questions.md) pueden afectar decisiones futuras sobre el modelo de datos:

| # | Pregunta | Área | Estado |
|---|----------|------|--------|
| Q-05 | ¿Cuál es la política de retención documental para evidencias, reportes y actas? | Gestión | ABIERTA |
| Q-08 | ¿Los horarios se sincronizan desde una fuente externa o se crean dentro del sistema? | Arquitectura | ABIERTA |
