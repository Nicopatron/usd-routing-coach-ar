# AFIP Audit Signals — Triggers, Mistakes, Audit Response Playbook

**Calibrado mayo 2026.** AFIP / ARCA enforcement 2025-2026 está en modo restrictivo: SIRA + algorithmic matching + RG 5616/2024 (e-invoicing) + RG 5700/2025 (Consumer-ID ≥10M ARS) + RG 5824/2026 (liquidación electrónica mensual + ampliación de obligados, vigencia julio 2026) → menos zona gris, más auditoría algorítmica.

Este file cubre dos cosas:
1. Qué signals disparan auditoría (para evitarlos en Routing Mode).
2. Qué hacer cuando ya recibiste notificación (para Audit Response Mode).

---

## Top 3 mistakes que disparan auditoría (frecuencia + severidad real)

### Mistake #1 — Invoice-FX mismatch

**Qué es:** facturás $5K USD a 1.395 ARS oficial el día de emisión, pero declarás esa Factura E al tipo de cambio del cobro (1.450 dos semanas después). El sistema AFIP auto-valida invoice metadata contra inflows reportados — la inconsistencia es detectable algorítmicamente.

**Severity:** alta. Penalty 25-75% del monto desfasado + intereses + back-tax. SIRA flagea automático en 3-6 meses.

**Cómo se evita:**
- Emitir Factura E en USD con cotización oficial AFIP del día de emisión.
- Reconciliar el dato del Wise statement contra la Factura E al cierre de mes.
- Si hay diferencia FX entre emisión y cobro, eso es ganancia/pérdida de cambio (renglón aparte para Bienes Personales/Ganancias en RI; en monotributo no afecta directamente la cat pero requiere registro en libro IVA digital opcional).

### Mistake #2 — Factura C (doméstica) a cliente foreign

**Qué es:** emitís Factura tipo C (régimen doméstico) cuando el cliente es no-residente. Type B para clientes locales finales, type A para empresas locales registradas, type E para exportación. Mezclar = audit trigger.

**Severity:** alta. Reclasificación a IIBB (gross income) provincial sin la exención de exportación. Pérdida del beneficio export = potencial salto de cat o forzado a RI.

**Cómo se evita:**
- Siempre Factura E para no-residentes.
- Verificar que el campo "país del receptor" esté correcto en el sistema AFIP.
- Mantener contrato firmado con el cliente externo on file (sirve como respaldo de export-service).

### Mistake #3 — Cash deposits sin invoice trail correspondiente

**Qué es:** declarás $3K USD/mes en monotributo via Factura E, pero hacés deposits cash adicionales (referidos, freelance side, friends-and-family) por otros $1-2K USD/mes en pesos. SIRA tracking + algorithmic deposit-vs-income matching te encuentra.

**Severity:** muy alta. ARBA/AFIP pueden disallowed full monotributo deduction + reclasificación + criminal referral si hay evidencia de intencionalidad.

**Cómo se evita:**
- Cada ingreso requiere Factura. Sin excepciones.
- Side-projects = segunda actividad code o aceptar que entran al mismo monotributo bucket (sumando para el límite de cat).
- Cash recibido informal (regalo familiar, devolución personal) tiene que tener fundamento documentable distinto a "ingreso".

---

## Otros triggers comunes (frecuencia menor pero relevantes)

### Salto sostenido de invoicing sin recategorización

Si pasás de cat F a cat H de un mes a otro (doble de invoicing) y no recategorizás dentro de 30 días, AFIP detecta y te recategoriza ellos con multa.

### Multiple monotributo registrations sin actividad clara

Tener múltiples actividades dentro de monotributo es legal pero requiere coding distinto. Si todas tus actividades están bajo el mismo code (ej: "consultoría informática") pero el flujo sugiere actividades distintas (consultoría + venta productos digitales + alquileres), audit trigger.

### Holding USD sustancial sin justificación

Mantener Wise USD account con saldo >$50K USD acumulado puede triggerear Bienes Personales review si no está declarado como activo en exterior. Pre-BCRA-liberalization 2025 era más estricto; post liberalization es más permisivo pero el threshold sigue.

### Crypto receipts sin tax basis documentation

USDT recibido sin valuación al oficial del día de recepción documentada = AFIP escrutinio. CNV obliga a VASPs a reportar; si tu estatement de la VASP no matchea con tu declaración mensual, flag.

### Platform payments sin compliance withholding

