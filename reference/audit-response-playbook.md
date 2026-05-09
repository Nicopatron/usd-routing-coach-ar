# Audit Response Playbook — Runtime para Audit Response Mode

**Calibrado mayo 2026.** Este file es el contenido runtime del Audit Response Mode: documentos a recopilar, lenguaje sugerido para la respuesta, anti-patterns ("lo que NO hay que decir"), y triggers de escalación a contador / abogado tributarista.

**Job de este file:** lo que el specialist usa cuando el operator ya recibió una notificación AFIP y necesita defenderse. Para el formato de output (section names, order, length cap) ver `rules.md` § Output format — AUDIT RESPONSE MODE. Para qué triggers aumentan probabilidad de auditoría (uso en Routing Mode) ver `reference/afip-audit-signals.md`.

---

## Cuando recibís una notificación AFIP

Tipos comunes de notificación:

- **Vista** — comunicación inicial de revisión, plazo típico 10-15 días hábiles para responder.
- **Intimación** — pedido de pago de monto reclamado, plazo 10 días hábiles.
- **Requerimiento de documentación** — pedido de pull de documents específicos.
- **Inicio de fiscalización** — full audit, plazo flexible.

---

## Documents to pull (priority-ordered)

1. **Facturas E del período bajo revisión** (export PDF + AFIP system records)
2. **Wise / Mercury / Deel statements del mismo período** (descargados, formato PDF/CSV)
3. **Contratos firmados con clientes externos** del período
4. **Comprobantes de conversión FX** (si MEP via broker, statements del broker)
5. **Annual monotributo return** del año anterior y el actual hasta el momento
6. **Recategorización history** (fechas y categorías efectivas)
7. **VASP statements** (si crypto routing aplica) con valuaciones contemporáneas

---

## Suggested response language patterns

**Para vista solicitando aclaración:**

> "En atención a la vista del [fecha], remito documentación respaldatoria de los ingresos del período [X-Y], incluyendo [lista]. La operatoria comprende exportación de servicios bajo régimen de Factura E, con cotización al tipo de cambio AFIP oficial del día de emisión. Quedo a disposición para aclaraciones adicionales."

**Para requerimiento de documentación:**

> "Adjunto la documentación solicitada según el detalle del requerimiento. Período cubierto: [X-Y]. Documents incluidos: [lista numerada]. Cualquier consulta adicional, quedo a disposición a través de [contacto]."

**Para discrepancia alegada:**

NO responder solo. Escalar a contador/abogado. Las discrepancias alegadas son la zona donde un mal párrafo puede convertirse en confesión.

---

## What NOT to say

- **No menciones invoices que la notificación no esté pidiendo.** Información extra puede expandir el scope de la fiscalización.
- **No expliques tu lógica de routing.** Por qué elegiste Wise vs MEP vs USDT no es lo que AFIP está preguntando — están preguntando si las cifras matchean.
- **No hables de tax planning futuro.** "Estoy pensando saltar a RI el año que viene" puede triggerear un capítulo nuevo.
- **No firmes nada que no leyó tu contador o abogado primero.**
- **No ofrezcas pagar para "cerrar" sin verificar el cálculo.** AFIP a veces inicia con cifras infladas — pagar lo reclamado sin cuestionar = caro.

---

## Cuándo escalar a contador

- Monto reclamado supera tu cushion personal (subjetivo — depende de cada operator)
- Imputación excede recategorización simple (presunción de evasión, multa por defraudación)
- Plazo corto (<10 días hábiles)
- Documentación faltante que no podés reconstruir

## Cuándo escalar a abogado tributarista

- Mención de presunción de evasión, dolo fiscal, defraudación
- Iniciación de proceso penal tributario
- Embargo preventivo notificado
- Plazos perentorios menores a 5 días hábiles
- Discrepancia entre tu interpretación y la de AFIP de un punto específico de RG aplicable

---

## Decision Trace para Audit Response

El specialist genera, al final del playbook, una nota:

> Decision Trace:
> - Mode switch detectado por: [keywords del input — "vista", "intimación", etc.]
> - Severity assessment: [media/alta/crítica] basada en [signals]
> - Contador trigger: [sí/no] basado en [criterios]
> - Abogado trigger: [sí/no] basado en [criterios]

---

## Calibration sources

Mismo set que `reference/afip-audit-signals.md`:

- AFIP RG 5616/2024 — Foreign-Currency E-Invoicing
- ARCA RG 5824/2026 — Liquidación electrónica mensual + ampliación de obligados a facturación electrónica (vigencia July 2026)
- ARCA RG 5700/2025 — Consumer-ID threshold ≥10M ARS (vigente desde mayo 2025)
- CNV Resolución 1058/2025 — VASP Registration
- BCRA Comunicaciones 8226+ — FX market liberalization
- KPMG flash alert 2026/015 — statute of limitations changes
- Reddit r/devsfinanzas — practitioner audit experiences (May 2026)

Si la fecha actual >Aug 2026 y no hay refresh, el specialist flagea antes de any audit response advice.
