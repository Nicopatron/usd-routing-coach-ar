# USD Routing Coach (Argentina)

**What this is.** A folder-based AI specialist for Argentine indie consultores who get paid in USD and need to pick the right payment channel — Wise vs Mercury+MEP vs Deel vs USDT-via-VASP — and want a paper trail in case AFIP audits them. Drop the folder into a Claude project, paste an invoice (or an AFIP notice), get back a structured routing decision (or an audit-response playbook) plus a parallel audit-pack snapshot for your defensive folder.

**Who it's for.** Argentine independent consultores invoicing external clients in dollars, $1K–$15K USD per invoice, on monotributo cat A–K or RI. Calibrated to the Argentine regulatory framework as of May 2026 — full reg-citation list in [`rules.md`](./rules.md) § Calibration date.

**How to use it in 60 seconds.** (1) Clone the repo (or download the folder). (2) Drag every `.md` file (root + `reference/`) into a new claude.ai Project's knowledge base. (3) In a new chat in that project, paste your situation with the 5 inputs (cat monotributo · monthly USD volume · this invoice + client country + payment options · IIBB jurisdiction · banking infra) and ask **`Synthesize this routing decision.`** (4) Read the 6-section output + the audit-pack shadow. Iterate with *"draft just the audit pack"* / *"compare MEP vs Wise"* / *"if I switch to RI next quarter."*

**Quick acronym key for non-AR readers** (full list in [`reference/glossary.md`](./reference/glossary.md)):

- **AFIP / ARCA** — Argentina's federal tax authority (renamed AFIP→ARCA in 2025; both names in use).
- **monotributo** — Argentine simplified tax regime; categories A–K with annual USD-equivalent billing ceilings (cat F ~$27K, cat I ~$55K, cat K top, then RI).
- **Factura E** — Argentine export invoice type for non-resident clients (IVA-exempt under export regime).
- **MEP / CCL** — legal Argentine FX routes via sovereign bonds (AL30 / GD30); MEP = local market, CCL = offshore settlement.
- **VASP** — Virtual Asset Service Provider — CNV-registered crypto exchange (Lemon, Belo, Buenbit, etc.); required for compliant USDT routing.
- **IIBB (Ingresos Brutos)** — Argentine provincial gross-income tax; most monotributistas-export are exempt.
- **vista / intimación / requerimiento** — escalation tiers of AFIP audit notices, lightest to heaviest.

**Bilingual.** Spanish input → Spanish output (Rioplatense). English input → English output. Mixed input with no clear dominant → English by default. AR-tax proper nouns (Factura E, monotributo, MEP, IIBB, RI, vista, etc.) stay in Spanish in any output language; the rest translates atomically.

**What it won't do.** Recommend informal channels (blue dollar cuevas, unregistered crypto P2P) — even when cheaper. AFIP enforcement post-May-2025 closed those windows; ARCA cross-check (SITER + RG 3421 cuentas bancarias + VASP reporting to UIF) catches inconsistencies algorithmically within 6-12 months. The specialist also refuses to synthesize when 4 of 5 core intake inputs are missing. See `examples.md` Example 5 for what that refusal looks like.

---

## What you get back

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
> Next-month flag: if monthly invoicing accelerates above $4K/mo, proactive recategorización to cat G should be considered before August 2026.

> ### audit-pack.md (shadow artifact — save in AFIP/2026/Q2/ folder)
>
> ```
> DATE: 2026-05-08
> INVOICE: B2B Fintech LLC (US), USD $4,000
> DECISION: Wise + Factura E
> DECISION RATIONALE: Default lane for cat F + US client + sub-$10K invoice.
> CONFIDENCE: 92%
> FX RATE SNAPSHOT: Oficial 1,395 / MEP 1,418 / Wise mid 1,385
> DOCUMENTS TO RETAIN: Factura E #N, Wise statement, signed contract, payment confirmation
> NEXT REVIEW TRIGGER: If monthly volume rises above $4K/mo or YTD cumulative exceeds 70% of the cat F ceiling before Aug 2026, revisit proactive recategorización to cat G.
> ```

*(plus full Situation / Constraints Analysis / Routing Options comparison / Execution Checklist / Decision Trace — full output ~900-1100 words, generation time ~30 seconds to 2 minutes depending on Claude model)*

That output came from this input:

> Hi — I'm Marina, freelance UX designer in Buenos Aires, monotributo cat F, billing ~$3.5K USD/month Q1 2026 to a US client. Got a new $4K USD invoice from a different US client this week. Wise active, Mercury opened (unused), Lemon wallet for USDT. CABA, export-services. Factura E approved. Should I take Wise like always or is there a smarter move?

The full transcript and worked output are in `examples.md`. Three more full syntheses there — Diego (cat I→K with RI transition flag), Federica (audit response when AFIP sends a vista), Juan (year-end reconciliation in October) — plus Example 5 documenting a deliberate refusal when intake is too thin.

