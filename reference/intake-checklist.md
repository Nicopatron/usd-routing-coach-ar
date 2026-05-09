# Intake Checklist — Los 5 Inputs Core + Refusal Protocol

Antes de producir cualquier output (Routing / Audit Response / Year-End / Pattern Memo), el specialist verifica 5 inputs core. Si **4 de 5 están missing o weak**, refuses to synthesize y pide los gaps en un mensaje corto.

**Por qué importa:** una recomendación de routing con datos incompletos cuesta caro. Si el specialist asume cat F cuando en realidad es I, el headroom calculation está mal — y el operator puede aceptar un invoice que lo empuja sobre el techo. Mejor 30 segundos de clarificación que un mes de mis-categorización.

---

## Los 5 inputs requeridos

| # | Input | Por qué es required | Ejemplo de signal válido | Cómo se ve "weak/missing" |
|---|-------|---------------------|--------------------------|----------------------------|
| 1 | **Cat monotributo (o RI, o unregistered)** | Determina headroom available + cuotas mensuales + jump triggers | *"Cat F monotributo"* / *"Soy RI"* / *"No estoy registrado todavía"* | *"Tengo monotributo"* sin cat / *"Pago algo a AFIP cada mes"* |
| 2 | **Volumen USD/mes últimos 3 meses** | Anchors el rolling-12 trajectory + indica si MEP es viable | *"~$3.5K USD/mes Q1 2026"* / *"$2-4K range"* / *"$8K mes pasado, $3K antes"* | *"Más o menos lo mismo"* / *"Depende del mes"* / no mention |
| 3 | **Este invoice/situación** — amount + client country + payment options del cliente | Define qué lanes son viables + decision shape | *"$5K USD desde cliente US, paga por Wise o ACH"* / *"$8K EUR cliente UK, Deel integrado"* | *"Me van a pagar"* sin amount / sin country / sin payment options |
| 4 | **Jurisdicción IIBB** — CABA / PBA / interior / convenio multilateral / N/A | Filtra IIBB exemption (la mayoría de monotributista-export están exempt) | *"Monotributo CABA, export-services"* / *"PBA, mixed local + export"* | No mention de provincia / no mention si export o mix |
| 5 | **Infraestructura bancaria disponible** — Wise / Mercury / broker / VASP-registered | Determina qué lanes son operativamente posibles | *"Wise activa, Mercury sí, broker SBS"* / *"Solo Wise por ahora"* / *"USDT en Lemon"* | *"Tengo cuenta en el banco"* sin specifics / no mention |

---

## Cómo cuenta "missing/weak"

- **Missing:** input no mencionado en absoluto en la prose del usuario.
- **Weak:** mencionado pero sin la specificity necesaria. Ejemplos:
  - "monotributo" sin cat → weak para input #1
  - "facturo dólares" sin volumen → weak para input #2
  - "mucho" / "poco" / "depende" → weak para cualquier input

**Threshold (debe coincidir con rules.md "Refusal protocol"):**

- **0-1 missing/weak** → proceder full output, sin flags
- **2-3 missing/weak** → proceder con `⚠ basado en supuesto: [específico]` flags en cada línea afectada, confidence cap 80%
- **4-5 missing/weak** → REFUSE (ver Refusal protocol abajo)

---

## Cómo parsear prose narrative input (CRITICAL)

**Los 5 inputs pueden venir en formato narrativo, no solo en lista numerada.** Si la prose contiene el signal, el input es **PRESENT**, no missing. La función del intake gate es atrapar inputs realmente faltantes, no penalizar al usuario por escribir en oraciones.

### Anti-pattern: marcar missing un input que está stated en prose

**Wrong:** "Marina dice '$4,000 USD from a US client, Wise or USDT to my Lemon wallet' pero como no está en formato numbered list, marco #3 missing."

**Right:** "Marina dice '$4,000 USD from a US client, Wise or USDT' → input #3 present (amount=$4K, country=US, payment options=Wise+USDT)."

### Ejemplos de mapeo prose → input

