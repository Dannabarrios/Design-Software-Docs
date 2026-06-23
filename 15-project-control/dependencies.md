# Dependencias

> Estado: 🟡 En progreso | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura / Gestión

Dependencias internas (entre secciones y servicios) y externas (sistemas y normativa).

## Dependencias internas

| Origen | Depende de | Motivo |
|--------|------------|--------|
| 09-microservices | 05-architecture/decisions (ADR-001) | No se crean servicios sin la decisión de arquitectura aprobada. |
| 04-requirements/traceability-matrix | 09-microservices | La matriz relaciona cada requisito con su servicio y prueba. |
| 06-data | 09-microservices | Cada servicio define su propio modelo de datos. |

## Dependencias externas

| Dependencia | Tipo | Estado |
|-------------|------|--------|
| SOFIA Plus | Fuente maestra / integración | Por confirmar (ver open-questions Q-02) |
| Fuentes maestras de fichas, aprendices, instructores | Integración / sincronización | Por confirmar (ver open-questions Q-01) |

> Nota: las dependencias entre microservicios se completarán cuando el catálogo de servicios esté definido.