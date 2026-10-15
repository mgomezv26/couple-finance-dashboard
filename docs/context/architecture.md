# Arquitectura

## Estado actual

El repositorio contiene documentación de gobierno, contexto, especificaciones y memoria. No hay módulos Python, UI, servicios, datasets, dependencias instalables ni tests de aplicación definidos en el repositorio.

## Límites acordados para la futura aplicación

```text
UI Streamlit (incluidas futuras pages)
                 |
                 v
services/data_loader.py (punto de entrada previsto)
                 |
                 +--> fuente demo sintética
                 +--> fuente Google Sheets del usuario
```

El cargador será la frontera entre UI y fuentes. Su existencia futura es una decisión de diseño, no un archivo implementado. Las restricciones operativas están en [data-access.md](../../.agents/rules/data-access.md) y [streamlit.md](../../.agents/rules/streamlit.md).

Quedan por especificar contrato de carga, validación, formato demo, tratamiento de errores y configuración de selección de fuente. Tampoco se han decidido caché, autenticación ni librerías de integración. No hay base de datos ni despliegue previstos dentro de esta fundación.

Motivos: [ADR 0001](../adr/0001-demo-and-google-data-sources.md) y [ADR 0002](../adr/0002-google-sheets-integration.md).
