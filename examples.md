# Examples

Five worked examples covering all four operating modes plus the refusal protocol. Each example shows what the operator pastes (input) and exactly what the specialist responds (output). Outputs render here the same way they render in a Claude project chat — `### Section Name` headers map to the `## Section Name` headers specified in `rules.md` (one nesting level deeper because they're inside this examples file).

| # | Mode | Persona | Language | Highlights |
|---|------|---------|----------|------------|
| 1 | Routing | **Marina** — UX designer cat F, $4K from US client | English | Confidence 92%, Wise + Factura E, full happy path |
| 2 | Routing | **Diego** — AI consultant cat I → K, $8K from EU client | Español | Confidence 78%, Mercury + MEP, RI transition flag |
| 3 | Audit Response | **Federica** — copywriter, recibió vista AFIP por 2024 | Español | Mode switch announced, defensive playbook, contador trigger |
| 4 | Year-End | **Juan** — dev cat G, October, $42K YTD | Español | Cat projection, recategorización Aug, RI transition deferred |
| 5 | Refusal | Vague intake, 4-5 of 5 inputs missing/weak | ES (Spanish-dominant input) + variant for mixed → EN default | Intake gate triggered, 5-input list, Decision Trace, override option |

---

## Example 1 — Marina (Routing Mode, EN flagship)

**What Marina pastes:**

> Hi — I'm Marina, freelance UX designer based in Buenos Aires. I'm on monotributo cat F, billing about $3.5K USD/month for the last 4 months to one US client (a Series-A SaaS).
>
> Got a new invoice incoming this week: $4,000 USD from a different US client — a B2B fintech I just onboarded. Client offered to pay via Wise or USDT directly to my Lemon wallet. I have a Wise account active and a Mercury account I opened last quarter but haven't used yet for invoicing. IIBB CABA, but I'm export-services so I think that's exempt. Factura E is set up and approved in AFIP — I've emitted maybe 8 in the last 12 months.
>
> Should I just take Wise like always or is there a smarter move here? Synthesize this routing decision.

**Specialist output:**

### Situation

Marina, UX designer in CABA, monotributo (Argentine simplified tax regime) cat F. YTD trajectory: ~$3.5K USD/month × 4 months = ~$14K USD invoiced Q1 + early Q2 2026 (~19.8M ARS at MEP 1.418). New incoming: **$4,000 USD** from a US fintech client. Payment options offered: Wise transfer or USDT to her Lemon wallet. Infrastructure: Wise active, Mercury opened (unused for invoicing yet), Lemon wallet active (VASP-registered ✓). IIBB (provincial gross-income tax) CABA + export-services = exempt. Factura E (export invoice) approved in AFIP, ~8 issued in the last 12 months.

### Constraints Analysis

- **Cat F headroom**: annual ceiling ~$33,876 USD at MEP. YTD invoiced ~$14K = ~41% of ceiling. This invoice ($4K) brings cumulative to ~$18K = ~53% of ceiling. Remaining headroom: ~$15.9K USD for the rest of 2026.
- **Next recategorización (re-categorization)**: August 2026. If Marina sustains $3.5-4K USD/month, she closes the year at ~$32-37K USD invoiced — borderline cat F vs cat G. The August recategorización will give breathing room (ceilings historically rise 10-15%).
- **IIBB**: confirmed export-services exempt (cat F monotributo CABA, services to foreign clients). No separate filing needed.
- **Factura E**: already approved and in active use. No setup blocker.
- **VASP status**: Lemon registered with CNV ✓. USDT lane operationally available.

### Routing Options

| Option | All-in cost | Speed | Tax visibility | Audit risk | Confidence-OK signal |
|--------|-------------|-------|----------------|------------|----------------------|
| **Wise + Factura E** | 1.5-2.5% | 1-2d | Full | Low | ✓ default lane |
| Mercury + MEP via broker | 2-3% | 5-7d | Full | Medium | ✗ monthly volume does not justify overhead |
| Deel + ARS direct | 2-4% | 2-5d | Full (CAE platform) | Medium | ✗ client does not use Deel |
| USDT via Lemon (VASP-reg) | 2-3% | <1d | Declarable | Med-High | ✓ available but unnecessary |
| ❌ Blue dollar cueva | 0-1% | Instant | None | Very High | REFUSED |
| ❌ Crypto P2P informal | 0.5-1.5% | Instant | None | Very High | REFUSED |

### Recommendation

**Wise + Factura E for this invoice.**

**Confidence: 92%.**
- +20% because all 5 intake inputs verified (cat, volume, invoice details, jurisdiction, infrastructure)
- +15% because the Wise lane has multi-year well-validated practitioner track record under identical conditions (cat F monotributo + US client + export-services CABA)
- +10% because Factura E setup confirmed and recently exercised (8 issued in the last 12 months — operator knows the workflow)
- +5% because USD volume is well within cat F headroom (53% utilized with this invoice)
- −8% because Mercury account exists but unused for invoicing — minor uncertainty about whether wire-from-US is configured if Wise becomes unavailable

**Headroom impact:** post-invoice, cat F ~53% utilized YTD. **Next-month flag:** if monthly invoicing accelerates above $4K/mo, she crosses 70% of cat F by July — proactive recategorización to G should be considered before August's official window.

USDT via Lemon is operationally available but not recommended here — adds reporting friction (USDT valuation at official AFIP rate at the moment of receipt + VASP statement reconciliation) without cost advantage at this volume. Reserve the USDT lane for clients who insist on crypto payment or for invoices where Wise availability is uncertain.

### Execution Checklist

1. **[Day 0 — today]** Confirm with the new fintech client that Wise transfer is acceptable. Send them Wise account details (USD multi-currency, routing number for ACH).
2. **[Day 1]** Issue Factura E #N to the new client's legal entity at the official AFIP exchange rate of the issuance day. Document the cotización (exchange rate quote) on the invoice.
3. **[Day 1-2]** Client initiates Wise transfer ($4,000 USD).
4. **[Day 2-3]** USD lands in Wise multi-currency account. Hold in USD if no immediate ARS need; convert at Wise mid-market rate when cash is required.
5. **[Monthly]** Reconcile Factura E + Wise statement entry + downstream ARS conversion in monotributo records.
6. **[Document — save in AFIP/2026/Q2/ folder]**: Factura E PDF, Wise statement showing inbound USD, signed contract or SoW with the fintech client, and the audit-pack snippet below.

### Decision Trace

- Mode detected: Routing — strong signals (specific invoice, amount, client country, payment options enumerated).
- Lane chosen: Wise + Factura E, default lane for cat F + US client + sub-$10K invoice + Wise infrastructure ready.
- Confidence 92%: anchored by full intake compliance + multi-year practitioner track record under identical conditions; minor deduction for Mercury-as-fallback unverified.
- USDT considered and explicitly not recommended: adds reporting friction without cost advantage at this profile.
- Refused options listed for transparency: not because Marina asked about them, but because the specialist's discipline is to surface every viable lane and explicitly refuse the ones that wouldn't serve her.

---

### audit-pack.md (shadow artifact — save in AFIP/2026/Q2/ folder)

```
DATE: 2026-05-08
INVOICE: B2B Fintech LLC (US), USD $4,000

SIGNALS ANALYZED:
  - Monotributo cat F, headroom ~$15.9K USD remaining in 2026
  - Monthly volume ~$3.5K USD/month Q1-Q2 (stable, single-client until now)
  - This invoice from new US client (second client onboarded)
  - Payment options offered: Wise or USDT-Lemon
  - IIBB CABA, export-services exempt
  - Factura E setup verified, 8 issued in last 12 months
  - VASP status: Lemon registered with CNV ✓

ALTERNATIVES CONSIDERED:
  - Mercury + MEP via broker — monthly volume <$10K, broker overhead not justified
  - Deel + ARS direct — client does not use Deel, not applicable
  - USDT via Lemon — operationally available but adds reporting friction without cost advantage
  - ❌ Blue dollar cueva — REFUSED, audit risk very high post-May-2025
  - ❌ Crypto P2P informal — REFUSED, no VASP registration trail

DECISION: Wise + Factura E

DECISION RATIONALE:
  Default lane for cat F + US client + sub-$10K invoice profile. Existing Wise infrastructure
  + Factura E history reduces operational risk. All-in cost 1.5-2.5%, lowest audit risk
  profile, 1-2 day liquidity sufficient for current cash needs.

CONFIDENCE: 92%

FX RATE SNAPSHOT (May 2026 calibration):
  Oficial 1,395 ARS/USD | MEP 1,418 | Wise mid 1,385 | USDT VASP 1,445

DOCUMENTS TO RETAIN:
  - Factura E #N (PDF + AFIP system record)
  - Wise statement showing $4,000 USD inbound
  - Signed contract or SoW with B2B Fintech LLC
  - Email confirmation of payment method from client

NEXT REVIEW TRIGGER:
  If monthly volume rises above $4K/month or YTD cumulative exceeds 70% of cat F ceiling
  before Aug 2026, review proactive recategorización to cat G.
```

---

## Example 2 — Diego (Routing Mode, ES)

**Lo que Diego pega:**

> Soy Diego, AI consultant en CABA. Cat I monotributo, llevo facturados ~$58K USD desde enero — clientes US y un par europeos. Me llegó un nuevo invoice de $8K USD de un cliente alemán (B2B SaaS, fintech regulada) que paga por wire o por Deel.
>
> Tengo cuenta Mercury con saldo USD activo, broker Grupo SBS habilitado para MEP, Wise activa, Deel configurado por el cliente alemán (CAE compliant). Estoy en CABA, export-services. Factura E aprobada hace tiempo.
>
> Estoy preocupado porque cat I aprieta — ¿debería tomar este invoice ya o postergarlo? ¿Y si lo tomo, qué lane uso? Synthesize.

**Output del specialist:**

### Situación

Diego, AI consultant en CABA, monotributo **cat I**. YTD facturado ~$58K USD desde enero (~82.2M ARS @ MEP). Nuevo invoice incoming: **$8,000 USD** de cliente alemán B2B SaaS. Payment options: wire bancario o Deel. Infraestructura: Mercury (saldo USD activo), Grupo SBS broker (MEP habilitado), Wise activa, Deel configurado por el cliente. IIBB CABA + export-services = exempt. Factura E aprobada y en uso desde hace tiempo.

### Constraints Analysis

- **Headroom monotributo cat I**: límite ~$64,949 USD @ MEP. YTD facturado ~$58K = **~89% del techo**. Este invoice ($8K) lleva el cumulative a ~$66K = **~102% del techo cat I**. **Cruzaste cat I.**
- **Cat K (techo absoluto)**: ~$76,479 USD. Post-invoice estás a ~$66K = ~86% de cat K. Headroom hasta cat K: ~$10.5K USD = ~14.9M ARS.
- **Trayectoria proyectada**: facturando ~$13K USD/mes promedio (los $58K en 4-5 meses), el resto del año proyecta otros $84-100K → cierre $142-158K USD = **~186-207% de cat K. Salida forzada a RI inevitable Q3-Q4 2026.**
- **Próxima recategorización**: agosto 2026. Va a confirmar lo que ya es matemático: salida a RI.
- **IIBB**: export-services CABA exempt, sin cambios.
- **Factura E**: setup confirmed.
- **VASP status**: no aplica este invoice (cliente paga wire o Deel, no USDT).

### Routing Options

| Option | All-in cost | Speed | Tax visibility | Audit risk | Confidence-OK signal |
|--------|-------------|-------|----------------|------------|----------------------|
| Wise + Factura E | 1.5-2.5% | 1-2d | Total | Baja | ✓ pero subóptimo a este volumen |
| **Mercury + MEP via broker** | 2-3% | 5-7d | Total | Media | ✓ **volumen justifica el overhead** |
| Deel + ARS direct (cliente lo ofrece) | 2-4% | 2-5d | Total (CAE platform) | Media | ✓ pero costo más alto que MEP |
| USDT via VASP-reg | 2-3% | <1d | Declarable | Media-Alta | ✗ cliente no paga en USDT |
| ❌ Blue dollar cueva | 0-1% | Instant | Cero | Muy Alta | REFUSED |
| ❌ Crypto P2P informal | 0.5-1.5% | Instant | Cero | Muy Alta | REFUSED |

### Recommendation

**Mercury + MEP via broker para este invoice.**

**Confidence: 78%.**
- +20% porque todos los inputs core están verificados
- +15% porque a este volumen ($8K invoice + trayectoria $13K USD/mes) el spread MEP vs oficial ($240-280 USD por invoice) supera claramente el broker overhead
- +10% porque infraestructura está toda lista (Mercury USD activo, SBS habilitado para MEP)
- −8% porque el RI transition timing es mid-Q3 — si MEP via broker se extiende >7 días, el invoice puede caer en período donde tu monotributo ya está siendo recategorizado o transicionando a RI, y la documentación queda en zona gris si el broker hace el trade el día equivocado
- −9% porque Deel está disponible y es operativamente más simple, aunque más caro — el operator podría preferir simplicidad ante RI transition incoming
- **Lo que cerraría el gap a 90%+**: confirmar con tu contador la timing exacta del RI transition trigger y si conviene recibir este invoice en monotributo o esperar al cambio de régimen.

**Headroom impact:** post-invoice cumulative $66K USD = excedés cat I ya. **Recomendación crítica: NO postergues el invoice — el problema no es este invoice puntual, es la trayectoria. Postergar este $8K por 30 días no te baja la trayectoria proyectada al cierre.**

**Próximo paso operacional crítico:** programar reunión con tu contador esta semana para iniciar transición a RI. Trigger objetivo: tu YTD ya supera cat I y proyectás superar K en mid-Q3. Better to plan the transition than have AFIP force it.

### Execution Checklist

1. **[Hoy]** Llamar a tu contador. Agendar reunión esta semana específicamente para RI transition timing.
2. **[Día 0]** Confirmar con el cliente alemán que wire bancario a Mercury es viable (vs Deel). Pasarle datos Mercury (US ABA + account number).
3. **[Día 1]** Emitir Factura E al cliente alemán por $8,000 USD, cotización oficial AFIP del día.
4. **[Día 2-3]** Cliente envía wire $8K USD → Mercury.
5. **[Día 4]** Wire de Mercury → tu cuenta argentina USD (Galicia/Santander/BBVA — la que tengas configurada). Wire fee típico $15-25.
6. **[Día 5-7]** Operación MEP via Grupo SBS: comprar AL30 con USD, vender en ARS. Documentar: comprobantes broker (compra + venta), tipo de cambio MEP del día, costos comisiones.
7. **[Mensual]** Reconciliar: Factura E + wire Mercury statement + Mercury→AR bank statement + broker statements + ARS landing.
8. **[Documentar — carpeta AFIP/2026/Q2/]**: Factura E PDF, Mercury statement, wire confirmation, broker statements MEP buy + sell, contrato firmado.
9. **[Q3 — pendiente reunión contador]** Iniciar formalización RI transition. Costo estimado: $1-2K USD/año en honorarios + IVA filing mensual. Beneficio: eliminás el cap de monotributo y ganás crédito fiscal por insumos.

### Decision Trace

- Mode detected: Routing — invoice específico + payment options + cliente country.
- Lane chosen: Mercury + MEP via broker. Volumen ($8K invoice + $13K/mes trajectory) justifica el broker overhead vs Wise. Spread MEP vs oficial = ~$240-280 USD por invoice = más que el broker fee.
- Confidence 78%: alta intake compliance + infraestructura lista, pero RI transition timing dentro de 60-90 días introduce documentación-uncertainty.
- Crítica más importante NO es la lane — es la trayectoria. Specialist flagea RI transition como acción prioritaria, no como observación tangencial.
- Deel descartado: cliente lo ofrece pero MEP via broker da mejor cost-of-funds y Deel agrega platform-withholding RG 5319/2025 que reduce el net.

---

### audit-pack.md (shadow artifact — guardalo en tu carpeta AFIP/2026/Q2/)

```
FECHA: 2026-05-08
INVOICE: SaaS GmbH (DE), USD $8,000

SIGNALS ANALYZED:
  - Cat monotributo I, YTD facturado ~$58K = 89% del techo
  - Trayectoria proyecta cierre $142-158K USD = forzada salida a RI Q3 2026
  - Cliente alemán B2B SaaS, paga por wire bancario o Deel
  - Infraestructura: Mercury USD activo, Grupo SBS habilitado MEP, Wise activa, Deel configurado
  - IIBB CABA, export-services exempt
  - Factura E aprobada y en uso

ALTERNATIVES CONSIDERED:
  - Wise + Factura E — funciona pero subóptimo a este volumen (~$240 dejados sobre la mesa)
  - Deel + ARS direct — operativamente más simple pero costo más alto + platform withholding
  - USDT via VASP — cliente no ofrece USDT, no aplicable
  - ❌ Blue dollar / crypto informal — REFUSED

DECISION: Mercury + MEP via broker (Grupo SBS)

DECISION RATIONALE:
  Volumen del invoice + trajectory mensual justifica overhead del MEP route. Spread MEP vs oficial
  estimado $240-280 USD por invoice supera el broker fee + wire fee (~$25-90 total). Critical
  flag adyacente: RI transition imminent — Q3 2026.

CONFIDENCE: 78%

FX RATE SNAPSHOT (May 2026 calibration):
  Oficial 1,395 | MEP 1,418 | Wise mid 1,385 | USDT VASP 1,445

DOCUMENTS TO RETAIN:
  - Factura E #N
  - Mercury statement showing $8,000 USD inbound + outbound wire to AR bank
  - Wire confirmation Mercury → cuenta argentina USD
  - Grupo SBS broker statements: AL30 buy in USD + AL30 sell in ARS
  - Contrato firmado con SaaS GmbH
  - Email confirmación payment method del cliente

NEXT REVIEW TRIGGER:
  CRÍTICO — agendar reunión contador esta semana para RI transition. YTD post-invoice
  excede cat I; trayectoria proyecta superar cat K mid-Q3. Mejor planificar la transición
  que tener AFIP forzarla.
```

---

## Example 3 — Federica (Audit Response Mode, ES)

**Lo que Federica pega:**

> Hola, urgente. Hoy me llegó esto a mi correo asociado a CUIT (lo copio como me llegó):
>
> *"Vista — Sr/a contribuyente: se le notifica que en virtud del análisis efectuado sobre las declaraciones juradas del período fiscal 2024 correspondientes al régimen Simplificado para Pequeños Contribuyentes, surgen inconsistencias entre los ingresos declarados y los movimientos de fondos detectados a través de SIRA. Se intima al contribuyente a presentar dentro del plazo de 15 (quince) días hábiles administrativos la siguiente documentación: facturas emitidas, comprobantes de cobro, y conciliación bancaria del período enero-diciembre 2024."*
>
> Soy Federica, copywriter freelance Mendoza, monotributo cat E el 2024. Facturé bastante por Upwork + algunos clientes directos. Estoy hecha bolsa, qué hago? Ayudame a pensar la respuesta.

**Output del specialist:**

### Mode Switch Notice

He detectado señales de notificación AFIP — vista por inconsistencias 2024. **Cambio a modo Audit Response — no voy a recomendar routing hasta que esto esté resuelto.** Vos primero respondés a esta vista, después armamos routing futuro.

### Trigger Identified

- **Tipo**: Vista (comunicación inicial de revisión, NO intimación con monto reclamado todavía).
- **Fundamento**: análisis de inconsistencias entre declaraciones juradas 2024 y movimientos bancarios detectados via SIRA.
- **Período bajo revisión**: enero-diciembre 2024.
- **Plazo**: 15 días hábiles administrativos para responder. Tiempo suficiente para preparar bien — pero no para postponer.
- **Documentación pedida**: facturas emitidas, comprobantes de cobro, conciliación bancaria del período.

**Severity assessment: media-alta.** Es vista (no intimación con monto), o sea AFIP está pidiendo aclaraciones — todavía no afirma evasión. Pero las inconsistencias SIRA son lo que normalmente precede a una intimación si la respuesta es débil o incompleta.

### Documents to Pull (priority-ordered)

1. **Facturas E emitidas durante 2024** (PDFs + records del sistema AFIP). Si hubo Facturas C o B también, todas.
2. **Statements de cuentas bancarias 2024** — todos los bancos donde recibiste fondos. Si tenés Wise, Payoneer, Mercury, Deel — descargá CSVs anuales.
3. **Statements de Upwork 2024** — earnings + withdrawals por mes.
4. **Contratos firmados con clientes directos 2024** (los que tengan documentación de SoW).
5. **Annual return monotributo 2024** — la presentación anual del régimen.
6. **Recategorización history 2024** — si hubo cambios de cat durante el año.
7. **Comprobantes de pagos cuotas mensuales monotributo 2024**.
8. **Si hubo conversiones ARS** — comprobantes de cualquier broker, exchange, casa de cambio que hayas usado.

### Suggested Response Language

Empezá la respuesta formal con esto, ajustá los datos específicos:

**Párrafo 1 (acuse + voluntad cooperación):**

> "Buenos días. En atención a la vista del [fecha], remito documentación respaldatoria correspondiente al período fiscal 2024 bajo el régimen Simplificado para Pequeños Contribuyentes (cat E al inicio del período).

**Párrafo 2 (lista lo que adjuntás):**

> Adjunto: (i) facturas emitidas durante el período (X facturas, monto total $Y), (ii) comprobantes de cobro asociados a cada factura, (iii) extractos bancarios consolidados del período (cuentas A, B, C), (iv) statements de plataformas de pago utilizadas (Upwork, [otras]), y (v) liquidación anual del régimen monotributo 2024 oportunamente presentada.

**Párrafo 3 (factura E + servicios al exterior):**

> El total facturado durante el período corresponde mayoritariamente a servicios prestados a clientes residentes en el exterior, bajo régimen de exportación de servicios (Facturas tipo E), con cotización al tipo de cambio AFIP oficial del día de emisión de cada factura.

**Párrafo 4 (cierre cooperativo):**

> Quedo a disposición para cualquier aclaración adicional que se requiera. Saludos cordiales."

### What NOT to Say

- **NO mencionar** detalles de tu lógica de routing (por qué elegiste Wise vs MEP, por qué USDT en algún momento). AFIP no preguntó eso.
- **NO ofrecer** información de períodos fiscales anteriores ni futuros. Solo 2024.
- **NO admitir** "puede haber habido errores" antes de saber qué errores específicos AFIP está alegando. Esa frase, en un escrito, puede ser usada como confesión.
- **NO firmar nada** que no haya leído tu contador antes. Si no tenés contador, ESTE es el momento de contratar uno (incluso si es por la consulta puntual de esta vista — costo típico $50-150 USD).
- **NO mencionar** voluntad de "cerrar" el caso pagando algo. Si AFIP escala a intimación con monto, el cálculo se hace en ese momento, no preventivo.
- **NO pasar más documentación de la que pidieron**. Pidieron facturas, cobros, conciliación bancaria — eso. Si hay otras cosas que podrían explicar inconsistencias, esperá a que las pregunten.

### Contador / Abogado Trigger

**Contador (sí, ahora):**
- Mejor que la respuesta sea revisada por contador antes de presentarla. Costo $50-150 USD por la consulta + revisión del escrito y la documentación.
- Si no tenés contador habitual, conseguí uno con experiencia en monotributo + servicios al exterior. Buenos canales: referidos del Skool community, freelancer fora argentinos, Reddit r/devsfinanzas.

**Abogado tributarista (sólo si):**
- AFIP escala a intimación con monto reclamado.
- El monto reclamado es sustancial relativo a tu cushion personal.
- Aparece mención de presunción de evasión, dolo fiscal, o defraudación.
- Plazos perentorios menores a 5 días hábiles.

**No es necesario abogado para esta vista todavía.** Si la respuesta es completa y bien documentada, lo más probable es que AFIP cierre el procedimiento sin escalar.

### Decision Trace

- Mode switch detectado: keywords "vista", "inconsistencias", "intima", "plazo", "SIRA", "documentación".
- Severity assessment: media-alta. Es vista (etapa inicial), no intimación con monto, pero las inconsistencias SIRA son trigger que precede a intimaciones formales.
- Contador trigger activado: sí, para revisión de la respuesta antes de presentarla.
- Abogado trigger: NO en este momento, condicional a escalada a intimación con monto.
- Plazo gestionable: 15 días hábiles permite preparar bien sin ahogo.

---

## Example 4 — Juan (Year-End Reconciliation Mode, ES)

**Lo que Juan pega:**

> Soy Juan, dev backend en CABA. Estamos en octubre, cat G monotributo. Facturé $42K USD desde enero — todo a clientes US/UK por Wise + algún Deel. Tengo Wise + Mercury. ¿En qué cat termino el año? ¿Conviene saltar a RI o aguantar el año?

**Output del specialist:**

### YTD Summary

Juan, dev backend en CABA, monotributo **cat G**. Facturado YTD enero-octubre 2026: **~$42,000 USD** (~59.5M ARS @ MEP 1.418). Distribución: Wise (mayoría) + algún Deel. Promedio mensual: ~$4,200 USD/mes.

### Cat Projection

- **Techo cat G actual**: ~62M ARS = ~$43,729 USD @ MEP.
- **YTD a octubre**: ~$42K = **~96% del techo cat G**. Estás al filo.
- **Proyección al cierre 2026** (manteniendo $4.2K/mes): noviembre + diciembre = +$8.4K → **cierre ~$50.4K USD = ~71M ARS = excede cat G por ~9M ARS**.
- **Cat H**: techo ~76M ARS = ~$53,600 USD. Cubrís cómodo.
- **Cat I**: techo ~92M ARS = ~$64,949 USD. Headroom adicional.

**Conclusión cat:** terminás el año en **cat H si recategorizás proactivamente ahora** o cuando llegue agosto 2026 te recategoriza ARCA con multa por sub-cat-ización.

### RI Transition Trigger Analysis

**¿Conviene saltar a RI ahora?**

Cálculo costo-beneficio aproximado:

**Quedarte en monotributo (re-cat a H):**
- Cuota mensual cat H: ~130K ARS (~$92 USD/mes @ MEP)
- IIBB CABA export-services: exempt
- Costo administrativo total mensual: ~$92 USD + 1-2 horas tuyas
- **Total anual: ~$1,100 USD + tiempo administrativo**

**Saltar a RI ahora (faltan 2 meses al cierre fiscal):**
- IVA: 0% para servicios al exterior (régimen exportación), pero hay que filing mensual
- Ganancias: alícuota progresiva 5-35% sobre ganancia neta. Para tu nivel ($50K USD = 17K USD aprox de ganancia neta después de gastos), ronda 9-15%.
- Honorarios contador: $80-150 USD/mes × 2 meses = $160-300 USD
- IIBB CABA: exempt para export-services
- Costo administrativo total Q4: $160-300 USD honorarios + ~4-8 hs/mes tuyas
- **Total Q4 estimado: $400-700 USD + tiempo significativo**

**Resultado:** saltar AHORA por solo 2 meses no compensa. Es overhead administrativo + setup de RI sin beneficio fiscal sustancial dado que ya estás cerca del cierre del año.

**Recomendación: NO saltar a RI todavía. Recategorizar a cat H proactivamente.**

### Recommended Actions Q4

1. **[Esta semana]** Recategorizar proactivamente de cat G a cat H en AFIP. Trámite online (~15 minutos). Te evita la multa por sub-cat-ización en agosto 2026.
2. **[Próximas 2 semanas]** Reconciliá invoicing YTD: contá Facturas E + montos + cotizaciones + Wise/Deel inflows. Confirmá que el match es 1:1 (sin gaps, sin duplicados).
3. **[Antes de fin de año]** Empezá a juntar documentación 2026 para la liquidación anual del régimen — facturas, statements bancarios, contratos.
4. **[Q1 2027]** Si proyectás que 2027 va a estar arriba de $55-60K USD/año (techo cat I), agendá reunión con contador en enero para RI transition antes de que sea forzada.
5. **[Decisión opcional]** Si querés ganar tiempo, el invoicing de noviembre-diciembre podés timear-lo: emitir facturas en diciembre que se cobran en enero significa que los inflows de enero cuentan para 2027, no 2026. Pero **no** retroactivar: emitirlas en 2027 si los servicios fueron prestados en 2026 = problema. Esto es a discutir con contador, no acción unilateral.

### Decision Trace

- Mode detected: Year-End Reconciliation. Strong signals: total YTD facturado, mes octubre (Q4 trigger), pregunta sobre cat de cierre + RI transition.
- Cat projection clara: cierre 2026 = exceso cat G por $7-9K USD. Recategorizar a H necesario.
- RI transition: NO recomendado para Q4 2026. Costo-beneficio no se sostiene a 2 meses del cierre. Reevaluar Q1 2027 según trayectoria.
- Key acción defensiva: recategorización proactiva esta semana evita multa por sub-cat en agosto 2026.

---

## Example 5 — Refusal: Intake Gate Triggered (Spanish-dominant input → Spanish refusal output)

**Lo que pega el usuario:**

> Hola, vivo en Argentina y soy freelance designer. Un cliente del exterior me quiere pagar afuera. Cuál es la mejor manera de cobrar?

**Output del specialist:**

Antes de routing necesito 4 de estos 5 inputs:

1. **Cat monotributo actual** (A-K, RI, o todavía no estás inscripto)
2. **Volumen USD/mes últimos 3 meses** (un rango está bien, ej: "$2-4K/mes")
3. **Este invoice**: monto en USD + país del cliente + opciones de pago que te ofrece (Wise, wire, Deel, USDT, etc.)
4. **Jurisdicción IIBB** (CABA / PBA / provincia interior / N/A si sos export-services puro)
5. **Infraestructura bancaria**: Wise sí/no, Mercury sí/no, broker sí/no, exchange crypto registrado en CNV sí/no

**Tengo:** freelance designer en Argentina ✓ (parcial — falta provincia y cat); cliente externo que va a pagar en USD ✓ (parcial — falta monto + país + opciones)

**Falta:** inputs #1, #2, #3 (monto + país + opciones), #4 (provincia específica), #5

Si querés un best-effort con `⚠ guessed` markers en cada supuesto, decímelo explícito — pero la respuesta estándar con este nivel de info sería inútil. Mandame los faltantes en un mensaje y arranco.

## Trazabilidad de la Decisión

- Mode que hubiera aplicado: Routing
- Inputs recibidos: 0 de 5 fully specified (2 partials: #3 country-only, #5 freelance-only)
- Inputs missing: #1, #2, #3 (specifics), #4 (specifics), #5 (specifics)
- Output language: español por input español-dominante ("freelance designer" como loanword no shifteao el dominio)
- Override available: sí, on explicit request

### Variant — same scenario but truly mixed-language input → English default

**Input alternativo:**

> Hi — I'm freelance from BA Argentina. Tengo un cliente del exterior que wants to pay me en dollars. ¿What's the best way para cobrar? Need compliant route.

**Output del specialist** (heavy mixed-language input → EN default):

Before routing I need 4 of these 5 inputs (defaulting to English; switch to Spanish on request):

1. **Monotributo category** (A-K, RI, or unregistered)
2. **USD volume / month, last 3 months** (a range is fine, e.g., "$2-4K/mo")
3. **This invoice**: USD amount + client country + payment options the client offers (Wise, wire, Deel, USDT, etc.)
4. **IIBB jurisdiction** (CABA / PBA / interior province / N/A if export-services only)
5. **Banking infrastructure**: Wise yes/no, Mercury yes/no, broker yes/no, CNV-registered crypto exchange yes/no

**Have:** freelance in Buenos Aires ✓ (partial — need province + cat); foreign client paying USD ✓ (partial — need amount, country, payment options); compliance-first preference ✓ (signal, not an input)

**Missing:** #1, #2, #3 (specifics), #4 (specifics), #5

If you want a best-effort guess with `⚠ guessed` markers on every assumption, say so explicitly — but the standard answer with this little context would be useless. Send me the missing inputs in one message and I'll produce the routing decision.

## Decision Trace

- Mode that would have applied: Routing
- Inputs received: 0 of 5 fully specified (3 partials: #4 region-only, #5 freelance-only, plus a compliance-preference signal)
- Inputs missing: #1, #2, #3 (specifics), #4 (specifics), #5 (specifics)
- Output language: English default (mixed-language input with no clear dominant — Spanish and English alternating clauses)
- Override available: yes, on explicit request
