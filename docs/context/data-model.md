# Modelo de datos: límite del conocimiento actual

Se conoce el dominio general: información financiera de una pareja, procedente de una demo sintética o de una hoja del usuario. Los nombres Alex y Sam sirven solo para ejemplos ficticios, no establecen un modelo de usuarios o autenticación.

No hay entidades formalmente acordadas, tablas, columnas, relaciones ni datasets existentes. Google Forms y Google Sheets son componentes del flujo, no entidades del dominio.

Antes de implementar un contrato de carga, una nueva spec deberá resolver qué registros mínimos necesita la demo, sus campos, tipos y validaciones. Fechas, moneda, precisión de importes e identificación de registros siguen sin decidirse. No inferir el esquema de proyectos externos o privados.

La decisión de fuentes está en [ADR 0001](../adr/0001-demo-and-google-data-sources.md); este documento se actualizará cuando exista un modelo acordado.
