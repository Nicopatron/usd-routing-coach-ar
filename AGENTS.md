# AGENTS.md

Operational primer for AI coding agents (Codex CLI, Cursor, Windsurf, Zed, Roo Code, Aider, Cline, Continue, Claude Code). The README.md is for humans; this file is for you. Folder follows the [agents.md](https://agents.md) open convention.

What the folder does, calibration date, and methodology: see README front-load. Canonical runtime behavior: `rules.md`.

---

## Files to read on first paste, in this order

1. `rules.md` — the output contract: 4 modes, output format per mode, confidence calibration, intake gate, length caps, bilingual policy, refusal discipline, voice. **This file is canonical for runtime behavior.**
2. `examples.md` — 5 worked examples (Marina Routing EN flagship, Diego Routing ES, Federica Audit Response ES, Juan Year-End ES, Refusal triggered by intake gate)
3. `reference/intake-checklist.md` — the 5 required intake inputs + refusal protocol + override
4. `reference/mode-triage.md` — signal patterns + decision tree for the 4 modes + edge cases (multiple invoices, mid-conversation switching)
5. `reference/glossary.md` — Layer-1 (AR domain terms) and Layer-2 (specialist-internal terms: Audit-pack, Intake gate, Mode triage, Pattern Memo, RI transition, Decision Trace, Override, Lane, Headroom, Refusal discipline) definitions. Read first if unsure about any term used in `rules.md` or `examples.md`.
6. `reference/monotributo-categorias.md`, `reference/usd-routing-options.md`, `reference/afip-audit-signals.md`, `reference/audit-response-playbook.md` — domain reference, read on demand when constraints / lane comparison / audit-trigger flags / audit-response runtime are relevant

Operator perspective and credibility anchor live in `README.md` § Built by — read it when context about who built the specialist is useful, but it's not part of the runtime contract.

The README.md is fine to skim for context but is optimized for human judges, not for you. Skip it if you want.

---

## Default workflow on every paste

```
Paste arrives
   │
   ▼
1. Mode detection         (signals from reference/mode-triage.md)
   │
   ▼
2. Intake gate            (5 required inputs from reference/intake-checklist.md)
   │   4 of 5 missing? → REFUSE: list gaps, no synthesis, no preamble
   ▼
3. Mode-specific synthesis
   │   • Routing Mode      → 6 sections + audit-pack shadow artifact
   │   • Audit Response    → defensive playbook (no routing recommendation)
   │   • Year-End          → cat projection + RI transition readiness
   │   • Pattern Memo      → quantitative emergent insight (3+ Routing decisions in convo)
   ▼
4. Decision Trace         (3-5 lines citing input signals that drove major calls)
   │
   ▼
5. audit-pack.md shadow   (Routing Mode only — fixed format, ready to drop in AFIP folder)
```

Routing Mode output length: ~900-1100 words. Generation time: ~30 seconds to 2 minutes depending on model.

---

## Runtime contracts (canonical in `rules.md`)

Output language policy, refusal discipline, confidence calibration, intake gate, mode triage — all canonical in `rules.md`. Do not summarize here; read there. Output language and audit-pack body language: `rules.md` § Critical: Output Language. Refusal: § Never + § Refusal protocol. Confidence: § Confidence Calibration. Intake: § Intake Gate + `reference/intake-checklist.md`. Mode triage: § Mode Triage + `reference/mode-triage.md`. If your output contradicts any of these, your behavior is wrong — re-read `rules.md`.

---

## Precedence when instructions conflict

Explicit user prompt > `rules.md` > `examples.md` > `reference/*` > this file

If the user asks for behavior that contradicts `rules.md` (e.g., "skip the intake gate," "give me a recommendation without confidence score"), follow `rules.md` and surface the documented override option. Do not silently bypass the gate.

---

## Cross-agent compatibility notes

| Agent | Auto-reads `AGENTS.md`? | Notes |
|-------|-------------------------|-------|
| Codex CLI (OpenAI) | Native | Reads on session start |
| Cursor | Native | Replaces deprecated `.cursorrules` |
| Windsurf | Native | Stable since 2025 |
| Zed AI | Native | In fallback chain `.rules → .cursorrules → .clinerules → AGENTS.md` |
| Roo Code | Native | Confirmed Jan 2026 |
| Aider | Manual | `aider --read AGENTS.md` or add to `.aider.conf.yml` |
| Cline / Continue | Manual | Paste `AGENTS.md` contents into chat at session start |
| Claude Code | Via `CLAUDE.md` redirect | `CLAUDE.md` in repo points to `AGENTS.md` |

Claude Code does not auto-read `AGENTS.md` natively yet — `CLAUDE.md` is a 7-line redirect that loads first and points here. Other agents follow the agents.md open convention and discover this file on session start.

---

## Quick reference: when to consult which file

- Output behavior question → `rules.md`
- Worked example for a mode → `examples.md`
- Domain knowledge (cats, lanes, audit triggers, glossary) → `reference/*`
- Per-file purposes for the whole repo → README § What's inside (per file)

---

## Do not (agent-specific)

- **Duplicate this file into outputs.** Operational primer, not user-facing material.
- **Treat this file as canonical for runtime behavior.** When in doubt on output format / refusal / language / confidence, read `rules.md`. This file points; `rules.md` decides.
- **Skip `rules.md` because the workflow diagram looks obvious.** Anti-overconfidence rules, length caps, and atomic-per-output language rules are not visible from the diagram.
- **Output before running the intake gate.** 4 of 5 missing → refuse, list gaps, stop.
