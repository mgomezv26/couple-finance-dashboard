# Constitución del proyecto

Versión: 1.0.0 · Adoptada: 2026-10-15

## I. Privacy by Design

El repositorio público contiene solo material sintético y configuración no sensible. La futura integración privada debe preservar esta separación desde el diseño. Regla operativa: [privacy.md](../../.agents/rules/privacy.md).

## II. Data Source Independence

La presentación consume un contrato de carga común, independiente de demo o Google Sheets. Cambiar la fuente no debe exigir reescribir pages.

## III. Demo Must Always Work

Cuando se implemente la app, la demo debe funcionar sin credenciales ni disponibilidad de Google. Desde entonces, cada cambio preservará ese recorrido. Actualmente no existe demo.

## IV. Specification Before Implementation

Define qué necesita el producto antes de codificar; separa requisitos, diseño, tareas y verificación. Una intención futura no autoriza implementarla.

## V. Simplicity First

Implementa el mínimo necesario para la spec vigente, sin infraestructura, dependencias ni abstracciones anticipadas.

## VI. Educational and Maintainable Code

Prioriza responsabilidades claras y comentarios que expliquen motivos para facilitar aprendizaje y mantenimiento.

## VII. Verifiable Changes

Cada cambio requiere evidencia adecuada a su naturaleza. No declares comprobaciones aprobadas sin ejecutarlas ni cierres tareas con fallos requeridos pendientes.

## Gobierno

Contrasta specs y planes con estos principios antes de implementar. Para modificarlos, documenta el motivo, actualiza versión y fecha, y revisa reglas y documentos afectados. Justifica decisiones arquitectónicas relevantes en ADRs. No amplíes el alcance solicitado mediante cambios documentales.