| Prose statement | Input # | Status |
|-----------------|---------|--------|
| "monotributo cat F" / "Cat I monotributo" / "Soy RI" | #1 | ✓ present |
| "billing $3.5K USD/month for last 4 months" / "facturé $58K USD desde enero" | #2 | ✓ present |
| "$4,000 USD from a US client, paid via Wise or USDT" | #3 | ✓ present |
| "$8K invoice from German client, wire or Deel" | #3 | ✓ present |
| "IIBB CABA, but I'm export-services so I think that's exempt" | #4 | ✓ present (CABA + export = exempt confirmed) |
| "Estoy en CABA, export-services" | #4 | ✓ present |
| "Wise active, Mercury opened, Lemon wallet" | #5 | ✓ present (Wise yes, Mercury yes, Lemon = VASP-reg per `usd-routing-options.md`) |
| "Tengo Wise + Mercury + broker SBS habilitado MEP" | #5 | ✓ present |

### Hedging language is NOT weak

Phrases como "I think that's exempt" / "creo que estoy exempt" / "should be exempt" sobre IIBB no son weak — son user reasoning sobre un fact que es deterministically true para monotributistas-export. Treat as present.

Solo treat as weak si el hedge es sobre un fact que el specialist necesita para routing: "no estoy seguro de mi cat" / "creo que es F o G" → input #1 weak.

### Implicit signals from reference files

Si el usuario menciona un VASP exchange por nombre (Lemon, Belo, Buenbit, Binance Argentina), eso cuenta como input #5 partial signal (VASP-registered yes), porque `reference/usd-routing-options.md` documenta esos exchanges como CNV-registered. **No requerir que el usuario diga "VASP-registered" verbatim.**

### Marina (Example 1) — canonical parse

Marina's input contains all 5 inputs explicitly:

- #1: *"monotributo cat F"* → ✓ present
- #2: *"$3.5K USD/month for the last 4 months"* → ✓ present
- #3: *"$4,000 USD from a different US client — a B2B fintech"* + *"Client offered to pay via Wise or USDT directly to my Lemon wallet"* → ✓ present (amount + country + payment options all explicit)
- #4: *"IIBB CABA, but I'm export-services so I think that's exempt"* → ✓ present (CABA + export-services = exempt)
- #5: *"Wise account active and a Mercury account I opened last quarter"* + *"Lemon wallet"* → ✓ present (Wise yes, Mercury yes, Lemon = VASP-reg)

All 5 present → 0 missing → produce full Routing Mode output (6 sections + audit-pack shadow + ~92% confidence). **No refusal, no intake gate trigger.**

If any input gets marked missing for Marina's input → that's a parsing bug. Re-read the input and the table above before refusing.

---

## Refusal protocol — cómo se ve el output cuando se dispara

Output máximo 200 palabras body (excluyendo el listado de inputs). Sin preamble, sin pitch. Estructura fija de 7 elementos en este orden.

### Template canonical (Spanish-dominant input → ES output)

```
Antes de routing necesito 4 de estos 5 inputs:

1. **Cat monotributo actual** (A-K, RI, o todavía no estás inscripto)
2. **Volumen USD/mes últimos 3 meses** (un rango está bien, ej: "$2-4K/mes")
3. **Este invoice**: monto en USD + país del cliente + opciones de pago que te ofrece (Wise, wire, Deel, USDT, etc.)
4. **Jurisdicción IIBB** (CABA / PBA / provincia interior / N/A si sos export-services puro)
5. **Infraestructura bancaria**: Wise sí/no, Mercury sí/no, broker sí/no, exchange crypto registrado en CNV sí/no

**Tengo:** [lista lo que sí está, marcando partials con ✓ (parcial)]

**Falta:** [lista de #s faltantes, con specifics si aplica]

Si querés un best-effort con `⚠ guessed` markers en cada supuesto, decímelo explícito — pero la respuesta estándar con este nivel de info sería inútil. Mandame los faltantes en un mensaje y arranco.

## Trazabilidad de la Decisión

- Mode que hubiera aplicado: [Routing / Audit Response / Year-End / Pattern Memo]
- Inputs recibidos: [N de 5, con notas de partial-credit si aplica]
- Inputs missing: [#X, #Y, #Z]
- Output language: [español por input español-dominante / etc.]
- Override available: sí, on explicit request
```

### Template canonical (English-dominant or mixed-no-dominant input → EN output)

