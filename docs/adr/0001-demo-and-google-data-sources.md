# ADR 0001: fuentes demo y Google

## Status

Aceptada el 2026-10-15 como dirección de diseño; implementación pendiente.

## Context

El proyecto debe poder explorarse públicamente sin datos privados y permitir posteriormente consultar la hoja propia del usuario.

## Decision

Admitir un modo demo con datos totalmente ficticios y, después, una fuente Google Sheets del usuario. La UI utilizará un punto común de carga, con independencia de la fuente. La demo deberá funcionar sin Google.

## Consequences

El contrato común y la selección de fuente deberán especificarse antes de implementar. Las pruebas futuras comprobarán la independencia de la demo. No se derivarán fixtures de registros privados y no se ocultarán errores de Google sustituyendo datos silenciosamente. Esta decisión no crea una demo ni fija su esquema.
