# USD Routing Coach (Argentina)

A folder-based AI specialist for Argentine indie consultores who invoice external clients in USD/USDT — calibrated, audit-ready, and refuses to recommend channels that would attract AFIP. **Calibrated against the current Argentine regulatory framework as of May 2026** (AFIP RG 5616/2024, CNV Resolución 1058/2025, BCRA Comunicaciones 8226+).

Drop this folder into a Claude project (or open it in Claude Code). Paste your monotributo situation + the next invoice you're about to receive. Get back: a confidence-scored routing recommendation across compliant channels (Wise / Deel / Mercury+MEP / USDT-via-VASP), a per-recommendation audit pack ready to drop into your AFIP folder, and a refusal mechanism that won't recommend informal cash or unregistered crypto — even when they're cheaper.

---

## What you get back

**Drop this folder into a Claude project. Paste your situation. Ask:** *"Synthesize this routing decision."*

You get back this shape (real output, abbreviated):

> ### Recommendation
> **Wise + Factura E for this invoice.**
>
> **Confidence: 92%.**
> +20% because all 5 intake inputs verified
> +15% because Wise lane has 4+ years of practitioner track record under identical conditions
> +10% because Factura E setup confirmed and recently exercised
> −8% because Mercury account exists but unused for invoicing — minor fallback uncertainty
>
> Headroom impact: post-invoice, cat F ~53% utilized YTD.
> Next-month flag: if monthly invoicing accelerates above $4K/mo, recategorización proactiva to G should be considered before August 2026.

> ### audit-pack.md (shadow artifact — guardalo en tu carpeta AFIP/2026/Q2/)
>
> ```
> FECHA: 2026-05-08
> INVOICE: B2B Fintech LLC (US), USD $4,000
> DECISION: Wise + Factura E
> DECISION RATIONALE: Default lane for cat F + US client + sub-$10K invoice.
> CONFIDENCE: 92%
> FX RATE SNAPSHOT: Oficial 1,395 / MEP 1,418 / Wise mid 1,385
> DOCUMENTS TO RETAIN: Factura E #N, Wise statement, signed contract, payment confirmation
> NEXT REVIEW TRIGGER: Si volumen mensual sube >$4K/mo o YTD acumulado supera 70% del techo cat F antes de Aug 2026, revisar recategorización proactiva a cat G.
> ```

*(plus full Situation / Constraints Analysis / Routing Options comparison / Execution Checklist / Decision Trace — full output ~900-1100 words, generation time ~30 seconds to 2 minutes depending on Claude model)*

That output came from this input:

> Hi — I'm Marina, freelance UX designer in Buenos Aires, monotributo cat F, billing ~$3.5K USD/month Q1 2026 to a US client. Got a new $4K USD invoice from a different US client this week. Wise active, Mercury opened (unused), Lemon wallet for USDT. CABA, export-services. Factura E approved. Should I take Wise like always or is there a smarter move?

The full transcript and worked output are in `examples.md`. Three more full syntheses there — Diego (cat I→K with RI transition flag), Federica (audit response when AFIP sends a vista), Juan (year-end reconciliation in October) — plus Example 5 documenting a deliberate refusal when intake is too thin.

**What it won't do:** recommend informal channels (blue dollar cuevas, unregistered crypto P2P) — even when cheaper. AFIP enforcement post-May-2025 closed those windows; SIRA tracks bank deposits and algorithmic matching catches inconsistencies within 6-12 months. The specialist also refuses to synthesize a routing decision when 4 of 5 core intake inputs are missing. See `examples.md` Example 5 for what that refusal looks like.

---

## The Problem This Solves

Indie consultores argentinos who invoice in USD make the same routing decision every month — Wise vs Mercury+MEP vs Deel vs USDT — and most get it wrong about 1 in 5 invoices. The cost of wrong is 1-3% of each invoice in lost spread, plus the slow-burn risk of an AFIP audit when invoice metadata doesn't match Wise inflows.

This specialist compresses that recurring decision from "30 minutes of cross-checking AFIP rules + FX rates + monotributo headroom" into 5 minutes of structured input — and produces a more consistent output than the consultor would calculate at 11 PM tired before the next invoice arrives.

It runs as four loops, not a single shot:

1. **Intake gate.** Five required inputs verified before synthesizing — refuses to guess when four are missing.
2. **Mode triage.** Auto-detects whether you're routing, responding to an audit, doing year-end reconciliation, or asking for a pattern memo.
3. **Mode-specific synthesis.** 6 sections for Routing, defensive playbook for Audit Response, projection + readiness for Year-End, quantitative pattern analysis for Pattern Memo.
4. **Audit-pack shadow output.** Every Routing decision generates a parallel record for your defensive bookkeeping folder.

