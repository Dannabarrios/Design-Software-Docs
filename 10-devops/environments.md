# Ambientes

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Descripción de los ambientes del sistema y cómo se promueve un cambio entre ellos. Los ambientes están alineados con la estrategia de ramas definida en [`00-governance/git-conventions.md`](../00-governance/git-conventions.md).

## Tabla de ambientes

| Ambiente | Rama asociada | Propósito | Cómo se actualiza |
|----------|--------------|-----------|-------------------|
| **dev** | `dev` / `hu-*-dev` | Integración continua del trabajo en desarrollo. Primer ambiente donde los cambios se integran y conviven. | PR aprobado desde una rama `hu-*-dev` hacia `dev`. |
| **qa** | `qa` / `hu-*-qa` | Validación funcional y técnica de los cambios integrados en `dev`. | PR o cherry-pick aprobado desde `dev` hacia `qa`. |
| **staging** | `release/*` | Candidato a producción. Acumula las HUs de una iteración y se valida de forma integral antes del release. | PR desde `release/*` acumulando cherry-picks de `qa`. |
| **main / prod** | `main` | Estado estable del repositorio y del sistema. Solo recibe releases validados. | PR aprobado desde `release/*` hacia `main`. |

## Flujo de promoción

Un cambio avanza de ambiente en ambiente mediante Pull Request. No se salta ningún ambiente salvo en hotfixes críticos:

```
hu-*-dev  ──PR──►  dev  ──PR──►  qa  ──PR──►  release/*  ──PR──►  main
```

## Descripción por ambiente

### dev

Ambiente de integración continua. Recibe los cambios de todas las ramas `hu-*-dev` activas. Es el primer punto donde varios cambios conviven; pueden existir inconsistencias temporales mientras se integran las historias de la iteración. No se garantiza estabilidad en todo momento.

### qa

Ambiente de validación. Recibe cambios que ya pasaron la revisión en `dev`. Aquí se ejecutan las pruebas contractuales (RNF-009) y se valida que los contratos OpenAPI y AsyncAPI son consistentes (RNF-008). Un cambio que falla en `qa` no avanza a staging.

### staging

Ambiente preproducción. Agrupa las HUs completas de una iteración en una rama `release/*`. Se ejecutan las pruebas end-to-end sobre el entorno integrado completo. Es el último punto de validación antes de producción; los cambios en staging deben estar listos para ser liberados.

### main / prod

Ambiente de producción (o documentación estable en el contexto actual del repositorio). Solo recibe merges desde ramas `release/*` aprobadas. Representa el estado oficial y auditable del sistema. Los hotfixes críticos pueden llegar directamente desde ramas `fix/doc-*` y luego se aplican hacia atrás en `qa` y `dev` con cherry-pick.

## Reglas generales

- Ningún cambio se aplica directamente sobre una rama protegida (`dev`, `qa`, `release/*`, `main`).
- Toda promoción requiere al menos una aprobación de PR.
- Las rutas con CODEOWNER requieren la aprobación explícita del propietario asignado (ver [`11-quality/code-review.md`](../11-quality/code-review.md)).
- Los ambientes son independientes: un fallo en `qa` no afecta `dev` ni `main`.
