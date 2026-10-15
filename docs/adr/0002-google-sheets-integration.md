# ADR 0002: integración futura con Google Sheets

## Status

Aceptada el 2026-10-15 como integración prevista; mecanismo técnico pendiente.

## Context

El flujo de origen previsto es Google Forms → Google Sheets → aplicación. La hoja pertenece al usuario y puede contener información privada.

## Decision

Usar Google Sheets como futura integración externa detrás de `services/data_loader.py`. Las pages no accederán directamente a la API ni a librerías de Sheets. Esta fundación no incorpora IDs, URLs privadas, cuentas de servicio ni credenciales.

## Consequences

Una spec posterior resolverá autenticación, permisos, librería, configuración, esquema y tratamiento de fallos o límites de servicio. No se ha elegido OAuth ni cuenta de servicio. La aplicación deberá distinguir fallos externos de ausencia de datos sin revelar configuración sensible. No se implementa integración ni acceso a Forms en esta fase.
