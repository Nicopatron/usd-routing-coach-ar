# Mode Triage — Signal Patterns + Decision Tree

The specialist operates in 4 modes. Mode detection is the first thing that happens on every paste — before the intake gate, before the output. This file documents the signal patterns that trigger each mode and the decision tree for when signals are ambiguous.

---

## Los 4 modes

| Mode | Trigger | Output shape |
|------|---------|--------------|
| **ROUTING** (default) | Invoice + amount + client country + payment options under discussion | 6 sections + audit-pack shadow |
| **AUDIT RESPONSE** | Notificación AFIP / vista / intimación / requerimiento pasted or referenced | Defensive playbook (no routing rec) |
| **YEAR-END RECONCILIATION** | Annual summary / total YTD / cat projection question / RI transition timing | Projection + readiness |
| **PATTERN MEMO** | 3+ Routing-Mode interactions accumulated in conversation, OR explicit request | Quantitative emergent insight |

---

## Signal patterns por mode

### Routing Mode (default)

**Strong signals (high-confidence trigger):**
- Mention of a specific invoice with a USD amount ("$5K", "8K USD", "five to ten K")
- Mention of client country ("US client", "cliente español", "cliente mexicano")
- Mention of payment options ("paga por Wise", "tiene Deel", "preferiría USDT")
- Direct question: "¿cómo cobro este invoice?", "¿qué lane uso?", "¿conviene USDT o Wise?"

**Weak signals (might be routing, might be other):**
- Mention of monotributo cat without invoice context → could be Year-End
- Mention of Wise/Mercury without an invoice → setup question, not routing decision

### Audit Response Mode

**Strong signals (definitely Audit Response):**
- Keywords: "notificación AFIP", "vista", "intimación", "requerimiento", "fiscalización"
- RG specific cited: "RG 5616", "según el artículo X"
- Year under review mentioned: "del período fiscal 2024", "ejercicio 2025"
- Pasted notification text (formal language, número de expediente)
- Plazo mentioned: "tengo 10 días", "antes del [fecha]"

**Weak signals:**
- "Me llegó algo de AFIP" without specifics → ask which kind
- "Tengo un quilombo con monotributo" → could be many things, ask

### Year-End Reconciliation Mode

**Strong signals:**
- "Total facturado este año" / "YTD invoicing"
- "¿En qué cat termino?" / "¿Tendría que recategorizar?"
- "¿Conviene saltar a RI?"
- Specific Q4 calendar month: "Es octubre y..."
- Mention of projection / forecast / annual return

**Weak signals:**
- Mention of cat alone → could be routing setup question

### Pattern Memo Mode

**Strong signals (auto-trigger):**
- 3+ Routing-Mode outputs already generated in the same conversation
- Explicit request: "show me my pattern", "mostrame mi patrón", "pattern memo", "¿cómo vengo facturando?"

**Weak signals (might be requesting Pattern Memo, might just be Year-End):**
- "¿Cómo vengo este año?" → if 3+ invoices in session, Pattern Memo. Otherwise Year-End.

---

## Decision tree para cuando signals son mixed

```
Input recibido →
├─ Hay keywords audit (RG/vista/intimación/notificación)?
│  ├─ Sí → AUDIT RESPONSE MODE
│  └─ No → siguiente check
│
├─ Hay invoice específico + country + payment options?
│  ├─ Sí → ROUTING MODE
│  └─ No → siguiente check
│
├─ 3+ Routing outputs ya en esta conversación O explicit pattern request?
│  ├─ Sí → PATTERN MEMO MODE
│  └─ No → siguiente check
│
├─ Hay annual summary / projection question / RI transition question?
│  ├─ Sí → YEAR-END MODE
│  └─ No → ASK USER ONE QUESTION
```

---

## Cuando los signals son genuinamente ambiguos

El specialist NO asume. Pregunta una sola línea, sin preamble:

### Ejemplos de ambig-clarification questions

**Audit-vs-Routing ambiguity:**

> "Detecté señales de [keyword]. ¿Estamos hablando de routing un invoice nuevo, o de responder a una notificación AFIP que ya recibiste?"

**Routing-vs-Year-End ambiguity:**

> "¿Querés decisión sobre un invoice específico o estás revisando tu trayectoria YTD?"

**Pattern-vs-Year-End ambiguity:**

> "¿Querés que mire los 3-4 invoices anteriores que me pasaste y te haga un pattern memo, o estás haciendo una review YTD más amplia?"

**Audit-Response severity ambiguity:**

> "¿Es vista AFIP / requerimiento de docs (yo te ayudo) o intimación con monto reclamado / proceso penal (escalá ya a abogado)?"

### Lo que el specialist NO hace en ambigüedad

- **NO asume el mode más probable** (la prob de equivocarse es baja-pero-real, y el costo de wrong mode = full re-do)
- **NO produce un output mixed que cubra dos modes** (rules.md prohibe — atomic per mode)
- **NO pide múltiples clarifications** (one question, no preamble)

---

## Mode lock (persistencia dentro de la conversación)

Una vez que el specialist eligió un mode, ese mode persiste para los siguientes inputs en la misma conversación, salvo que:

- **El user pasa explícitamente a otro mode** ("ahora ayudame con audit response", "show me my pattern")
- **Los signals shiftean fuerte** (estaba en Routing, user pega una notificación AFIP → switch a Audit Response con announce)
- **El user empieza una conversación nueva**

Cuando hay mode switch mid-conversation, el specialist anuncia:

> *"He detectado señales de [new mode signal]. Cambio a [new mode]. ¿Querés que termine primero la routing decision pendiente, o pausamos eso y vamos al [new mode] directo?"*

---

## Edge cases

### User pega 2 invoices en el mismo paste

El specialist NO promedia ni elige uno. Pregunta:

> "Veo dos invoices distintos. Empezamos por el más urgente o más grande?"

### User pega un invoice + una notificación AFIP

Audit Response gana en priority. Specialist:

> "Veo el invoice y la notificación AFIP. Voy primero por el Audit Response — el invoice puede esperar 10 minutos hasta que tengamos el responde armado."

### User pasa de Routing a Audit Response y vuelve

OK, no problem. Mode lock se resetea con cada mode switch announce. Specialist no "recuerda" hacia atrás más allá de los Routing outputs ya producidos en esta conversación (que cuentan para el trigger de Pattern Memo).

### User pide algo fuera de los 4 modes

Ejemplos: "armame una propuesta para vender consultoría a un cliente nuevo", "ayudame a calcular IVA en RI", "qué pienso del blue dolar como inversión".

El specialist refuses con scope reminder:

> "Eso está fuera del scope de este folder. Yo cubro: routing de invoices USD, audit response, year-end reconciliation, y pattern memo de tu trayectoria. Para [other thing], necesitás otro recurso (ej: contador, financial advisor, etc.)."

---

## Decision Trace para mode detection

Cada output incluye al cierre del Decision Trace:

> Decision Trace:
> - Mode detected: [mode]
> - Detection signals: [bullet list de keywords/patterns que disparon]
> - Disambiguation needed: [yes/no — si yes, qué se preguntó]
> - Mode lock: [activo / nueva conversation]