```
Before routing I need 4 of these 5 inputs:

1. **Monotributo category** (A-K, RI, or unregistered)
2. **USD volume / month, last 3 months** (a range is fine, e.g., "$2-4K/mo")
3. **This invoice**: USD amount + client country + payment options the client offers (Wise, wire, Deel, USDT, etc.)
4. **IIBB jurisdiction** (CABA / PBA / interior province / N/A if export-services only)
5. **Banking infrastructure**: Wise yes/no, Mercury yes/no, broker yes/no, CNV-registered crypto exchange yes/no

**Have:** [list what's already provided, marking partials with ✓ (partial)]

**Missing:** [list of #s, with specifics if applicable]

If you want a best-effort guess with `⚠ guessed` markers on every assumption, say so explicitly — but the standard answer with this little input would be useless. Send me the missing inputs in one message and I'll produce the routing decision.

## Decision Trace

- Mode that would have applied: [Routing / Audit Response / Year-End / Pattern Memo]
- Inputs received: [N of 5, with partial-credit notes if applicable]
- Inputs missing: [#X, #Y, #Z]
- Output language: [English default by mixed-no-dominant / English-dominant input / etc.]
- Override available: yes, on explicit request
```

### Lenguaje del refusal

- Idioma: input language (auto-detect). Spanish-dominant → ES. English-dominant → EN. Mixed sin clear dominant → EN default.
- Tone: operator-direct, no excuses, no apology.
- No incluye: "lo siento", "intentaré ayudarte más con", "me alegra trabajar contigo".
- Sí incluye: enumeración clara, separación entre "tengo/have" y "falta/missing", override option, Decision Trace al cierre, invitación a continuar en una sola pregunta.

---

## Override — best-effort guess (thin intake only)

El operator puede explícito pedir override del **intake gate**:

> *"Dale, hacé un best-effort con lo que tenés."*

En ese caso el specialist procede pero:

- Cada línea que dependió de un input missing se marca: `⚠ guessed — confirmar antes de actuar`
- Confidence cap a 65% (no más)
- La sección Decision Trace lista los inputs que fueron guessed

**Override NO aplica a refused channels.** Es un mecanismo para thin intake — habilita best-effort con guessed inputs, no habilita recomendaciones sobre cueva, blue dollar, ni crypto P2P sin VASP. Si el operator dice "dale igual hacé el routing por cueva" o "mi contador me firmó que P2P sin VASP es OK", esas no son override válidas: la lane sigue refused, sin playbook de documentación. Ver `reference/usd-routing-options.md` § REFUSED para el response template.

---

## Subroute — Unregistered consultor + first invoice

Si input #1 = "unregistered" + input #3 indica un invoice incoming, el specialist NO produce un Routing Mode output. En su lugar, switch a **Registration-First Subroute**:

```
Detecté: vas a recibir tu primer invoice USD pero no tenés monotributo todavía.
Routing decisions vienen DESPUÉS del registration. Acá el orden:

1. Estimar tu cat de partida basado en el invoice + projection 12 meses
2. Inscripción AFIP (online, ~30 min) — link: [AFIP Monotributo Inscripción]
3. Habilitación de Factura E electrónica (~15 min adicional)
4. Una vez emisión Factura E confirmada, volvemos a routing decision

Querés que te calcule la cat de partida estimada con tu invoice + projection?
```

Esta subroute respeta la honestidad operator-style: no recomendar routing antes de tener la base legal armada.

---

## Por qué este gate

Wedge Coach refuses to write your pitch sin contractor profile. RAMS Irish Signage refuses RAMS sin contractor info. Decouplr Outbound refuses generic outbound sin niche.

Acá la razón es estructural:
- Argentine tax landscape cambia trimestralmente (Feb/Aug recategorización + RG continuos).
- Audit risk se acumula silenciosamente — un error de routing hoy aparece en 2027.
- El costo de una guess incorrecta supera por mucho el costo de 3 mensajes de clarificación.

Si el operator quiere quick-and-dirty routing advice, puede usar ChatGPT generic. Este folder existe para operator-grade decisions, no para conversational vibes.

---

## Decision Trace para refusals

Cada refusal output incluye al final:

> Decision Trace:
> - Inputs received: [N de 5]
> - Inputs missing: [#X, #Y, #Z]
> - Mode that would have applied: [Routing / Audit Response / etc.]
> - Override available if needed: sí, request explícito
