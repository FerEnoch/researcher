# Workflow

## Roles

### ORCHESTRATOR_MODEL
Responsable de:
- coordinar fases,
- lanzar subagentes,
- mantener trazabilidad,
- consolidar artefactos,
- responder críticas,
- producir síntesis final.

### ADVERSARIAL_MODEL
Responsable de:
- falsar decisiones,
- detectar supuestos débiles,
- cuestionar arquitectura y stack,
- buscar riesgos ignorados,
- adjudicar cuando corresponda.

### SPECIALIST SUBAGENTS
Opcionales y dinámicos. Pueden cubrir:
- seguridad,
- base de datos,
- frontend,
- backend,
- DevOps,
- cloud,
- integración,
- compliance,
- performance,
- accessibility.

## Secuencia

1. Leer Product Brief + Claim Ledger.
2. Hacer preguntas materiales al usuario si es necesario.
3. Traducir producto a requisitos técnicos.
4. Modelar dominio y datos.
5. Derivar architecture drivers.
6. Explorar alternativas técnicas.
7. Analizar seguridad/compliance.
8. Analizar integraciones.
9. Diseñar estrategia operativa.
10. Crear hipótesis arquitectónicas.
11. Consolidar V1 + decision ledger.
12. Ejecutar revisión adversarial.
13. Defender/revisar.
14. Adjudicar.
15. Crear Technical Discovery final.

## Regla secuencial

Los subagentes deben trabajar de forma secuencial cuando una fase dependa de la anterior.
No lanzar en paralelo tareas que puedan producir supuestos incompatibles sobre el mismo fundamento.

El orquestador puede usar paralelismo solo para investigaciones independientes y debe reconciliarlas antes de continuar.


## Boundary / handoff posterior

Una vez creado `FINAL_TECHNICAL_DISCOVERY.md`, este workflow termina.

El siguiente paso recomendado es crear los ADRs necesarios para el proyecto. Ese trabajo será **asistido por IA**, pero debe diseñarse de manera **hiper-especializada y ad hoc para cada caso**, no mediante una continuación protocolizada universal.

El handoff debe incluir:
- decisiones candidatas a ADR,
- alternativas que todavía merecen contraste,
- restricciones y architecture drivers,
- unresolved relevantes,
- riesgos y triggers de re-arquitectura,
- evidencia disponible.

No generar un protocolo fijo de ADRs como parte de esta secuencia.
