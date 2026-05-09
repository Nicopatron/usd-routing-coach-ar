# Changelog

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
