# Desarrollo

## Preparación actual

Abre un checkout de este repositorio con Git y un editor de Markdown. Lee [AGENTS.md](../../AGENTS.md) y [activeContext.md](../../memory-bank/activeContext.md). No hay dependencias que instalar ni aplicación que ejecutar: todavía no existen `requirements.txt`, `app.py` o una suite de tests.

Python y Streamlit son tecnologías previstas, no un entorno reproducible ya configurado. La futura spec de implementación deberá fijar versiones compatibles, dependencias, preparación de entorno y comandos de arranque y pruebas antes de presentarlos como instrucciones válidas. Esta tarea no requiere instalar paquetes.

Para inspeccionar el trabajo documental desde la raíz:

```text
git status --short
git diff --check
git diff -- README.md
rg --files --hidden -g '!.git/**'
```

`rg` es una utilidad opcional de inventario. Revisa también los archivos nuevos directamente: el diff normal no incluye su contenido hasta que estén en el índice. No es necesario hacer staging, commit ni push para revisarlos.

## Spec-Driven Development

Cada cambio delimitado se documenta en `specs/<id-feature>/`:

| Archivo | Responsabilidad |
| --- | --- |
| `spec.md` | QUÉ necesita el producto: requisitos, exclusiones y aceptación verificable. |
| `plan.md` | CÓMO se implementará: diseño, archivos afectados, restricciones y verificaciones. |
| `tasks.md` | Pasos ejecutables y estado de cada tarea. |
| `checklists/` | Comprobación de calidad y requisitos con evidencias. |

Flujo completo:

Constitution → Specify → Clarify → Plan → Checklist → Tasks → Analyze → Implement → Converge.

- **Constitution:** comprobar principios y límites duraderos.
- **Specify / Clarify:** definir necesidad y resolver dudas materiales; registrar lo que queda fuera.
- **Plan / Checklist / Tasks:** concretar diseño, criterios de revisión y pasos ejecutables.
- **Analyze:** comprobar coherencia entre requisitos, diseño, tareas y constitución.
- **Implement:** ejecutar únicamente el alcance autorizado.
- **Converge:** contrastar resultado con aceptación, corregir fallos y actualizar contexto y memoria.

Para cambios pequeños: Specify → Plan → Tasks → Implement → Converge. Se pueden usar secciones breves en la spec pertinente, manteniendo requisitos y verificaciones explícitos. El flujo reducido no elimina la privacidad ni la comprobación de resultados.

La [spec 001](../../specs/001-project-foundation/spec.md) cubre solo la fundación. La próxima fase necesita sus propios requisitos; no se inicia automáticamente al cerrar esta.