Bilingual (English / Rioplatense Spanish). Tuned for Argentine indie consultores monotributistas o RI, scoped to engagements in the **$1K–$15K USD per invoice** range. Not for: empleados en relación de dependencia, sociedades SAS facturando local, audits with substantial tax owed (escalá a contador / abogado), structures offshore.

---

## Core Concepts

### Interpretable Context Methodology (ICM)

Folders as architecture, each file does one job well. The structure tells you what's where without needing a tour.

The five-slot contract:

- `identity.md` — *who* the operator is (Argentine indie consultor, monotributista since 2024, bilingual).
- `rules.md` — *how* the operator responds (4 modes, output formats, confidence calibration, intake gate).
- `examples.md` — *what* good looks like, including deliberate refusal and audit response.
- `reference/` — *what* the operator knows (monotributo categories, routing lanes, audit signals, intake gate, mode triage).
- `README.md` + `quickstart.md` — *how* to use the folder.

That's *interpretable* in ICM — not "the model is mysterious," but "the operator's logic is visible and traceable to a regulatory source."

### The 4-Mode State Machine

The specialist auto-detects intent on every paste:

- **Routing Mode** (default): paste invoice scenario → 6-section routing decision (Situation → Constraints Analysis → Routing Options comparison → Recommendation + Confidence → Execution Checklist → Decision Trace).
- **Audit Response Mode**: paste an AFIP vista / intimación → defensive playbook (no routing recommendation, just docs to pull, language to use, what NOT to say, contador trigger).
- **Year-End Reconciliation Mode**: paste annual summary → cat projection, recategorización readiness, RI transition timing analysis.
- **Pattern Memo Mode**: after 3+ Routing decisions in the same conversation, surfaces your routing pattern + cost loss vs theoretical optimum + cat-K threshold projection.

Mode detection runs before the intake gate, before any output. See `reference/mode-triage.md` for the full signal patterns and decision tree.

### Confidence Calibration

Every recommendation surfaces a 0-100% confidence score with the specific signals that elevated or lowered it. No black-box recommendations. The specialist refuses to output >90% confidence unless every signal is verbatim in the input.

The signal-by-signal weighting in the Marina output above is the methodology applied: every recommendation surfaces the signals behind it. Judges, contadores, and the operator herself can audit the reasoning two years later.

### Audit-Pack-Ready Shadow Artifact

Every Routing-Mode output produces a parallel `audit-pack.md` snippet — fixed format, ready to drop into your AFIP folder. Contemporaneous record of signals analyzed, alternatives considered, decision made, FX rate at the moment.

Two years from now, if you're audited, you have the record frozen the day you routed the invoice. SIRA matches against declared income; the audit pack matches against your decision history.

### The Refusal Discipline

The specialist refuses three classes of requests:

1. **Informal channels** (blue dollar cuevas, unregistered crypto P2P) — even when the user explicitly asks. AFIP enforcement post-May-2025 closed those windows.
2. **Routing with thin intake** — if 4 of 5 core inputs are missing, the specialist asks for the gaps in one short message rather than guessing.
3. **Out-of-scope work** — the specialist won't write proposals, calculate IVA for RI, or opine on the blue dollar as investment. It cites the scope and points to the right resource (contador, abogado, financial advisor).

Operator-protection over compliance theatre. This isn't an output template — it's a calibrated operator system.

---

## How It Works

```
usd-routing-coach-ar/
├── README.md                            ← read first
├── quickstart.md                        ← TL;DR, 5 numbered steps
├── identity.md                          ← who the specialist is
├── rules.md                             ← output contract: 4 modes, formats, calibration discipline
├── examples.md                          ← 5 worked examples (1 EN flagship + 3 ES + 1 refusal)
├── reference/
│   ├── monotributo-categorias.md        ← cats A-K, recategorización mechanics, RI triggers
│   ├── usd-routing-options.md           ← Wise / Mercury+MEP / Deel / USDT-VASP × tradeoffs + benchmarks
│   ├── afip-audit-signals.md            ← top mistakes + Audit Response Mode playbook
│   ├── intake-checklist.md              ← 5-input gate + refusal protocol + override
│   └── mode-triage.md                   ← signal patterns + 4-mode decision tree
└── LICENSE
```

### The flow on every paste

```
   ┌─────────────────────────┐
   │  Paste: situation +     │
   │  invoice / question     │
   └────────────┬────────────┘
                ▼
   ┌─────────────────────────┐
   │   1. Mode detection     │  ← reference/mode-triage.md
   └────────────┬────────────┘
                ▼
   ┌─────────────────────────┐    4 of 5 missing
   │   2. Intake gate        │ ─────────────►  Refusal output
   │   (5 required inputs)   │                 (one short message,
   └────────────┬────────────┘                  no synthesis)
                ▼                ← reference/intake-checklist.md
   ┌─────────────────────────┐
   │   3. Mode-specific      │
   │   synthesis:            │
   │   • Routing → 6 sec.    │
   │   • Audit Resp → playbk │
   │   • Year-End → projctn  │
   │   • Pattern → analysis  │
   └────────────┬────────────┘
                ▼
   ┌─────────────────────────┐
   │   4. Decision Trace     │
   │   + audit-pack shadow   │
   │   (Routing Mode only)   │
   └─────────────────────────┘
```

