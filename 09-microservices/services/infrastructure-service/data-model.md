# data-model — infrastructure-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| Recurso | Ambiente o recurso físico del SENA (aula, laboratorio, taller, equipo). |
| Inventario | Registro de ítems de inventario asociados a un recurso. |
| Disponibilidad | Estado de disponibilidad operativa de un recurso en un período. |
| Reserva | Bloqueo temporal de un recurso para una actividad planificada. |

## Relaciones

- Un `Recurso` tiene un `Inventario` con muchos ítems.
- Un `Recurso` tiene muchas `Disponibilidad` a lo largo del tiempo.
- Una `Reserva` referencia un `Recurso` y define el período bloqueado.
- Una `Reserva` activa reduce la `Disponibilidad` del `Recurso` en ese período.
