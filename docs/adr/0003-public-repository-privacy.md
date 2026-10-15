# ADR 0003: repositorio público y privacidad

## Status

Aceptada el 2026-10-15 como política del proyecto. La visibilidad remota del repositorio no se ha verificado ni modificado en esta tarea.

## Context

Se ha solicitado preparar un repositorio público separado del proyecto financiero privado. No se ha inspeccionado ni importado contenido de ese proyecto.

## Decision

Mantener esta base independiente y utilizar únicamente datos ficticios creados para ella. No copiar código ni material externo o privado. Los ejemplos personales usarán Alex y Sam. Aplicar la [regla de privacidad](../../.agents/rules/privacy.md) a todos los archivos preparados para versionar.

## Consequences

El futuro usuario configurará su fuente privada fuera del contenido público versionado. Documentación, fixtures y capturas deberán tener procedencia sintética. La revisión requiere inspeccionar contenido además de buscar patrones; anonimizar un archivo privado no es el procedimiento acordado para producir ejemplos. Esta decisión no publica ni modifica repositorios remotos.
