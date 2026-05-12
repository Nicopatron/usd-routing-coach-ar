# Changelog

## v1.0.2 — Identity-examples trilogy + numerical accuracy + voice authenticity sweep (2026-05-12)

Post-comp follow-up: built the three identity-example composites (Marina, Diego, Federica) referenced in `examples.md` Examples 1–3, audited the repo numerically and regulatorily, and ran two adversarial review cycles (council of advisors + consultor AR impersonation) to harden voice authenticity. No structural changes to the 4-mode contract or output formats — strictly content accuracy + voice refinement + flagship-case completeness.

### Identity-examples trilogy (new)

Three composite operator profiles, each ~2,000–2,800 words, full 11-section Voiceprint structure:

- `identity-examples/marina.md` — UX designer freelance CABA, monotributo cat F, single anchor US client, Wise default. The "established operator with the loop already built."
- `identity-examples/diego.md` — AI consultant CABA, monotributo cat I→K excedida, multi-client US + EU, Mercury + MEP via broker, RI transition imminent Q3 2026. The "operator under asymmetric time pressure."
- `identity-examples/federica.md` — copywriter freelance Mendoza, monotributo cat E in 2024, mid-vista AFIP por inconsistencias cross-check, Upwork-primary banking, contador-first posture. The "operator in the middle of audit response."

Each cross-linked bidireccional with the matching worked example in `examples.md` (Marina ↔ Example 1, Diego ↔ Example 2, Federica ↔ Example 3).

### Numerical accuracy fixes

- `identity-examples/diego.md` — 3 numerical errors detected by council audit and remediated against the repo's own reference tables: Q1 loss claim $2–3K USD → ~$100 USD in cuota extra (real math: cuota J − cuota I delta × 3 months / MEP 1.418); cuota cat K monthly $1,350 USD → ~$975 USD (1,381,687 ARS / MEP 1.418); spread MEP vs oficial at $8K invoice $240–280 USD → ~$130 USD ((1.418 − 1.395) × 8000 / 1.418).
- `examples.md` Example 2 (Diego) — same spread MEP error propagated in 4 occurrences; corrected. Confidence recalculated 78% → 72% reflecting honest margin ($85–95 USD net after fees vs Wise alternative); recommendation matized from "Mercury + MEP" to "Mercury + MEP primary, Deel as defensible alternative" given modest margin + RI transition + contador-gap context.
- `README.md` — stale cat F headroom citation $33,876 USD → corrected to ~$27,251 USD (matches `reference/monotributo-categorias.md` at MEP 1.418).

### Regulatory framing refinements

- SIRA / SITER / RG 3421 framing across `reference/glossary.md`, `reference/afip-audit-signals.md`, and `reference/usd-routing-options.md` — moved from "sibling regimes" to the technically accurate "RG 3421/2012 as umbrella regulation; RG 4298/2018 redefined the SITER sub-section of RG 3421; RG 5512/2024 and RG 5699/2025 update thresholds." Removes the implicit suggestion that SITER and RG 3421 are independent regimes.
- All RG citations in identity files (`marina.md`, `diego.md`, `federica.md`) reviewed for "voice authenticity" — RG numbers moved from operator vocabulary to contador-mediated language ("the contador calls it 'el cruce'; the RG numbers stay in the formal writ"). Operators in the field don't quote RG numbers; their contadores do. Files now reflect that.

### Flagship case completeness

- `examples.md` Example 3 (Federica) — added "Hipótesis de causa probable" diagnosis section connecting Federica's Upwork-primary banking to the most common cross-check pattern for that operator profile (Factura E razón social = end client; bank deposit remitente = Upwork Global Inc.). Repo already documented the Upwork-Payoneer-flow pattern in `reference/usd-routing-options.md`; the flagship Audit Response Mode case now uses that knowledge. Federica's identity file Sec 6 Vocabulary updated with the operational anchors ("el cruce", "razón social en Factura E vs remitente bancario", "Upwork Global Inc.", "Payoneer withholding").

### Voice authenticity refinements (council + consultor AR impersonation)

- `identity-examples/diego.md` — removed two character-sheet tells that read as "voz autor curando" (running schedule with specific times and Lisbon peer; Telegram groups "no signal, cero" closing). Rewrote with operational anchors only (Discord peers as sanity check for RI journey).
- `identity-examples/federica.md` — refraseado the weekend-cooking-with-mom detail to remove the calibrated-for-vulnerability quote and meta-commentary. Factual detail remains, emotional sub-text removed.
- `examples.md` Example 4 (Juan) — wording precision: "recategorización forzada inminente" → "ARCA te recategorizará automáticamente en Aug 2026 with potential penalization"; "multa por sub-cat-ización 2026" → "penalization standard AR practice (the contador calculates case-by-case based on interest + unpaid quota delta), no single RG-numeric percentage."

### Tracking + tooling

- `identity-examples/MARINA-AUDIT.md` — receipt for the two audit cycles (Marina round 1+2, Diego round 1, Federica preventive, plus the re-audit cycle uncovering Upwork-Payoneer gap + voice-authenticity refinements). 16 cumulative lessons documented.
- `identity-examples/voice-tics-pending.md` — 3 entries logged as "observed but not promoted" (Sec 4 third-person opening uniformity, em-dashes-banned bullet duplicated literally across 3 files, confidence math +N/−N tension in Example 2). Each with a promotion rule keyed to the next observation cycle.
- `identity.md` — added cross-reference to `reference/afip-audit-signals.md` for the "AFIP audits inconsistency, not suspicion" claim (operationally true, now explicitly anchored).
- `rules.md` § Output format — ROUTING MODE — clarified that confidence breakdown lives in the Recommendation prose ("+N% because..."); the audit-pack shadow artifact reports the final consolidated number only.