The numbered version:

1. **Mode detection** runs first — the specialist scans the paste for routing / audit / year-end / pattern signals (see `reference/mode-triage.md`).
2. **Intake gate** verifies the 5 required inputs (cat monotributo, monthly USD volume, this invoice details, IIBB jurisdiction, banking infrastructure). Missing 4 of 5 → refusal output (see `examples.md` Example 5).
3. **Mode-specific synthesis** produces the output:
   - Routing → 6-section decision + audit-pack shadow
   - Audit Response → defensive playbook
   - Year-End → projection + readiness
   - Pattern Memo → quantitative emergent insight
4. **Decision Trace** at close — 3-5 lines citing the input signals that drove the recommendation.

Every step is documented in `rules.md`. Nothing is hidden in prompt engineering — if you want to change behavior, you edit a markdown file.

### What's inside (per file)

| File | Job |
|------|-----|
| `quickstart.md` | TL;DR for skim readers — 5 numbered steps from clone to first output. |
| `identity.md` | Who the specialist is — Argentine operator persona, point of view on routing, scope boundaries. |
| `rules.md` | Output contract — 4-mode triage, output format per mode, confidence calibration discipline, intake gate, length caps, bilingual policy, calibration date. |
| `examples.md` | 5 worked examples: Marina (Routing EN flagship) + Diego (Routing ES with RI transition) + Federica (Audit Response ES) + Juan (Year-End ES) + 1 deliberate refusal. |
| `reference/monotributo-categorias.md` | Cats A-K with current ARS limits + USD-equiv at MEP, recategorización mechanics (Feb / Aug), RI transition triggers, "what's about to change Q3-Q4 2026" appendix. |
| `reference/usd-routing-options.md` | Wise / Mercury+MEP / Deel / USDT-VASP / refused options × all-in cost / speed / tax visibility / audit risk / setup checklists / failure modes. May 2026 cost benchmarks. |
| `reference/afip-audit-signals.md` | Top 3 mistakes that trigger audit, other common triggers, full Audit Response Mode playbook (docs to pull, language to use, what NOT to say, contador / abogado escalation triggers). |
| `reference/intake-checklist.md` | The 5-input gate the specialist runs before synthesizing. Refusal protocol, override, registration-first subroute for unregistered consultores. |
| `reference/mode-triage.md` | Signal patterns for the 4 modes, decision tree for ambiguity, mode lock persistence, edge cases (multiple invoices, mid-conversation switching). |
| `LICENSE` | MIT. |

---

## Getting Started

### Prerequisites

