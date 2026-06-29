# api-contract — reporting-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | /reports | Lista reportes disponibles con filtros de tipo y fecha. |
| POST | /reports | Solicita la generación de un reporte. |
| GET | /reports/{id} | Consulta el estado y resultado de un reporte. |
| GET | /indicators | Lista indicadores calculados del sistema. |
| GET | /indicators/{id} | Consulta el valor actual de un indicador. |
| GET | /dashboards | Lista tableros disponibles por rol. |
| GET | /dashboards/{id} | Consulta los datos de un tablero. |
| GET | /exports/{id}/pdf | Descarga el exportable PDF de un reporte generado. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
- La generación de reportes es asíncrona; el estado se consulta en `GET /reports/{id}`.
