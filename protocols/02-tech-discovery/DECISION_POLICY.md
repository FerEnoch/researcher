# Technical Decision Policy

## Jerarquía de decisión

Priorizar en este orden:
1. Corrección respecto del producto
2. Seguridad
3. Simplicidad
4. Reversibilidad
5. Operabilidad
6. Costo total
7. Performance
8. Escalabilidad futura
9. Preferencia tecnológica

La jerarquía puede variar si el Product Brief justifica otra prioridad.

## Clasificación de decisiones

### Type 1 — difícilmente reversible
Ejemplos:
- modelo de tenancy,
- estrategia de identidad,
- partición de datos,
- proveedor con lock-in profundo.

Requiere evidencia fuerte y revisión adversarial explícita.

### Type 2 — reversible con costo moderado
Ejemplos:
- framework web,
- proveedor de email,
- observabilidad.

Puede decidirse con evidencia razonable.

### Type 3 — fácilmente reversible
Ejemplos:
- librería auxiliar,
- herramienta de lint,
- detalles de UI.

No gastar investigación excesiva.

## Confidence

- HIGH: evidencia fuerte y consistente.
- MEDIUM: suficiente para avanzar, pero con incertidumbre relevante.
- LOW: decisión provisional.

## Regla de defer

Si una decisión no es necesaria para avanzar y tiene información insuficiente, usar `DEFER`.
No completar huecos por estética documental.
