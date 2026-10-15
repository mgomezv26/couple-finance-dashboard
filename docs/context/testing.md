# Estrategia de verificación

## Fundación documental

No existe suite de tests de aplicación. Para esta fase se comprueban el inventario requerido, destinos de enlaces relativos, formato de las skills, privacidad y coherencia de alcance. Se revisa el contenido completo, además del diff, porque los archivos nuevos pueden no aparecer en `git diff`.

La evidencia de cierre se conserva en el [checklist de fundación](../../specs/001-project-foundation/checklists/foundation.md). No se confunde esta validación con una demo funcional.

## Cuando exista implementación

- Añadir tests para lógica relevante y contratos del cargador, con fixtures sintéticos.
- Verificar independencia de fuentes y recorrido demo sin credenciales ni disponibilidad de Google.
- Cubrir entradas inválidas y fallos de lectura sin revelar configuración sensible.
- Verificar la UI afectada cuando existan pantallas.

Herramienta de tests, comandos y cobertura concreta se decidirán en la spec de implementación correspondiente. Las pruebas rutinarias deberán poder ejecutarse sin acceder a datos privados. Una integración real con Google requerirá una configuración separada y alcance explícito.

Regla de cierre: [testing.md](../../.agents/rules/testing.md). Revisión de entregas ejecutables: [release-check](../../.agents/skills/release-check/SKILL.md).
