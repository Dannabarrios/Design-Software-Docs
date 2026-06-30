# Integración y entrega continua

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Lineamientos de integración y entrega continua (CI/CD) del sistema. La herramienta de CI/CD concreta no está definida aún; este documento describe el flujo y las validaciones esperadas a nivel de pipeline genérico. La elección de herramienta se resolverá como parte del diseño de infraestructura.

## Flujo por ambientes

El pipeline sigue la estrategia de ramas del repositorio (ver [`00-governance/git-conventions.md`](../00-governance/git-conventions.md)):

```
hu-*-dev  ──PR──►  dev  ──PR──►  qa  ──PR──►  release/*  ──PR──►  main
```

Cada transición entre ambientes se activa mediante un Pull Request aprobado. No existe promoción automática sin revisión humana.

## Validaciones por etapa

### Al abrir un PR hacia `dev`

El pipeline valida que el cambio cumple las condiciones mínimas antes de permitir la revisión:

| Validación | Descripción |
|-----------|-------------|
| Lint de estructura de documentos | Verifica que los archivos tienen encabezado, estado, autor y están enlazados desde el README de su sección. |
| Validación de contratos OpenAPI | Verifica que los archivos en `07-api/contracts/openapi/` son válidos según el estándar OpenAPI (RNF-008). |
| Validación de contratos AsyncAPI | Verifica que los esquemas de eventos en `09-microservices/communication-patterns.md` son consistentes con el estándar AsyncAPI (RNF-008). |
| Conventional Commits | Verifica que los mensajes de commit siguen el formato `<type>(NN-section): description`. |
| Enlaces relativos | Verifica que los enlaces internos del repositorio no están rotos. |

### Al integrar en `dev`

El PR fue aprobado por al menos un revisor y todas las validaciones pasaron. Se integra el cambio y el ambiente `dev` refleja el estado actualizado.

### Al promover a `qa`

- El cambio integrado en `dev` pasa a `qa` mediante un nuevo PR (o cherry-pick para HUs específicas).
- El pipeline ejecuta las pruebas contractuales (RNF-009) de los servicios afectados por el cambio.
- Se valida que los contratos OpenAPI y AsyncAPI siguen siendo consistentes tras la integración.

### Al crear un `release/*` (staging)

- Se acumulan las HUs de una iteración en una rama `release/*`.
- El pipeline ejecuta las pruebas end-to-end sobre el ambiente de staging.
- Se genera un resumen de cambios para la revisión final antes del merge a `main`.

### Al integrar en `main`

- Solo se integran ramas `release/*` aprobadas.
- `main` representa el estado estable del repositorio y del sistema.

## Pruebas contractuales en el pipeline (RNF-009)

Las pruebas contractuales son obligatorias por microservicio y se ejecutan en el pipeline de `qa` en adelante:

- Cada servicio tiene pruebas que verifican su contrato OpenAPI publicado en `07-api/contracts/openapi/`.
- Los consumidores de un servicio tienen pruebas que verifican su lado del contrato.
- Un cambio de contrato que rompe compatibilidad debe incrementar la versión de la API y actualizar las pruebas de todos los consumidores antes de integrarse.

## Hotfix en main

Los hotfixes críticos en `main` siguen el flujo `fix/doc-*` → `main` → cherry-pick a `qa` y `dev`. El pipeline de `main` se ejecuta igual que el de `release/*`. Ver flujo completo en [`00-governance/git-conventions.md`](../00-governance/git-conventions.md).