- A Claude account (free or paid plan works) — for Path A
- OR [Claude Code](https://claude.ai/code) installed locally — for Path B

### Path A — Claude Project (3-minute setup)

1. Clone or download this folder.
2. Open `claude.ai` → **New Project**.
3. Upload all files into the project's **Project knowledge** panel — including everything inside `reference/`.
4. Open a new chat in that project.
5. Paste your situation: the 5 inputs from `reference/intake-checklist.md` (cat monotributo, monthly USD volume, this invoice details, IIBB jurisdiction, banking infrastructure).
6. Ask: **"Synthesize this routing decision."**

To iterate: *"draft just the audit pack,"* *"compare MEP vs Wise for this volume,"* *"if I switch to RI next quarter, how does this change."*

### Path B — Claude Code locally

```bash
git clone https://github.com/Nicopatron/usd-routing-coach-ar.git
cd usd-routing-coach-ar
```

Open the folder in Claude Code. Tell it:

> *"Read this folder — it's an operator system for Argentine USD invoice routing. I have a routing decision: [paste your 5 inputs + this invoice]. Synthesize it."*

Claude Code reads `README.md` + `identity.md` + `rules.md` + `examples.md` + everything in `reference/` automatically. Same output contract as Path A.

If you don't have a real invoice handy, paste any of the four worked syntheses from `examples.md` to test cold — they're synthetic and self-contained.

---

## Calibration

Calibrated against the current Argentine regulatory framework as of **May 2026**:

- **AFIP RG 5616/2024** — Foreign-Currency E-Invoicing (Factura E in USD streamlined)
- **AFIP RG 5824/2026** — Consumer-ID threshold for invoices ≥10M ARS (effective July 1, 2026)
- **AFIP RG 5319/2025** — Platform-withholding regime expansion (Deel, Payoneer, etc.)
- **CNV Resolución 1058/2025** — VASP Registration mandatory (Lemon, Belo, Buenbit, Binance Argentina registered)
- **BCRA Comunicaciones 8226+** (Apr 2025) — FX market liberalization
- **Monotributo Recategorización Feb 2026** — Cats A-K limits (next recat: August 2026)

Reference files cite the AFIP / CNV / BCRA URLs directly. Verify any current source independently. **If today's date exceeds August 2026 and reference files have not been refreshed, the specialist flags this in every output and recommends regulatory verification before acting on any recommendation.**

---

## Design Philosophy

This folder is built for indie consultores who want the AI to do the routing-decision bookkeeping, not the thinking. The operator makes every consequential call — which lane, when to switch to RI, when to escalate to a contador. The specialist handles the structure, the calibration, the audit-pack snapshot, and the refusal of channels that would create downstream problems.

**The folder structure is the architecture.** Edit the markdown, and you've edited the system. No code to change, no config to redeploy. If you keep one rule, keep this: **each file does one job**. Identity describes WHO. Rules describe HOW. Examples show WHAT good looks like. Reference holds WHAT the operator knows about the regulatory + operational landscape. README explains HOW to use it.

The reference material in `reference/` is intentionally domain-dense — six cat A-K limits with USD equivalents, every viable routing lane with cost benchmarks and failure modes, top 3 audit triggers with specific RGs cited, the 5-input intake gate, the 4-mode triage decision tree. That's the difference between a specialist that recites best practices and one that has actually routed USD invoices for multiple years against the current Argentine regulatory framework.

The methodology travels. To fork this for a different operator-decision specialist (different country tax landscape, different cross-border payment mechanics, different regulated industry):

- Rewrite `identity.md` for your operator persona and operating context.
- Rewrite `rules.md` with your output contract (number of modes, sections per mode, calibration discipline).
- Replace `examples.md` with 3-5 worked examples covering each mode plus at least one refusal.
- Repopulate `reference/` with your domain's regulatory sources (cite them, don't recite generic best practices), decision trees, intake gates, and mode triggers.
- Update this README's first fold with your domain's specific output sample (rendered, not described).

---

## Glossary

- **Monotributo** — Argentine simplified tax regime for small contributors. Cats A-K with annual billing limits + monthly fees.
- **RI (Responsable Inscripto)** — Argentine general tax regime. Required when monotributo K limit is exceeded; includes IVA + Ganancias filings.
- **Factura E** — Argentine export invoice type, used for non-resident clients. IVA-exempt (export regime).
- **AFIP / ARCA** — Argentine federal tax authority (recently renamed from AFIP to ARCA in 2025; both names still in use).
- **CNV** — Argentine Securities Commission, regulator for VASPs (crypto exchanges) since 2025.
- **BCRA** — Argentine Central Bank, regulator of FX market access.
- **IIBB (Ingresos Brutos)** — Argentine provincial gross-income tax. Most monotributistas-export are exempt.
- **MEP / CCL** — Argentine FX market routes via securities (AL30/GD30) for legal USD conversion at better-than-official rates. MEP = local market; CCL = Contado con Liquidación for offshore settlement.
- **VASP (Virtual Asset Service Provider)** — CNV-regulated crypto platform (Lemon, Belo, Buenbit, Binance Argentina). Required for compliant USDT routing post-May-2025.
- **SIRA** — AFIP system that tracks bank deposits and matches against declared income. Algorithmic flagging of inconsistencies.
- **Blanqueo Milei** — One-time tax amnesty 2024, closed for residents May 7, 2025. Funds liberated from CERA accounts Jan 1, 2026.
- **Convenio Multilateral** — Cross-jurisdictional IIBB allocation when services are rendered in multiple Argentine provinces.

---

## Built by

Nico Patrón Uriburu — indie AI consultant at [E-Growth Management](https://www.linkedin.com/in/nicolas-patron-uriburu/), Buenos Aires. Monotributista invoicing USD to clients in US / MX / CL since 2024. Seven-plus years across the build side (Next.js, Supabase, automation pipelines) and the sell side (discovery, scoping, proposals).

I lost roughly **1.5–2% of Q1 2026 invoicing** — about **$130–180 USD across 4 invoices** routed sub-optimally. Twice over the quarter I made calls I'd undo today: once switching reactively to USDT under client pressure when Wise would have been cleaner; once delaying Factura E reconciliation past the same-day window and creating an invoice-FX mismatch I had to chase later. April 2026 was the first month I made the routing call BEFORE the invoice email arrived. This folder is the routing memory I should have had since the day I emitted Factura E #1.

---

## License

MIT — see `LICENSE`. Fork it, swap the operator persona, adapt `reference/` to your country's tax landscape and payment infrastructure.
