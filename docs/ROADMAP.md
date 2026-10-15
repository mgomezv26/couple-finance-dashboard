# Roadmap del producto

Este archivo es la única fuente de verdad para el roadmap general del producto. Describe las fases previstas, no especificaciones detalladas. Los requisitos pueden refinarse cuando comience cada fase.

Cada spec y su carpeta en `specs/` se crearán únicamente cuando vayamos a empezar la fase correspondiente. Incluir una fase aquí no inicia su implementación ni modifica la arquitectura actual.

## 001-project-foundation

**Estado:** completed

**Objetivo:** Preparar el repositorio, sistema de contexto para agentes, constitution, rules, skills, specifications, memory-bank, documentación y ADRs.

## 002-demo-data-source

**Estado:** planned

**Objetivo:** Crear una fuente de datos demo completamente ficticia y un data_loader que permita ejecutar la aplicación sin Google ni credenciales.

## 003-google-sheets-source

**Estado:** planned

**Objetivo:** Añadir una segunda fuente de datos basada en el Google Sheets propio del usuario, manteniendo la UI desacoplada de la fuente.

## 004-summary-dashboard

**Estado:** planned

**Objetivo:** Implementar el dashboard general de finanzas de la pareja usando la capa común de acceso a datos.

## 005-expenses-dashboard

**Estado:** planned

**Objetivo:** Implementar análisis, filtros y visualizaciones de gastos.

## 006-savings-dashboard

**Estado:** planned

**Objetivo:** Implementar seguimiento de cuentas de ahorro, evolución y ahorro mensual.

## 007-housing-goal

**Estado:** planned

**Objetivo:** Implementar seguimiento del objetivo financiero para compra de vivienda.

## 008-home-purchase-simulator

**Estado:** planned

**Objetivo:** Permitir simular la compra de una vivienda indicando precio, capital disponible, financiación, impuestos, gastos, colchón, plazo e interés hipotecario.

## 009-person-dashboard

**Estado:** planned

**Objetivo:** Crear dashboards individuales reutilizables para Persona 1 y Persona 2 sin nombres hardcodeados.

## 010-property-tracker

**Estado:** planned

**Objetivo:** Permitir registrar viviendas consideradas, contacto con inmobiliarias, visitas, características, valoración y conexión con el simulador de compra.
