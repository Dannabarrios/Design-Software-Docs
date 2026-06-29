# api-contract — auth-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| POST | /auth/login | Autentica un usuario y emite token de sesión. |
| POST | /auth/logout | Cierra la sesión activa e invalida el token. |
| POST | /auth/refresh | Renueva el token de acceso usando el refresh token. |
| GET | /users | Lista usuarios del sistema. |
| POST | /users | Crea un usuario. |
| GET | /users/{id} | Consulta un usuario por identificador. |
| PUT | /users/{id} | Actualiza datos de un usuario. |
| GET | /roles | Lista roles disponibles. |
| POST | /roles | Crea un rol. |
| PUT | /roles/{id}/permissions | Asigna permisos a un rol. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
- Los tokens tienen tiempo de expiración configurable; la renovación exige refresh token válido.
