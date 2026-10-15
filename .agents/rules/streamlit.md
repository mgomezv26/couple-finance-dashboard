# Streamlit

**Propósito:** separar presentación, negocio y acceso a datos.

**Alcance:** futura UI Streamlit, incluidas las pages.

**Cuándo se aplica:** al implementar o revisar UI; actualmente no existe app ejecutable.

**Decisiones:** la UI consume el cargador definido en [data-access.md](data-access.md), sin acceder directamente a Google Sheets. Extrae lógica de negocio compleja de la UI. Mantén consistencia visual entre vistas una vez exista una convención comprobable. Presenta errores de carga sin exponer configuración privada.
