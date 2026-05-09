# Changelog

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
- AFIP RG 5824/2026 — Consumer-ID threshold (effective 2026-07-01)
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
├── quickstart.md                        TL;DR 5 numbered steps
├── identity.md                          operator persona + scope
├── rules.md                             4-mode output contract + calibration discipline
├── examples.md                          5 worked examples (4 modes + refusal)
├── reference/
│   ├── intake-checklist.md              5-input gate + refusal protocol
│   ├── mode-triage.md                   signal patterns + decision tree
│   ├── monotributo-categorias.md        cats A-K limits + recat mechanics
│   ├── usd-routing-options.md           Wise / Mercury+MEP / Deel / USDT × tradeoffs
│   └── afip-audit-signals.md            top mistakes + Audit Response playbook
├── LICENSE                              MIT
└── CHANGELOG.md                         this file
```

### Bug fixes in v1.0

- **Bilingual section header drift** (`84728b7`, 2026-05-09) — Examples 2 (Diego), 3 (Federica), 4 (Juan) had English section headers in Spanish-output examples, violating the atomic-per-output rule. Translated 17 section headers + 7 audit-pack labels per the `rules.md` EN/ES translation table. Marina (EN flagship Example 1) unchanged.
- **AGENTS.md ↔ rules.md contradiction on audit-pack labels** (`84728b7`) — AGENTS.md said "labels stay Spanish always", rules.md had EN/ES translation table. Resolved per AGENTS.md own precedence rule (rules.md > AGENTS.md): audit-pack labels translate per output language.

### License

MIT. Fork it, swap the regulatory framework in `reference/`, rebuild for your country's tax landscape and payment infrastructure.
