# data-model — parameter-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| Catalogo | Conjunto de valores base reutilizables. |
| Parametro | Valor configurable del sistema. |
| Regla | Regla configurable aplicable por otros servicios. |
| CalendarioInstitucional | Calendario con fechas institucionales. |
| Tipo | Tipificación reutilizable. |

## Relaciones

- Un `Catalogo` contiene muchos `Tipo`.
- Una `Regla` referencia uno o varios `Parametro`.