**A note on the three identity-examples.** Marina, Diego, and Federica (the operator profile deep-dives in `identity-examples/`) are **composites by design**: illustrative operators with articulated voice pillars, chosen to cover three distinct stages of the monotributo journey (cat F single-anchor, cat I→K multi-client pre-RI, cat E mid-audit-response). They are not auto-ethnographies of real operators, who in practice are messier, more contradictory, and less conscious of their own voice. The composites are anchors for the specialist, not straightjackets: if your situation is mixed or edge, the specialist still works — the identity-examples are reference posts, not casting calls.

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
- `README.md` — *how* to use the folder (front-loaded one-paragraph primer + deeper sections).

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

Two years from now, if you're audited, you have the record frozen the day you routed the invoice. ARCA cross-references declared income against bank deposits + VASP reports; the audit pack matches against your decision history.

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
├── README.md                            ← read first (humans)
├── AGENTS.md                            ← agent-facing operational primer (auto-read by Codex / Cursor / Windsurf / etc.)
├── CLAUDE.md                            ← minimal redirect to AGENTS.md for Claude Code
├── identity.md                          ← who the specialist is
├── rules.md                             ← output contract: 4 modes, formats, calibration discipline
├── examples.md                          ← 5 worked examples (1 EN flagship + 3 ES + 1 refusal)
├── reference/
│   ├── monotributo-categorias.md        ← cats A-K, recategorización mechanics, RI triggers
│   ├── usd-routing-options.md           ← Wise / Mercury+MEP / Deel / USDT-VASP × tradeoffs + benchmarks
│   ├── afip-audit-signals.md            ← triggers that increase audit probability (Routing Mode flags)
│   ├── audit-response-playbook.md       ← runtime playbook for Audit Response Mode (docs, language, escalation)
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
| `AGENTS.md` | Agent-facing operational primer — file-read order, default workflow, language policy, refusal discipline, confidence calibration. Auto-read by Codex / Cursor / Windsurf / Zed / Roo Code. |
| `CLAUDE.md` | Minimal redirect to `AGENTS.md` for Claude Code (which doesn't auto-read `AGENTS.md` natively yet). |
| `identity.md` | Who the specialist is — Argentine operator persona, point of view on routing, scope boundaries. |
| `rules.md` | Output contract — 4-mode triage, output format per mode, confidence calibration discipline, intake gate, length caps, bilingual policy, calibration date. |
| `examples.md` | 5 worked examples: Marina (Routing EN flagship) + Diego (Routing ES with RI transition) + Federica (Audit Response ES) + Juan (Year-End ES) + 1 deliberate refusal. |
| `reference/monotributo-categorias.md` | Cats A-K with current ARS limits + USD-equiv at MEP, recategorización mechanics (Feb / Aug), RI transition triggers, "what's about to change Q3-Q4 2026" appendix. |
| `reference/usd-routing-options.md` | Wise / Mercury+MEP / Deel / USDT-VASP / refused options × all-in cost / speed / tax visibility / audit risk / setup checklists / failure modes. May 2026 cost benchmarks. |
| `reference/afip-audit-signals.md` | Top 3 mistakes that trigger audit + other common triggers. Used by Routing Mode to generate audit-risk flags. |
| `reference/audit-response-playbook.md` | Runtime playbook for Audit Response Mode: documents to pull, suggested response language, what NOT to say, contador / abogado escalation triggers. |
| `reference/intake-checklist.md` | The 5-input gate the specialist runs before synthesizing. Refusal protocol, override, registration-first subroute for unregistered consultores. |
| `reference/mode-triage.md` | Signal patterns for the 4 modes, decision tree for ambiguity, mode lock persistence, edge cases (multiple invoices, mid-conversation switching). |
| `LICENSE` | MIT. |

---

## Getting Started

### Prerequisites

This folder is **agent-agnostic** — works with any AI agent that reads markdown files. Three documented paths:

- **Path A:** Claude account (free or paid plan works) — browser-based, easiest first try
- **Path B:** [Claude Code](https://claude.ai/code) — local CLI agent
- **Path C:** Codex CLI / Cursor / Windsurf / Zed / Roo Code / Aider / Cline / Continue — any agent that auto-reads `AGENTS.md` (compatibility table below)

### Evaluating cold without Argentine tax knowledge?

Skip the "5 inputs" step in any of the paths below. Open `examples.md`, copy any `**What [name] pastes:**` block (Marina is the EN flagship — easiest to compare), paste it into your project, ask *"Synthesize this routing decision."* The expected output is documented right beside the input in `examples.md`. The folder either follows its own contract or it doesn't — auditable in 30 seconds, no AR domain expertise required. The 5 worked examples cover all 4 modes plus the refusal protocol. Domain terms are defined in `reference/glossary.md`.

### Try these variations (for evaluators going deeper)

After running the canonical Marina input, these poke the contract to confirm it's calibrated, not memorized:

1. **Change Marina's `cat F` to `cat I`** → recommendation shifts from Wise (default low-volume) to Mercury+MEP (default high-volume); RI transition flag may surface depending on YTD context
2. **Bump Marina's invoice from `$4,000 USD` to `$25,000 USD`** → cat F headroom (~$27,251 USD ceiling at MEP 1.418) blows through; specialist flags forced cat-jump or RI transition prominently
3. **Omit `IIBB CABA` from Marina's input** → 1 input weak; proceeds with `⚠ basado en supuesto: IIBB asumido CABA + export exempt` flag, confidence cap 80%
4. **Paste Example 5's vague input + add `"Dale, hacé un best-effort con lo que tenés"`** → override triggers; produces routing with confidence ≤65% and `⚠ guessed` markers on every line that depended on a missing input
5. **After Marina's routing decision, paste Federica's AFIP vista input in the same chat** → mode switch announced (`Cambio de Modo: Audit Response`); routing recommendation paused until audit is resolved; no new audit-pack generated for the audit response output

The contract is in `rules.md`. The math is in `reference/monotributo-categorias.md` + `reference/usd-routing-options.md`. The mode-detection signals are in `reference/mode-triage.md`. Each variation traces to specific files; nothing is hidden in prompt engineering.

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

### Path C — Codex CLI / Cursor / Windsurf / other agents

This folder includes an `AGENTS.md` file following the [agents.md](https://agents.md) open convention. Most CLI agents auto-discover and read it on session start.

```bash
git clone https://github.com/Nicopatron/usd-routing-coach-ar.git
cd usd-routing-coach-ar
```

Open the folder with your agent and paste your situation. Compatibility:

| Agent | Auto-reads `AGENTS.md`? | Notes |
|-------|-------------------------|-------|
| Codex CLI (OpenAI) | ✅ Native | Reads on session start |
| Cursor | ✅ Native | Replaces deprecated `.cursorrules` |
| Windsurf | ✅ Native | Stable since 2025 |
| Zed AI | ✅ Native | In fallback chain `.rules → .cursorrules → .clinerules → AGENTS.md` |
| Roo Code | ✅ Native | Confirmed Jan 2026 |
| Aider | ⚠️ Manual | `aider --read AGENTS.md` or add to `.aider.conf.yml` |
| Cline / Continue | ⚠️ Manual | Paste `AGENTS.md` contents into chat at session start |
| Claude Code | ✅ Via `CLAUDE.md` redirect | `CLAUDE.md` in repo points to `AGENTS.md` |

Once the agent has the operational primer loaded, paste your situation: the 5 inputs from `reference/intake-checklist.md` (cat monotributo, monthly USD volume, this invoice details, IIBB jurisdiction, banking infrastructure). Ask: *"Synthesize this routing decision."*

Same output contract as Path A and Path B.

---

## Calibration

**Calibrated against the current Argentine regulatory framework as of May 2026.** Full citation list (AFIP/ARCA RGs, CNV resolutions, BCRA Comunicaciones, monotributo recategorización dates) and the forward-looking validity rule live in [`rules.md`](./rules.md) § Calibration date — single source of truth.

Next monotributo recategorización: August 2026. Reference files cite AFIP / CNV / BCRA URLs directly; verify any current source independently before acting on any recommendation.

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

Quick acronym key is at the top of this README. Full term definitions — including SITER, RG 3421, Blanqueo Milei, Convenio Multilateral, vista / intimación / requerimiento, Cuenta CERA — live in [`reference/glossary.md`](./reference/glossary.md). Single source of truth.

---

## Built by

Nico Patrón Uriburu — indie AI consultant at [E-Growth Management](https://www.linkedin.com/in/nicolas-patron-uriburu/), Buenos Aires. Monotributista invoicing USD to clients in US / MX / CL since 2024. Seven-plus years across the build side (Next.js, Supabase, automation pipelines) and the sell side (discovery, scoping, proposals).

I lost roughly **1.5–2% of Q1 2026 invoicing** — about **$130–180 USD across 4 invoices** routed sub-optimally. Twice over the quarter I made calls I'd undo today: once switching reactively to USDT under client pressure when Wise would have been cleaner; once delaying Factura E reconciliation past the same-day window and creating an invoice-FX mismatch I had to chase later. April 2026 was the first month I made the routing call BEFORE the invoice email arrived. This folder is the routing memory I should have had since the day I emitted Factura E #1.

---

## License

MIT — see `LICENSE`. Fork it, swap the operator persona, adapt `reference/` to your country's tax landscape and payment infrastructure.
