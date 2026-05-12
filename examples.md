# Examples

Five worked examples covering all four operating modes plus the refusal protocol. Each example shows what the operator pastes (input) and exactly what the specialist responds (output). Outputs render here the same way they render in a Claude project chat — `### Section Name` headers map to the `## Section Name` headers specified in `rules.md` (one nesting level deeper because they're inside this examples file).

| # | Mode | Persona | Language | Highlights |
|---|------|---------|----------|------------|
| 1 | Routing | **Marina** — UX designer cat F, $4K from US client | English | Confidence 92%, Wise + Factura E, full happy path |
| 2 | Routing | **Diego** — AI consultant cat I → K, $8K from EU client | Español | Confidence 72%, Mercury + MEP o Deel (margen modesto), RI transition flag |
| 3 | Audit Response | **Federica** — copywriter, recibió vista AFIP por 2024 | Español | Mode switch announced, defensive playbook, contador trigger |
| 4 | Year-End | **Juan** — dev cat G, octubre, $42K YTD | Español | Cat projection, ventana recat Feb 2027, RI transition Q1 2027 |
| 5 | Refusal | Vague intake, 4-5 of 5 inputs missing/weak | ES (Spanish-dominant input) + variant for mixed → EN default | Intake gate triggered, 5-input list, Decision Trace, override option |

---

## Example 1 — Marina (Routing Mode, EN flagship)

> **Persona deep-dive:** [`identity-examples/marina.md`](./identity-examples/marina.md). Voice pillars, vocabulary, content themes, and decision posture for the Marina profile (cat F, single anchor US client, Wise default, CABA jurisdiction).

**What Marina pastes:**

> Hi — I'm Marina, freelance UX designer based in Buenos Aires. I'm on monotributo cat F, billing about $3.5K USD/month for the last 4 months to one US client (a Series-A SaaS).
>
> Got a new invoice incoming this week: $4,000 USD from a different US client — a B2B fintech I just onboarded. Client offered to pay via Wise or USDT directly to my Lemon wallet. I have a Wise account active and a Mercury account I opened last quarter but haven't used yet for invoicing. IIBB CABA, but I'm export-services so I think that's exempt. Factura E is set up and approved in AFIP — I've emitted maybe 8 in the last 12 months.
>
> Should I just take Wise like always or is there a smarter move here?

**Specialist output:**

### Situation

Marina, UX designer in CABA, monotributo (Argentine simplified tax regime) cat F. YTD trajectory: ~$3.5K USD/month × 4 months = ~$14K USD invoiced Q1 + early Q2 2026 (~19,800,000 ARS at MEP 1,418). New incoming: **$4,000 USD** from a US fintech client. Payment options offered: Wise transfer or USDT to her Lemon wallet. Infrastructure: Wise active, Mercury opened (unused for invoicing yet), Lemon wallet active (VASP-registered ✓). IIBB (provincial gross-income tax) CABA + export-services = exempt. Factura E (export invoice) approved in AFIP, ~8 issued in the last 12 months.

### Constraints Analysis

- **Cat F headroom**: annual ceiling 38,642,048 ARS = ~$27,251 USD at MEP 1,418. YTD invoiced ~$14K = ~51% of ceiling. This invoice ($4K) brings cumulative to ~$18K = ~66% of ceiling. Remaining headroom: ~$9,300 USD for the rest of 2026.
- **Next recategorización (re-categorization)**: August 2026. If Marina sustains $3.5-4K USD/month, she closes the year at ~$32-37K USD invoiced — over cat F ($27,251), well into cat G ($32,589) and possibly cat H ($49,446). The August recategorización will absorb part of that with the IPC adjustment, but proactive recat to G is already advisable given current trajectory.
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
- +5% because cat F runway is still positive (66% utilized post-invoice; ~$9.3K USD remaining before forced jump)
- −8% because Mercury account exists but unused for invoicing — minor uncertainty about whether wire-from-US is configured if Wise becomes unavailable
- −5% because trajectory at $3.5-4K/mo already projects closing the year above cat F ceiling — the lane choice is right but cat-management urgency is higher than a clean cat F case

**Headroom impact:** post-invoice, cat F ~66% utilized YTD. **Next-month flag fires now:** at current $3.5-4K/mo trajectory, Marina crosses 70% of cat F next invoice — proactive recategorización to G is already advisable, do not wait for August's official window. Recategorizing to G keeps headroom up to $32,589 USD = ~14.6K USD additional runway.

USDT via Lemon is operationally available but not recommended here — adds reporting friction (USDT valuation at official AFIP rate at the moment of receipt + VASP statement reconciliation) without cost advantage at this volume. Reserve the USDT lane for clients who insist on crypto payment or for invoices where Wise availability is uncertain.

### Execution Checklist

1. **[Day 0 — today]** Confirm with the new fintech client that Wise transfer is acceptable. Send them Wise account details (USD multi-currency, routing number for ACH).
2. **[Day 1]** Issue Factura E #N to the new client's legal entity at the official AFIP exchange rate of the issuance day. Document the exchange rate quote on the invoice.
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
  - Monotributo cat F (ceiling 38,642,048 ARS / ~$27,251 USD @ MEP 1,418), headroom ~$9,300 USD remaining in 2026
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
  YTD cumulative is already at 66% of cat F ceiling post-invoice; one more
  invoice at current pace crosses 70%. Recategorize to cat G proactively
  this month — do not wait for Aug 2026 official window.
```

---

## Example 2 — Diego (Routing Mode, ES)

> **Persona deep-dive:** [`identity-examples/diego.md`](./identity-examples/diego.md). Voice pillars, vocabulary, content themes, and decision posture for the Diego profile (cat I → K, multi-client US+EU, Mercury+MEP default, CABA jurisdiction, RI transition imminent Q3 2026).

**Lo que Diego pega:**

> Soy Diego, AI consultant en CABA. Cat I monotributo, llevo facturados ~$58K USD desde enero — clientes US y un par europeos. Me llegó un nuevo invoice de $8K USD de un cliente alemán (B2B SaaS, fintech regulada) que paga por wire o por Deel.
>
> Tengo cuenta Mercury con saldo USD activo, broker Grupo SBS habilitado para MEP, Wise activa, Deel configurado por el cliente alemán (CAE compliant). Estoy en CABA, export-services. Factura E aprobada hace tiempo.
>
> Estoy preocupado porque cat I aprieta — ¿debería tomar este invoice ya o postergarlo? ¿Y si lo tomo, qué lane uso?

**Output del specialist:**

### Situación

Diego, AI consultant en CABA, monotributo **cat I**. YTD facturado ~$58K USD desde enero (~82.2M ARS @ MEP). Nuevo invoice incoming: **$8,000 USD** de cliente alemán B2B SaaS. Payment options: wire bancario o Deel. Infraestructura: Mercury (saldo USD activo), Grupo SBS broker (MEP habilitado), Wise activa, Deel configurado por el cliente. IIBB CABA + export-services = exempt. Factura E aprobada y en uso desde hace tiempo.

### Análisis de Constraints

- **Headroom monotributo cat I**: límite real 78.479M ARS = **~$55,345 USD @ MEP 1.418**. YTD facturado ~$58K = **~105% del techo cat I — ya estás afuera**. Este invoice ($8K) lleva el cumulative a ~$66K = **~119% del techo cat I**, te ubica adentro de cat J ($63,381) y cerca del techo cat K.
- **Cat J**: techo 89.872M ARS = ~$63,381 USD. Post-invoice $66K = ~104% de cat J. **Cruzaste cat J también.**
- **Cat K (techo absoluto)**: 108.357M ARS = ~$76,415 USD. Post-invoice $66K = ~86% de cat K. Headroom hasta cat K: ~$10.4K USD = ~14.7M ARS.
- **Trayectoria proyectada**: facturando ~$13K USD/mes promedio (los $58K en 4-5 meses), el resto del año proyecta otros $84-100K → cierre $142-158K USD = **~186-207% del techo cat K. Salida forzada a RI inevitable Q3 2026.**
- **Próxima recategorización**: agosto 2026. Va a confirmar lo que ya es matemático: salida a RI.
- **IIBB**: export-services CABA exempt, sin cambios.
- **Factura E**: setup confirmed.
- **VASP status**: no aplica este invoice (cliente paga wire o Deel, no USDT).

### Opciones de Routing

| Opción | Costo all-in | Velocidad | Visibilidad fiscal | Riesgo de auditoría | Señal Confidence-OK |
|--------|-------------|-----------|--------------------|---------------------|---------------------|
| Wise + Factura E | 1.5-2.5% | 1-2d | Total | Baja | ✓ pero subóptimo a este volumen |
| **Mercury + MEP via broker** | 2-3% | 5-7d | Total | Media | ✓ **volumen justifica el overhead** |
| Deel + ARS direct (cliente lo ofrece) | 2-4% | 2-5d | Total (CAE platform) | Media | ✓ pero costo más alto que MEP |
| USDT via VASP-reg | 2-3% | <1d | Declarable | Media-Alta | ✗ cliente no paga en USDT |
| ❌ Blue dollar cueva | 0-1% | Instant | Cero | Muy Alta | REFUSED |
| ❌ Crypto P2P informal | 0.5-1.5% | Instant | Cero | Muy Alta | REFUSED |

### Recomendación

**Mercury + MEP via broker es la lane primaria. Deel queda como alternativa defendible si Diego prioriza simplicidad operacional pre-RI transition.**

El trade-off real: Mercury+MEP captura ~$85-95 USD netos por factura sobre Wise (después de wire fee + broker fee 0.5%), pero suma 5-7 días de procesamiento + coordinación con SBS + documentación broker. Deel cuesta más en bruto (~$80-160 USD adicionales en esta factura vs MEP) pero elimina la coordinación con broker en pleno período pre-RI transition. Si Diego ya tiene flujo MEP probado de facturas anteriores, la lane primaria se sostiene. Si no, Deel le da certeza de timing mientras se concentra en armar el contador con experiencia RI.

**Confidence: 72%.**
- +20% porque todos los inputs core están verificados
- +10% porque infraestructura está toda lista (Mercury USD activo, SBS habilitado para MEP)
- +8% porque el operator tiene flujo MEP probado de facturas anteriores y la lane primaria es operacionalmente conocida
- −8% porque el RI transition timing es mid-Q3 — si MEP via broker se extiende >7 días, el invoice puede caer en período donde tu monotributo ya está siendo recategorizado o transicionando a RI, y la documentación queda en zona gris si el broker hace el trade el día equivocado
- −9% porque el margen MEP-vs-Wise neto post-fees ($85-95/factura) es modesto: justifica ofrecer Deel como alternativa real, no descartarla con un parágrafo
- −9% porque el contador actual de Diego NO tiene experiencia RI para AI consulting (ver `identity-examples/diego.md` § Background): la documentation playbook MEP via SBS queda mid-engagement sin sparring contable adecuado mientras la migración a un contador RI-experto está pendiente
- **Lo que cerraría el gap a 90%+**: confirmar con tu contador (preferentemente uno con experiencia RI para AI consulting que vas a tener que conseguir esta semana) la timing exacta del RI transition trigger, y revalidar spread MEP del día de operación contra fuente live ([rueda.live](https://rueda.live/en)) antes de ejecutar el trade.

**Headroom impact:** post-invoice cumulative $66K USD ya excede cat I y cat J — estás dentro de cat K con ~14% de runway antes del techo absoluto del régimen. **Recomendación crítica: NO postergues el invoice — el problema no es este invoice puntual, es la trayectoria. Postergar este $8K por 30 días no baja la trayectoria proyectada al cierre.**

**Próximo paso operacional crítico:** programar reunión con tu contador esta semana para iniciar transición a RI. Trigger objetivo: tu YTD ya supera cat I y cat J, y proyectás superar K en Q3 2026. Mejor planificar la transición que tenerla forzada por AFIP.

### Checklist de Ejecución

1. **[Hoy]** Llamar a tu contador. Agendar reunión esta semana específicamente para RI transition timing.
2. **[Día 0]** Confirmar con el cliente alemán que wire bancario a Mercury es viable (vs Deel). Pasarle datos Mercury (US ABA + account number).
3. **[Día 1]** Emitir Factura E al cliente alemán por $8,000 USD, cotización oficial AFIP del día.
4. **[Día 2-3]** Cliente envía wire $8K USD → Mercury.
5. **[Día 4]** Wire de Mercury → tu cuenta argentina USD (Galicia/Santander/BBVA — la que tengas configurada). Wire fee típico $15-25.
6. **[Día 5-7]** Operación MEP via Grupo SBS: comprar AL30 con USD, vender en ARS. Documentar: comprobantes broker (compra + venta), tipo de cambio MEP del día, costos comisiones.
7. **[Mensual]** Reconciliar: Factura E + wire Mercury statement + Mercury→AR bank statement + broker statements + ARS landing.
8. **[Documentar — carpeta AFIP/2026/Q2/]**: Factura E PDF, Mercury statement, wire confirmation, broker statements MEP buy + sell, contrato firmado.
9. **[Q3 — pendiente reunión contador]** Iniciar formalización RI transition. Costo estimado: $1-2K USD/año en honorarios + IVA filing mensual. Beneficio: eliminás el cap de monotributo y ganás crédito fiscal por insumos.

### Trazabilidad de la Decisión

- Modo detectado: Routing — factura específica + opciones de pago + país del cliente.
- Lane elegida: Mercury + MEP vía broker como lane primaria, Deel como alternativa defendible. Volumen ($8K factura + $13K/mes trayectoria) sostiene el overhead del broker vs Wise pero el margen es ajustado. Spread MEP vs Wise = ~$150 USD netos por factura antes de fricción; después de wire fee ($15-25) + broker fee 0.5% (~$40) el neto capturado es $85-95. La diferencia bruta con Deel es ~$80-160 USD: cobertura razonable a cambio de certeza de timing + simplicidad pre-RI.
- Confianza 72%: alto cumplimiento de intake gate + infraestructura lista, pero margen MEP modesto + timing de RI transition dentro de 60-90 días + gap de contador introducen incertidumbre documental no trivial.
- La crítica más importante NO es la lane — es la trayectoria. El specialist flagea RI transition como acción prioritaria, no como observación tangencial.
- Flag crítico de contexto: Diego cita en `identity-examples/diego.md` § Background que su contador actual NO tiene experiencia en RI para AI consulting. Esta recomendación asume que Diego inicia migración a contador con experiencia RI en paralelo al trabajo de esta factura, dentro de las próximas 2-4 semanas. Si no lo hace, el playbook de documentación MEP vía SBS queda mid-engagement sin sparring contable adecuado, lo cual aumenta el riesgo operacional y refuerza la viabilidad de Deel como ruta menos compleja.
- Deel NO descartado: ofrecido como alternativa real con trade-off explícito (más caro en bruto $80-160 USD, pero menos coordinación + certeza de timing + no requiere documentación MEP vía broker). Cualquier decisión final entre las dos lanes pasa por el contador.

---

### audit-pack.md (shadow artifact — guardalo en tu carpeta AFIP/2026/Q2/)

```
FECHA: 2026-05-08
FACTURA: SaaS GmbH (DE), USD 8.000

SEÑALES ANALIZADAS:
  - Cat monotributo I (techo 78.479M ARS / ~$55.345 USD), YTD facturado ~$58K = 105% del techo — ya excedido
  - Post-factura $66K = 119% cat I, 104% cat J, 86% cat K
  - Trayectoria proyecta cierre $142-158K USD = forzada salida a RI Q3 2026
  - Cliente alemán B2B SaaS, paga por transferencia bancaria o Deel
  - Infraestructura: Mercury USD activo, Grupo SBS habilitado MEP, Wise activa, Deel configurado
  - IIBB CABA, export-services exento
  - Factura E aprobada y en uso

ALTERNATIVAS CONSIDERADAS:
  - Wise + Factura E — funciona, subóptimo a este volumen (~$85-95 netos dejados sobre la mesa por factura después de fees)
  - Deel + ARS direct — alternativa defendible: ~$80-160 USD más caro en bruto pero
    elimina coordinación con broker + da certeza de timing pre-RI transition
  - USDT vía VASP — cliente no ofrece USDT, no aplicable
  - ❌ Blue dollar / crypto informal — RECHAZADO

DECISIÓN: Mercury + MEP vía broker (Grupo SBS) como primary, Deel como alternativa.

FUNDAMENTO DE LA DECISIÓN:
  Volumen de la factura + trayectoria mensual sostiene el overhead del MEP route con margen ajustado.
  Spread MEP vs Wise ~$150 USD por factura antes de fricción; neto post-fees (wire $15-25 +
  broker 0.5% ~$40) = $85-95 capturados. Deel cuesta ~$80-160 más en bruto pero compra
  certeza de timing + reduce documentación pre-RI. La decisión final entre las dos pasa por
  contador con experiencia RI (que Diego todavía NO tiene — gap a cerrar esta semana).
  Flag crítico adyacente: RI transition inminente — Q3 2026.

CONFIANZA: 72%

COTIZACIÓN AL MOMENTO (calibración mayo 2026):
  Oficial 1.395 | MEP 1.418 | Wise mid 1.385 | USDT VASP 1.445

DOCUMENTOS A RETENER:
  - Factura E #N
  - Mercury statement mostrando $8.000 USD entrada + salida wire a banco AR
  - Confirmación wire Mercury → cuenta argentina USD
  - Grupo SBS broker statements: compra AL30 en USD + venta AL30 en ARS
  - Contrato firmado con SaaS GmbH
  - Email confirmación método de pago del cliente

CRITERIO DE PRÓXIMA REVISIÓN:
  CRÍTICO — agendar reunión con contador esta semana para RI transition. YTD post-factura
  excede cat I y cat J; trayectoria proyecta superar cat K en Q3 2026. Mejor planificar
  la transición que tenerla forzada por AFIP.
```

---

## Example 3 — Federica (Audit Response Mode, ES)

> **Persona deep-dive:** [`identity-examples/federica.md`](./identity-examples/federica.md). Voice pillars, vocabulary, content themes, and decision posture for the Federica profile (copywriter freelance Mendoza, cat E 2024, in-the-middle-of vista AFIP por inconsistencias RG 3421 + SITER, contador-first posture).

**Lo que Federica pega:**

> Hola, urgente. Hoy me llegó esto a mi correo asociado a CUIT (lo copio como me llegó):
>
> *"Vista — Sr/a contribuyente: se le notifica que en virtud del análisis efectuado sobre las declaraciones juradas del período fiscal 2024 correspondientes al régimen Simplificado para Pequeños Contribuyentes, surgen inconsistencias entre los ingresos declarados y los movimientos de fondos informados a través del régimen informativo de cuentas bancarias (RG 3421) y del Sistema Informativo de Transacciones Económicas Relevantes (SITER). Se intima al contribuyente a presentar dentro del plazo de 15 (quince) días hábiles administrativos la siguiente documentación: facturas emitidas, comprobantes de cobro, y conciliación bancaria del período enero-diciembre 2024."*
>
> Soy Federica, copywriter freelance Mendoza, monotributo cat E el 2024. Facturé bastante por Upwork + algunos clientes directos. Estoy hecha bolsa, qué hago? Ayudame a pensar la respuesta.

**Output del specialist:**

### Cambio de Modo

He detectado señales de notificación AFIP — vista por inconsistencias 2024. **Cambio a modo Audit Response — no voy a recomendar routing hasta que esto esté resuelto.** Vos primero respondés a esta vista, después armamos routing futuro.

### Trigger Identificado

- **Tipo**: Vista (comunicación inicial de revisión, NO intimación con monto reclamado todavía).
- **Fundamento**: análisis de inconsistencias entre declaraciones juradas 2024 y movimientos bancarios informados via RG 3421 (cuentas bancarias) + SITER (operaciones financieras relevantes).
- **Período bajo revisión**: enero-diciembre 2024.
- **Plazo**: 15 días hábiles administrativos para responder. Tiempo suficiente para preparar bien — pero no para postponer.
- **Documentación pedida**: facturas emitidas, comprobantes de cobro, conciliación bancaria del período.

**Severity assessment: media-alta.** Es vista (no intimación con monto), o sea AFIP está pidiendo aclaraciones — todavía no afirma evasión. Pero las inconsistencias detectadas via cross-check RG 3421 + SITER son lo que normalmente precede a una intimación si la respuesta es débil o incompleta.

### Hipótesis de causa probable (Upwork-flow mismatch)

Federica mencionó que "facturé bastante por Upwork + algunos clientes directos". El pattern de cross-check más común para ese perfil es Upwork-primary mismatch: Factura E al cliente final que la contrató en la plataforma vs depósitos bancarios con remitente Upwork (la plataforma actúa como agente de pago intermediario, no el cliente directo). Detalle completo de los 3 patterns de mismatch típicos por perfil operativo en [`reference/audit-response-playbook.md`](./reference/audit-response-playbook.md) § Cross-check mismatch patterns típicos.

**Cómo se trabaja en la respuesta (sin admitir):**

- NO se admite "emití mal las Facturas E". Esa frase, en un escrito, es confesión.
- SÍ se documenta el flujo operativo: contratos con clientes finales (en Upwork), Facturas E al cliente final, statements Upwork con earnings + fees + withholdings, statements bancarios con depósitos remitidos por Upwork. La narrativa es "operé via plataforma intermediaria que actúa como agente de pago del cliente final."
- Si el contador detecta que efectivamente hay delta neto-vs-bruto no declarado, esa decisión la toma el contador con vos (regularización voluntaria con menos multa, vs esperar intimación con monto), no se adelanta en el descargo a la vista.

**Si esta hipótesis NO matchea el caso real de Federica** (por ejemplo, todos los clientes fueron directos sin Upwork, o la inconsistencia es por otro motivo), la documentación que se junta abajo igual cubre el caso — pero el ángulo del escrito cambia. La pregunta operativa para el contador en la primera reunión: ¿de dónde sale el delta que ARCA computó, y a qué pattern de mismatch corresponde?

### Documentos a Recopilar (orden de prioridad)

1. **Facturas E emitidas durante 2024** (PDFs + records del sistema AFIP). Si hubo Facturas C o B también, todas.
2. **Statements de cuentas bancarias 2024** — todos los bancos donde recibiste fondos. Si tenés Wise, Payoneer, Mercury, Deel — descargá CSVs anuales.
3. **Statements de Upwork 2024** — earnings + withdrawals por mes.
4. **Contratos firmados con clientes directos 2024** (los que tengan documentación de SoW).
5. **Annual return monotributo 2024** — la presentación anual del régimen.
6. **Recategorización history 2024** — si hubo cambios de cat durante el año.
7. **Comprobantes de pagos cuotas mensuales monotributo 2024**.
8. **Si hubo conversiones ARS** — comprobantes de cualquier broker, exchange, casa de cambio que hayas usado.

### Lenguaje de Respuesta Sugerido

Empezá la respuesta formal con esto, ajustá los datos específicos:

**Párrafo 1 (acuse + voluntad cooperación):**

> "Buenos días. En atención a la vista del [fecha], remito documentación respaldatoria correspondiente al período fiscal 2024 bajo el régimen Simplificado para Pequeños Contribuyentes (cat E al inicio del período).

**Párrafo 2 (lista lo que adjuntás):**

> Adjunto: (i) facturas emitidas durante el período (X facturas, monto total $Y), (ii) comprobantes de cobro asociados a cada factura, (iii) extractos bancarios consolidados del período (cuentas A, B, C), (iv) statements de plataformas de pago utilizadas (Upwork, [otras]), y (v) liquidación anual del régimen monotributo 2024 oportunamente presentada.

**Párrafo 3 (factura E + servicios al exterior):**

> El total facturado durante el período corresponde mayoritariamente a servicios prestados a clientes residentes en el exterior, bajo régimen de exportación de servicios (Facturas tipo E), con cotización al tipo de cambio AFIP oficial del día de emisión de cada factura.

**Párrafo 4 (cierre cooperativo):**

> Quedo a disposición para cualquier aclaración adicional que se requiera. Saludos cordiales."

### Lo Que NO Hay Que Decir

- **NO mencionar** detalles de tu lógica de routing (por qué elegiste Wise vs MEP, por qué USDT en algún momento). AFIP no preguntó eso.
- **NO ofrecer** información de períodos fiscales anteriores ni futuros. Solo 2024.
- **NO admitir** "puede haber habido errores" antes de saber qué errores específicos AFIP está alegando. Esa frase, en un escrito, puede ser usada como confesión.
- **NO firmar nada** que no haya leído tu contador antes. Si no tenés contador, ESTE es el momento de contratar uno (incluso si es por la consulta puntual de esta vista — costo típico $50-150 USD).
- **NO mencionar** voluntad de "cerrar" el caso pagando algo. Si AFIP escala a intimación con monto, el cálculo se hace en ese momento, no preventivo.
- **NO pasar más documentación de la que pidieron**. Pidieron facturas, cobros, conciliación bancaria — eso. Si hay otras cosas que podrían explicar inconsistencias, esperá a que las pregunten.

### Trigger Contador / Abogado

**Contador (sí, ahora):**
- Mejor que la respuesta sea revisada por contador antes de presentarla. Costo $50-150 USD por la consulta + revisión del escrito y la documentación.
- Si no tenés contador habitual, conseguí uno con experiencia en monotributo + servicios al exterior. Buenos canales: referidos del Skool community, freelancer fora argentinos, Reddit r/devsfinanzas.

**Abogado tributarista (sólo si):**
- AFIP escala a intimación con monto reclamado.
- El monto reclamado es sustancial relativo a tu colchón financiero personal.
- Aparece mención de presunción de evasión, dolo fiscal, o defraudación.
- Plazos perentorios menores a 5 días hábiles.

**No es necesario abogado para esta vista todavía.** Si la respuesta es completa y bien documentada, lo más probable es que AFIP cierre el procedimiento sin escalar.

### Trazabilidad de la Decisión

- Mode switch detectado: keywords "vista", "inconsistencias", "intima", "plazo", "régimen informativo", "SITER", "documentación".
- Severity assessment: media-alta. Es vista (etapa inicial), no intimación con monto, pero las inconsistencias detectadas via cross-check (RG 3421 + SITER) son trigger que precede a intimaciones formales.
- Contador trigger activado: sí, para revisión de la respuesta antes de presentarla.
- Abogado trigger: NO en este momento, condicional a escalada a intimación con monto.
- Plazo gestionable: 15 días hábiles permite preparar bien sin ahogo.

---

## Example 4 — Juan (Year-End Reconciliation Mode, ES)

**Lo que Juan pega:**

> Soy Juan, dev backend en CABA. Estamos en octubre, cat G monotributo. Facturé $42K USD desde enero — todo a clientes US/UK por Wise + algún Deel. Tengo Wise + Mercury. ¿En qué cat termino el año? ¿Conviene saltar a RI o aguantar el año?

**Output del specialist:**

### Resumen YTD

Juan, dev backend en CABA, monotributo **cat G**. Facturado YTD enero-octubre 2026: **~$42.000 USD (USD 42,000)** (~59.500.000 ARS @ MEP 1.418). Distribución: Wise (mayoría) + algún Deel. Promedio mensual: ~$4.200 USD/mes (USD 4,200).

### Proyección de Cat

- **Techo cat G actual**: 46.211.109 ARS = ~$32.589 USD (USD 32,589) @ MEP 1.418.
- **YTD a octubre**: ~$42K = **~129% del techo cat G — ya estás afuera de cat G**. La ventana de recategorización oficial de agosto 2026 ya pasó. Si en agosto no recategorizaste proactivamente, ARCA puede aplicar penalización por sub-categorización de los meses excedidos retroactivamente; conviene regularizar AHORA (trámite proactivo fuera de ventana es permitido) y no esperar la próxima ventana forzada de febrero 2027.
- **Proyección al cierre 2026** (manteniendo $4.200/mes): noviembre + diciembre = +$8.400 → **cierre ~$50.400 USD (USD 50,400) = ~71.500.000 ARS**. Eso excede cat H (70.113.407 ARS = ~$49.446 USD / USD 49,446) y se ubica dentro de cat I (78.479.212 ARS = ~$55.345 USD / USD 55,345).
- **Cat H**: techo 70.113.407 ARS = ~$49.446 USD (USD 49,446). Tu cierre proyectado lo supera por ~$1.000 USD.
- **Cat I**: techo 78.479.212 ARS = ~$55.345 USD (USD 55,345). Tu cierre proyectado deja ~$5.000 USD de headroom.

**Conclusión cat:** terminás el año en **cat I si recategorizás proactivamente ahora**. Cat H probablemente no alcance — tu trayectoria proyectada cruza el techo cat H en diciembre. Si esperás a la ventana forzada de febrero 2027, ARCA va a recategorizar retroactivamente desde el mes del exceso (junio-julio 2026 con tu trayectoria) y aplicar penalización por los meses sub-cat — práctica AR standard sin porcentaje único por RG; el contador la calcula caso a caso según intereses + cuotas no abonadas en la cat correcta.

### Análisis Trigger Transición a RI

**¿Conviene saltar a RI ahora?**

Cálculo costo-beneficio aproximado:

**Quedarte en monotributo (re-cat a I, dado que la proyección de cierre lo justifica):**
- Cuota mensual cat I servicios: ~824.802 ARS (~$582 USD/mes @ MEP 1.418)
- IIBB CABA export-services: exento
- Costo administrativo total mensual: ~$582 USD + 1-2 horas tuyas
- **Total anual proyectado (asumiendo cat I los 12 meses): ~$7.000 USD (USD 7,000) + tiempo administrativo**
- Pero por los 2 meses que quedan: ~$1.165 USD (USD 1,165) adicionales (Nov + Dic)

**Saltar a RI ahora (faltan 2 meses al cierre fiscal):**
- IVA: 0% para servicios al exterior (régimen exportación), pero hay que filing mensual
- Ganancias: alícuota progresiva 5-35% sobre ganancia neta. Para tu nivel (~$50.400 USD facturado, ~$17.000 USD de ganancia neta después de gastos), ronda 9-15%.
- Honorarios contador: $80-150 USD/mes × 2 meses = $160-300 USD
- IIBB CABA: exento para export-services
- Costo administrativo total Q4: $160-300 USD honorarios + ~4-8 hs/mes tuyas
- **Total Q4 estimado: $400-700 USD + tiempo significativo**

**Resultado:** la cuota cat I por 2 meses (~$1.165 USD / USD 1,165) ya supera el setup RI Q4 ($400-700 USD). El cálculo se invierte respecto al caso "cat H vs RI" — para cat I, RI puede ser **más barato** los últimos 2 meses, especialmente si ya estás proyectando RI inevitable en 2027.

**Recomendación matizada:** dos caminos defensibles. (a) Recategorizar a cat I ahora y saltar a RI en enero 2027 con tiempo de setup. (b) Evaluar setup RI inmediato si tu pipeline 2027 ya proyecta >$60K USD/año (techo cat I), porque ahorrás multas + el setup ya es necesario. Decisión final: con tu contador esta semana.

### Acciones Recomendadas Q4

1. **[Esta semana]** Reunión con contador. La decisión cat I vs RI inmediato no es trivial — requiere proyectar pipeline 2027 contra costo administrativo RI vs cuota cat I + tiempo. Ese cálculo es del contador, no del specialist.
2. **[Esta semana, en paralelo]** Recategorizar proactivamente al menos a cat H en AFIP (trámite online ~15 minutos) para no quedar mal-categorizado mientras se resuelve la decisión RI. Tu YTD ya supera cat G — quedarte en cat G es flag inmediato.
3. **[Próximas 2 semanas]** Reconciliá invoicing YTD: contá Facturas E + montos + cotizaciones + Wise/Deel inflows. Confirmá que el match es 1:1 (sin gaps, sin duplicados).
4. **[Antes de fin de año]** Empezá a juntar documentación 2026 para la liquidación anual del régimen — facturas, statements bancarios, contratos.
5. **[Q1 2027]** Si la decisión Q4 fue quedarte en monotributo, en enero re-evaluar RI transition con tu contador antes de la ventana de recategorización forzada de febrero 2027 — y proyectar si en agosto 2027 te vas a llevar otra recat automática a J o K, lo cual acelera la urgencia del salto.
6. **[Decisión opcional]** Si querés ganar tiempo, el invoicing de noviembre-diciembre podés timear-lo: emitir facturas en diciembre que se cobran en enero significa que los inflows de enero cuentan para 2027, no 2026. Pero **no** retroactivar: emitirlas en 2027 si los servicios fueron prestados en 2026 = problema. Esto es a discutir con contador, no acción unilateral.

### Trazabilidad de la Decisión

- Modo detectado: Year-End Reconciliation. Señales fuertes: total YTD facturado, mes octubre (trigger Q4), pregunta sobre cat de cierre + RI transition.
- Cat projection clara: YTD ya excede cat G (estás 29% arriba); cierre 2026 proyectado se ubica dentro de cat I. Recategorizar al menos a H esta semana es defensa básica.
- RI transition: matizado. La cuota cat I los últimos 2 meses ($1.165 USD) ronda o supera el setup RI Q4 ($400-700 USD). Decisión final del contador, no recomendación unilateral del specialist.
- Key acción defensiva: recategorización proactiva esta semana (mínimo a H) evita flag inmediato; reunión contador esta semana para resolver cat I vs RI.

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

### Trazabilidad de la Decisión

- Modo que hubiera aplicado: Routing
- Inputs recibidos: 0 de 5 totalmente especificados (2 parciales: #3 con "cliente externo paga USD" pero sin monto/país/opciones específicas; #4 sin provincia específica más allá de "Argentina")
- Inputs faltantes: #1 (cat), #2 (volumen mensual), #3 (monto + país + opciones), #4 (provincia/jurisdicción IIBB específica), #5 (infraestructura bancaria)
- Idioma de output: español por input español-dominante ("freelance designer" como loanword no cambia el dominio)
- Override disponible: sí, bajo pedido explícito

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

### Decision Trace

- Mode that would have applied: Routing
- Inputs received: 0 of 5 fully specified (2 partials: #3 with "foreign client paying USD" but no amount/country-specific/options; #4 with "Buenos Aires" but no province/IIBB-jurisdiction specifics; plus a compliance-preference signal that isn't itself one of the 5 inputs)
- Inputs missing: #1 (cat), #2 (monthly volume), #3 (amount + country + payment options), #4 (specific IIBB jurisdiction), #5 (banking infrastructure)
- Output language: English default (mixed-language input with no clear dominant — Spanish and English alternating clauses)
- Override available: yes, on explicit request
