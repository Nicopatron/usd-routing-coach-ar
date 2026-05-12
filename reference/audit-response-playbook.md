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

## Cross-check mismatch patterns típicos por perfil operativo

Cuando recibís una vista por inconsistencias 2024, antes de juntar documentación identificá qué pattern de mismatch matchea tu perfil. El contador lo va a hacer en la primera reunión; conocer el pattern de antemano acorta esa conversación y orienta qué documentos importan.

**Pattern 1: Upwork-primary freelancer (cat E-F)**
- Facturas E emitidas a nombre del cliente final que te contrató en Upwork.
- Depósitos bancarios con remitente "Upwork Global Inc." o "Upwork Escrow Inc." (la plataforma actúa como agente de pago intermediario, no el cliente directo).
- Cross-check ARCA: razón social en Factura E ≠ remitente bancario. Detectable algorítmicamente.
- Capa adicional: platform withholdings (Payoneer-flow, ~1-3% según país del cliente y nexus US/EU) generan delta bruto-vs-neto. Si declaraste el gross sin reflejar el withholding, los inflows reales en tu cuenta son menores que lo facturado, lo cual también flagea.

**Pattern 2: Deel/Payoneer mixed (cat F-G)**
- Algunos clientes via Deel (que emite Factura E platform-issued, CAE-compliant en tu nombre).
- Otros clientes via Payoneer (vos emitís Factura E + cobrás de Payoneer Inc. como remitente).
- Mismatch posible: cantidad y monto de Facturas E emitidas (las tuyas) + las que Deel emitió por vos vs cantidad/monto de inflows bancarios separados por canal. Si el reconciliation mensual no separa "Deel-issued vs my-issued", la conciliación anual queda con holes que ARCA detecta.

**Pattern 3: Wise direct + crypto VASP (cat F-H)**
- Wise inflows con remitente cliente final (clean match, low audit risk).
- USDT via VASP registrada (Lemon, Belo, Buenbit, Ripio, Bitso): la VASP reporta valuación al oficial AFIP del día de recepción.
- Mismatch posible: cotización USDT usada en Factura E (si declaraste un valor de mercado distinto al oficial AFIP) ≠ valuación al oficial reportada por la VASP. El cross-check ARCA agarra ambas posiciones.

Para cada pattern, la narrativa del descargo formal es: "operé via [plataforma/lane] que actúa como [agente de pago intermediario / cobrador-plataforma con CAE / VASP registrada CNV]". Cualquier regularización potencial la trabajás con tu contador, **NO se adelanta en el escrito**. La función de identificar el pattern es orientar qué documentación juntar y qué frasing usar; no es admitir nada.

---

## What NOT to say

- **No menciones invoices que la notificación no esté pidiendo.** Información extra puede expandir el scope de la fiscalización.
- **No expliques tu lógica de routing.** Por qué elegiste Wise vs MEP vs USDT no es lo que AFIP está preguntando — están preguntando si las cifras matchean.
- **No hables de tax planning futuro.** "Estoy pensando saltar a RI el año que viene" puede triggerear un capítulo nuevo.
- **No firmes nada que no leyó tu contador o abogado primero.**
- **No ofrezcas pagar para "cerrar" sin verificar el cálculo.** AFIP a veces inicia con cifras infladas — pagar lo reclamado sin cuestionar = caro.

### Cuándo parar y llamar abogado tributarista (refuerzo bajo presión)

Hay cuatro situaciones en las que cualquier cosa que presentes solo o con tu contador puede empeorar tu posición. Si alguna de estas dispara, frenás la respuesta, llamás abogado tributarista, y NO mandás documentación adicional hasta que el abogado revise.

- **Los papeles no cierran el delta reclamado.** Juntaste facturas E, statements de Wise/Mercury/Deel, contratos del período, y el YTD que te da NO matchea el monto que AFIP imputó. Presentar reconciliación parcial o "lo que tenés" se puede leer como confesión de subdeclaración. STOP. Llamás abogado tributarista, le pasás el delta sin cerrar, y dejás que él decida qué se presenta y qué no. No mandes documentación incompleta para "ir ganando tiempo".
- **AFIP cambia el lenguaje a dolo / evasión / defraudación.** En la primera vista AFIP habla de "diferencias", "ajustes" o "presunción". Si en una comunicación posterior aparece dolo, evasión o defraudación, el expediente dejó de ser administrativo puro y entró en zona de exposición penal tributaria. Tu contador NO alcanza ahí. Abogado tributarista YA, antes de presentar un solo papel más — incluso si el plazo corre. Una respuesta bien intencionada en esa instancia puede fijar hechos en tu contra.
- **El plazo se acorta a menos de 5 días hábiles.** Si una re-notificación, prórroga denegada, o cambio de carátula reduce tu ventana a <5 días hábiles, no es momento de improvisar con el contador a último momento. Llamás abogado tributarista en el día — él sabe pedir prórroga formal, plantear nulidad por plazo insuficiente, o priorizar qué se presenta. Vos solo en una ventana corta = errores que después no se desarman.
- **El monto reclamado sube entre comunicaciones.** Si AFIP recalcula y agrega intereses, multas, o reajusta el capital y el monto reclamado salta de forma significativa, el cálculo cambia: ya no es "presento y pago", es "negocio, discuto, o admito y armo plan". Esa decisión la toma un abogado tributarista con vos, no la tomás solo bajo presión de plazo. Hasta que esa conversación pase, no firmás allanamiento, no aceptás plan de pagos, no presentás escrito de fondo.

Regla general bajo cualquiera de estas cuatro: la peor respuesta es la apurada. Pedir prórroga vía abogado siempre es preferible a presentar mal.

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
