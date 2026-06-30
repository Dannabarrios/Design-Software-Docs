# Datos

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

## Contenido

Documenta el modelo de datos global del sistema, el diccionario de entidades y la estrategia de migración.

> **Diferencia con `02-domain/`:** aquella sección describe las entidades en términos de negocio (invariantes, reglas, lenguaje ubicuo). Esta sección describe la implementación de persistencia (colecciones, atributos, tecnología, migraciones).

> **Diferencia con `09-microservices/`:** aquí vive el modelo de datos **global** — diccionario conceptual compartido y estrategia de migración. El detalle de colecciones propio de cada servicio se documenta en `09-microservices/services/<servicio>/data-model.md`.

## Archivos

| Archivo | Descripción | Estado |
|---------|-------------|--------|
| [models.md](./models.md) | Principio de una sola BD con colecciones por dominio y resumen por servicio. | 🟢 |
| [data-dictionary.md](./data-dictionary.md) | Diccionario de entidades del dominio con servicio dueño, descripción y campos clave. | 🟢 |
| [migration-strategy.md](./migration-strategy.md) | Estrategia de versionado de esquemas y preguntas abiertas con impacto en datos. | 🟢 |