### Calibration

Same as v1.0 (May 2026 framework). RG citations re-verified against Boletín Oficial sources in the re-audit cycle:

- RG 3421/2012 (régimen unificado de información financiera) — vigente, with threshold updates by RG 5512/2024 and RG 5699/2025
- RG 4298/2018 (SITER sub-régimen) — vigente
- RG 5616/2024, RG 5700/2025, RG 5824/2026, CNV Res 1058/2025, Decreto 953/2024 — all verified vigentes May 2026

---

## v1.0.1 — Brief-alignment patch (2026-05-09)

Front-loaded the README with a 3-beat opening paragraph (what / who / how-to-use-in-60s) plus a quick acronym key, per the brief's "one paragraph someone could follow with no other context" requirement. Folded `quickstart.md` into the README opening and deleted the separate file (its job — TL;DR 5 steps — is now done by the front-load). Bilingual policy now explicitly covers audit-pack body narrative (was implicit; cold-stranger audit flagged the ambiguity). README dropped from 345 → ~315 lines while gaining the cold-reader on-ramp.

## v1.0 — Clief Notes Weekly Comp #3 (2026-05-09)

Initial public release.

### What this folder is

A folder-based AI specialist for Argentine indie consultores invoicing US/EU clients in USD/USDT. Drop into a Claude project (or any agent that reads `AGENTS.md`) and Claude becomes a routing coach.

### What's in this release

- **4-mode state machine**: Routing (default) / Audit Response / Year-End Reconciliation / Pattern Memo
- **Routing Mode output**: 6-section synthesis (Situation → Constraints Analysis → Routing Options → Recommendation → Execution Checklist → Decision Trace) plus an `audit-pack.md` shadow artifact ready to drop into your AFIP folder
- **Confidence calibration**: signal-by-signal breakdown, anti-overconfidence rule (>90% requires every signal verbatim in input)
- **Refusal discipline**: refuses informal channels (blue dollar cuevas, unregistered crypto P2P) even when explicitly asked; refuses synthesis when 4 of 5 intake inputs are missing
- **Bilingual atomic-per-output**: Spanish input → Spanish output, English input → English output, no mid-section language switching; explicit translation table in `rules.md`
- **Cross-agent compatibility**: `AGENTS.md` (agents.md convention) read natively by Codex CLI / Cursor / Windsurf / Zed / Roo Code; `CLAUDE.md` redirect for Claude Code

### Calibration

Argentine regulatory framework as of **May 2026**:

- AFIP RG 5616/2024 — Foreign-Currency E-Invoicing
- ARCA RG 5824/2026 — Electronic monthly liquidación + expansion of e-invoicing obligados (effective 2026-07-01)
- ARCA RG 5700/2025 — Consumer-ID threshold ≥10M ARS (effective May 2025; does not apply to Factura E to foreign clients)
- CNV Resolución 1058/2025 — VASP Registration mandatory
- BCRA Comunicaciones 8226+ (Apr 2025) — FX market liberalization
- Monotributo Recategorización Feb 2026 — Cats A-K limits (next recat: Aug 2026)

If today's date exceeds August 2026 and reference files have not been refreshed, the specialist flags this in every output and recommends regulatory verification before acting on any recommendation.

### Files

```
usd-routing-coach-ar/
├── README.md                            human primer
├── AGENTS.md                            agent operational primer
├── CLAUDE.md                            Claude Code redirect → AGENTS.md
├── identity.md                          operator persona + scope
├── rules.md                             4-mode output contract + calibration discipline
├── examples.md                          5 worked examples (4 modes + refusal)
├── reference/
│   ├── intake-checklist.md              5-input gate + refusal protocol
│   ├── mode-triage.md                   signal patterns + decision tree
│   ├── monotributo-categorias.md        cats A-K limits + recat mechanics
│   ├── usd-routing-options.md           Wise / Mercury+MEP / Deel / USDT × tradeoffs
│   ├── afip-audit-signals.md            triggers that increase audit probability (Routing Mode flags)
│   └── audit-response-playbook.md       runtime playbook for Audit Response Mode
├── LICENSE                              MIT
└── CHANGELOG.md                         this file
```

### Bug fixes in v1.0

- **Bilingual section header drift** (`84728b7`, 2026-05-09) — Examples 2 (Diego), 3 (Federica), 4 (Juan) had English section headers in Spanish-output examples, violating the atomic-per-output rule. Translated 17 section headers + 7 audit-pack labels per the `rules.md` EN/ES translation table. Marina (EN flagship Example 1) unchanged.
- **AGENTS.md ↔ rules.md contradiction on audit-pack labels** (`84728b7`) — AGENTS.md said "labels stay Spanish always", rules.md had EN/ES translation table. Resolved per AGENTS.md own precedence rule (rules.md > AGENTS.md): audit-pack labels translate per output language.

### License

MIT. Fork it, swap the regulatory framework in `reference/`, rebuild for your country's tax landscape and payment infrastructure.
