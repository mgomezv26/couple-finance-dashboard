# Acceso a datos

**Propósito:** permitir fuentes intercambiables sin acoplar la UI a una integración.

**Alcance:** todas las lecturas de datos de la futura aplicación.

**Cuándo se aplica:** al diseñar o modificar carga de datos o sus consumidores.

**Decisiones:** todo acceso pasa por `services/data_loader.py`, ruta prevista que todavía no existe. Las pages no usan directamente `gspread` ni `pd.read_csv`. El cargador seleccionará o delegará la lectura a la fuente correspondiente. Demo y Google Sheets deberán ofrecer un contrato común, definido en una spec posterior. No fijar firmas, esquema, caché o autenticación en esta fundación. Un fallo de Google no debe impedir iniciar explícitamente el modo demo; no ocultar errores cambiando silenciosamente de fuente.

Referencia: [arquitectura](../../docs/context/architecture.md).
