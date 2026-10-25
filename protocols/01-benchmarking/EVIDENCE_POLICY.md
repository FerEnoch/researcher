# Evidence Policy

## 1. Clasificación de fuentes

Priorizar, en este orden cuando sea razonable:

1. **Fuentes primarias**: sitio oficial, documentación, pricing oficial, términos, changelog, API docs, app stores, material regulatorio, organismos públicos, repositorios oficiales.
2. **Fuentes secundarias de alta calidad**: medios especializados, firmas de research reconocidas, estudios académicos, informes sectoriales con metodología visible.
3. **Fuentes comunitarias**: GitHub issues/discussions, Reddit, foros, reviews, comunidades profesionales. Útiles para problemas reales y percepción de usuarios, pero no para afirmar hechos duros sin triangulación.
4. **Fuentes débiles**: agregadores, contenido SEO, blogs sin metodología, resúmenes automáticos. Pueden servir como pistas, nunca como base única para claims importantes.

## 2. Reglas por claim

Cada claim material debe registrar:

- `CLAIM_ID`
- afirmación
- categoría
- fuente(s)
- fecha de publicación o consulta cuando sea pertinente
- tipo de fuente
- fuerza de evidencia
- alcance geográfico
- si es `FACT`, `INFERENCE` u `OPINION`
- nivel de confianza
- objeciones conocidas
- estado: `SUPPORTED`, `PARTIALLY_SUPPORTED`, `CONTESTED`, `REJECTED` o `UNRESOLVED`

## 3. Triangulación

- Claims estratégicos o de alto impacto no deben depender de una única fuente débil.
- Cuando exista una fuente primaria clara, esta tiene prioridad sobre resúmenes secundarios, salvo evidencia de desactualización.
- Datos de mercado deben incluir año, región y metodología cuando estén disponibles.
- No extrapolar automáticamente tendencias de EE.UU./Europa a Argentina.

## 4. Actualidad

Distinguir entre:

- hechos estructurales del rubro;
- estado actual de productos/competidores;
- tendencias recientes;
- hipótesis futuras.

Los datos sensibles al tiempo deben registrar fecha.

## 5. Inferencias técnicas

Al analizar arquitectura, stack, SEO, performance, accesibilidad, integraciones, modelo de datos observable o patrones técnicos:

- diferenciar lo confirmado de lo inferido;
- no afirmar tecnologías ocultas como hechos sin evidencia;
- explicar la base de la inferencia;
- marcar limitaciones de observabilidad.

## 6. Regla adversarial

Una objeción no invalida un claim por ser convincente. El adjudicador debe evaluar:

`calidad de evidencia + independencia de fuentes + actualidad + relevancia geográfica + aplicabilidad al caso`

Si ninguna postura supera razonablemente a la otra, el claim queda `UNRESOLVED`.

## 7. Argentina

La adaptación argentina requiere investigación propia. Debe revisar cuando aplique:

- actores locales;
- hábitos de compra/uso;
- WhatsApp y canales de contacto;
- medios de pago y Mercado Pago;
- facturación e implicancias operativas de ARCA;
- regulación sectorial;
- privacidad y tratamiento de datos;
- logística y cobertura territorial;
- integraciones locales;
- estructura de costos y expectativas comerciales;
- restricciones económicas/monetarias relevantes;
- prácticas de soporte y onboarding del mercado local.

No convertir esta etapa en una mera traducción del benchmark global.
