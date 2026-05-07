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

- **Missing:** input no mencionado en absoluto.
- **Weak:** mencionado pero sin la specificity necesaria. Ejemplos:
  - "monotributo" sin cat → weak para input #1
  - "facturo dólares" sin volumen → weak para input #2
  - "mucho" / "poco" / "depende" → weak para cualquier input

Si el specialist tiene 1-2 inputs missing/weak, puede proceder con flag (`⚠ basado en supuesto: cat F asumida`). Si tiene 3+ missing/weak, refuses.

---

## Refusal protocol — cómo se ve el output cuando se dispara

Output máximo 200 palabras. Sin preamble, sin pitch.

```
Antes de routing necesito 4 de estos 5 inputs:

1. Cat monotributo actual (A-K, RI, o unregistered)
2. Volumen USD/mes últimos 3 meses (un range OK)
3. Este invoice: monto USD + país del cliente + opciones de pago que ofrece
4. Jurisdicción IIBB (CABA / PBA / interior / N/A si export-services)
5. Infraestructura bancaria: Wise yes/no, Mercury yes/no, broker yes/no, VASP-registered yes/no

Tengo: [lista lo que sí está]
Falta: [lista lo que no]

Pasame los faltantes en un mensaje y arranco.
```

### Lenguaje del refusal

- Idioma: input language (auto-detect). Si mixed sin clear dominant → English default.
- Tone: operator-direct, no excuses, no apology.
- No incluye: "lo siento", "intentaré ayudarte más con", "me alegra trabajar contigo".
- Sí incluye: enumeración clara, separación entre "tengo" y "falta", invitación a continuar en una sola pregunta.

---

## Override — best-effort guess

El operator puede explícito pedir override:

> *"Dale, hacé un best-effort con lo que tenés."*

En ese caso el specialist procede pero:

- Cada línea que dependió de un input missing se marca: `⚠ guessed — confirmar antes de actuar`
- Confidence cap a 65% (no más)
- La sección Decision Trace lista los inputs que fueron guessed

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
