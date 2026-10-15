# Flujo de datos previsto

```text
Google Forms --> Google Sheets del usuario --> cargador --> aplicación
Datos demo ficticios -----------------------> cargador --> aplicación
```

El primer recorrido expresa el origen externo previsto: el usuario registra información mediante Forms y esta queda en su hoja. La aplicación futura consultaría Sheets a través de `services/data_loader.py`; no se ha definido acceso directo a Forms desde la app.

El segundo recorrido deberá poder funcionar sin servicios Google. La fuente demo no se obtendrá anonimizando información privada: sus datos serán creados desde cero.

No hay flujos ejecutables ni sincronización implementados. Frecuencia de lectura, configuración, validación y respuesta a errores requieren una spec posterior. Los datos y la configuración privada del usuario permanecerán fuera del contenido público versionado; véase [ADR 0003](../adr/0003-public-repository-privacy.md).