Deel, Payoneer, Upwork pueden aplicar withholdings propios según su lógica interna y residencia (p.ej. 1099 reporting si hay U.S. tax nexus). NO hay un RG argentino específico que extienda withholding a estas plataformas para consultores AR (RG 5319/2023, a veces mal citada para esto, es un régimen de percepción IVA sobre portales virtuales locales tipo Mercado Libre y excluye explícitamente a monotributistas). Si tu net cobrado no matchea con el bruto declarado, eso por sí solo es audit trigger — independientemente del origen del withholding.

---

## Audit Response Mode — Playbook defensivo

### Cuando recibís una notificación AFIP

Tipos comunes de notificación:

- **Vista** — comunicación inicial de revisión, plazo típico 10-15 días hábiles para responder.
- **Intimación** — pedido de pago de monto reclamado, plazo 10 días hábiles.
- **Requerimiento de documentación** — pedido de pull de documents específicos.
- **Inicio de fiscalización** — full audit, plazo flexible.

### Documents to pull (priority-ordered)

1. **Facturas E del período bajo revisión** (export PDF + AFIP system records)
2. **Wise / Mercury / Deel statements del mismo período** (descargados, formato PDF/CSV)
3. **Contratos firmados con clientes externos** del período
4. **Comprobantes de conversión FX** (si MEP via broker, statements del broker)
5. **Annual monotributo return** del año anterior y el actual hasta el momento
6. **Recategorización history** (fechas y categorías efectivas)
7. **VASP statements** (si crypto routing aplica) con valuaciones contemporáneas

### Suggested response language patterns

**Para vista solicitando aclaración:**

> "En atención a la vista del [fecha], remito documentación respaldatoria de los ingresos del período [X-Y], incluyendo [lista]. La operatoria comprende exportación de servicios bajo régimen de Factura E, con cotización al tipo de cambio AFIP oficial del día de emisión. Quedo a disposición para aclaraciones adicionales."

**Para requerimiento de documentación:**

> "Adjunto la documentación solicitada según el detalle del requerimiento. Período cubierto: [X-Y]. Documents incluidos: [lista numerada]. Cualquier consulta adicional, quedo a disposición a través de [contacto]."

**Para discrepancia alegada:**

NO responder solo. Escalar a contador/abogado. Las discrepancias alegadas son la zona donde un mal párrafo puede convertirse en confesión.

### What NOT to say

- **No menciones invoices que la notificación no esté pidiendo.** Información extra puede expandir el scope de la fiscalización.
- **No expliques tu lógica de routing.** Por qué elegiste Wise vs MEP vs USDT no es lo que AFIP está preguntando — están preguntando si las cifras matchean.
- **No hables de tax planning futuro.** "Estoy pensando saltar a RI el año que viene" puede triggerear un capítulo nuevo.
- **No firmes nada que no leyó tu contador o abogado primero.**
- **No ofrezcas pagar para "cerrar" sin verificar el cálculo.** AFIP a veces inicia con cifras infladas — pagar lo reclamado sin cuestionar = caro.

### Cuándo escalar a contador

- Monto reclamado supera tu cushion personal (subjetivo — depende de cada operator)
- Imputación excede recategorización simple (presunción de evasión, multa por defraudación)
- Plazo corto (<10 días hábiles)
- Documentación faltante que no podés reconstruir

### Cuándo escalar a abogado tributarista

- Mención de presunción de evasión, dolo fiscal, defraudación
- Iniciación de proceso penal tributario
- Embargo preventivo notificado
- Plazos perentorios menores a 5 días hábiles
- Discrepancia entre tu interpretación y la de AFIP de un punto específico de RG aplicable

### Decision Trace para Audit Response

El specialist genera, al final del playbook, una nota:

> Decision Trace:
> - Mode switch detectado por: [keywords del input — "vista", "intimación", etc.]
> - Severity assessment: [media/alta/crítica] basada en [signals]
> - Contador trigger: [sí/no] basado en [criterios]
> - Abogado trigger: [sí/no] basado en [criterios]

---

## Calibration sources

- AFIP RG 5616/2024 — Foreign-Currency E-Invoicing
- ARCA RG 5824/2026 — Liquidación electrónica mensual + ampliación de obligados a facturación electrónica (vigencia July 2026)
- ARCA RG 5700/2025 — Consumer-ID threshold ≥10M ARS (vigente desde mayo 2025)
- CNV Resolución 1058/2025 — VASP Registration
- BCRA Comunicaciones 8226+ — FX market liberalization
- KPMG flash alert 2026/015 — statute of limitations changes
- Reddit r/devsfinanzas — practitioner audit experiences (May 2026)

Si la fecha actual >Aug 2026 y no hay refresh, el specialist flagea antes de any audit response advice.
