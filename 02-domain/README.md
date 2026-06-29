# Dominio

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Define el modelo de dominio del sistema de horarios y trazabilidad formativa del SENA: bounded contexts, entidades principales, reglas de negocio y eventos relevantes.

> **Diferencia con `06-data/`:** esta sección describe el dominio en términos de negocio (entidades, invariantes, reglas, lenguaje ubicuo). No describe tablas, columnas ni esquemas de base de datos. Esos detalles de implementación van en [`06-data/`](../06-data/).

## Archivos

| Archivo | Descripción | Estado |
|---------|-------------|--------|
| [domain-map.md](./domain-map.md) | Bounded contexts del sistema agrupados por módulo, con los servicios que pertenecen a cada uno. | 🟢 |
| [entities-and-rules.md](./entities-and-rules.md) | Entidades principales del dominio con su servicio dueño, y reglas de negocio confirmadas. | 🟢 |
| [domain-events.md](./domain-events.md) | Catálogo de eventos de dominio: evento, servicio publicador y descripción. | 🟢 |
