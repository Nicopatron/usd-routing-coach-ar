# Changelog

## v1.0.3 — identity.md council audit (Phase K) + adversarial regression sweep (Phase L) (2026-05-13)

Re-auditoría comp-3 con dos lentes complementarios:
- **Phase K — Council** sobre identity.md (el único file operacional sin council previo). Verdict BLOCK + decisión arquitectural: delete + merge anchor a README "Built by". Repo pasa de 5-slot ICM contract a 4-slot.
- **Phase L — Adversarial-review** sobre los 9 files restantes (rules.md + AGENTS.md + reference/* las 7). 3-agent finder→debunker→referee. 18 REAL bugs adjudicados + 18 false positives + 5 LOW deferred.

Total: 22 issues addressed (9 council findings → identity.md delete; 13 adversarial fixes; 5 adversarial deferred) en ~3 hs wall-clock.

### Architectural change

Repo pasa de **5-slot ICM contract** (identity / rules / examples / reference / README) a **4-slot ICM contract** (rules / examples / reference / README). Alineado con pattern Voiceprint-winner comp-3 (identity ultra-minimal de Ruben). Each file does one job; nada duplica otro.

### Council findings que motivaron la deletion

| # | Severidad | Hallazgo |
|---|-----------|----------|
| 1 | 🔴 FATAL L14 | Factual inversion. SITER fue creado por RG 3421/2012 (Título II), NO por RG 4298. RG 4298/2018 *modificó* SITER. Fraseado actual leía como si RG 4298 creó SITER como sub-régimen — wrong direction. |
| 2 | 🔴 FATAL L15 | Overclaim regulatorio. VASPs son CNV-registered (Res. 1058/2025) y reportan a CNV; AFIP/ARCA gana visibilidad via cross-check SITER + RG 3421 banking flow, NO via direct VASP→AFIP reporting. Internal incoherence con L14 dentro del mismo scroll. |
| 3 | 🟡 VOICE L15 | "Cerraron como opción ética" — único slip a branding. Marina/Diego/Federica nunca moralize sus lane choice; cost-out audit risk. |
| 4 | 🟡 VOICE L46 | "Refusa" no es vocabulario AR consultor. Real: "no toca / no recomienda". El Outsider council: "ese verbo lo escribió alguien pensando en prompts de LLM, no clientes". |
| 5 | 🔴 STRUCTURAL | Esquizofrenia de voz: primera persona ("Soy un operator") + tercera persona ("el specialist refusa") dentro del mismo file. Toca misrepresentation si distribuido como bio de humano vs spec de herramienta. |
| 6-9 | 🟢 DUPLICATION | ~50% del file duplicaba rules.md (refusal, confidence, mode triage) + README (positioning, "what it won't do", calibration). Violaba el propio principio "single source of truth" del repo. |

### Files modified

- `identity.md` — **DELETED**. 52 LOC removidas. Anchor de credibilidad ya presente en `README.md` § Built by (L331-335, intacto desde v1.0).
- `README.md` — 5 references a identity.md removidas: ICM 5-slot → 4-slot (L87-97), directory tree (L137-145), file table (L202-215), Path B auto-read list (L267), forking guide (L317).
- `AGENTS.md` — 2 references removidas: read order #1 (identity.md → rules.md ahora #1, others shifted up), precedence chain (`rules.md > identity.md > examples.md` → `rules.md > examples.md`).
- `identity-examples/voice-tics-pending.md` — items 4 (Nico coherence vs operator chaos) y 5 (identity.md em-dashes legacy) marked **RESOLVED via deletion**.
- `identity-examples/MARINA-AUDIT.md` — appended Phase K section con full audit trail: council inputs, 5 findings classified, meta-reviewer peer review, Chairman verdict BLOCK, decision rationale, remediation table, verification post Phase K, 3 lecciones nuevas (acumulado 19 → 22).

### Lecciones nuevas (acumulado 19 → 22)

- **20. Council post-write detecta architectural decisions, no solo edits.** Value highest de Phase K no fueron los findings 🔴/🟡 directos sino la "what none saw" question del meta-reviewer que cuestionó el supuesto de que identity.md deba existir. ROI: 45 min audit → eliminó 52 LOC de superficie + 2 errores factuales + 50% duplicación + risk de misrepresentation. Negative result aprovechable: cuando el council sugiere "delete this entire artifact" y reduces surface > upside marginal, aceptar.
- **21. Distribution-facing files con primera-persona claims técnicas requieren bar más alto que internal artifacts.** Si un file se firma "Soy un operator argentino" Y se distribuye públicamente (repo, Pareto contact, judge cold-read), las claims técnicas dejan de ser outputs del specialist y pasan a ser afirmaciones del autor. Bar factual irreproachable o el file debe estar en tercera persona / no existir.
- **22. ICM 5-slot contract no es dogma.** Jake Van Clief's ICM canonical es "identity / rules / examples / reference / README", pero Voiceprint ganó comp-3 con identity ultra-minimal. Bar real ICM: "each file does one job well", no "todos los slots full". ICM honestidad > ICM completeness.

### Verificación post Phase K

| Check | Result |
|-------|--------|
| identity.md exists | ❌ deleted ✅ |
| grep identity.md en source files (excluding CHANGELOG/MARINA-AUDIT historical) | 0 references ✅ |
| README "Built by" intacto y único source de credibility | ✅ L331-335 |
| AGENTS.md read order sin identity.md, coherente | ✅ rules.md #1 |
| voice-tics-pending.md items 4, 5 marcados RESOLVED | ✅ |
| voice-tics-pending.md items 1, 2, 3, 6 mantenidos deferred | ✅ (no relacionados a identity.md) |
| identity-examples/* (Marina/Diego/Federica) intactos post-Phase K | ✅ 0 changes |

### Phase L — Adversarial-review (regression check sobre los 9 files restantes)

Files reviewed: `rules.md`, `AGENTS.md`, `reference/usd-routing-options.md`, `reference/monotributo-categorias.md`, `reference/audit-response-playbook.md`, `reference/glossary.md`, `reference/intake-checklist.md`, `reference/afip-audit-signals.md`, `reference/mode-triage.md`.

3-agent flow (finder over-reports → debunker challenges → referee adjudicates with ground truth):

- **Finder**: 36 bugs reported (0 CRITICAL, 10 MEDIUM, 26 LOW). 76 puntos.
- **Debunker**: 13 CONFIRMED, 19 DISPROVED, 4 UNCERTAIN.
- **Referee**: 18 REAL bugs, 18 FALSE POSITIVES (Debunker correct on 18/19, wrong on 1 — BUG-016 VASP reporting where Referee verified RG 3421 obligated-subjects against regulatory text and confirmed Finder's claim).

#### Phase L fixes aplicados (13 de 18 — los más actionable)

**MEDIUM (3):**

- **BUG-010** `reference/monotributo-categorias.md` — USD equiv column renamed "USD equiv. operativo @ MEP 1.418" + new footnote explicit que AFIP cat-math usa BCRA Comunicación A 3500 (~oficial), no MEP. Sample: cat F = $27,251 @ MEP vs $27,701 @ oficial. Resuelve self-contradiction con L47 (que dice oficial pero table usaba MEP).
- **BUG-016** `reference/usd-routing-options.md:202` — Rewrote RG 3421 reporting framing. Old: "RG 3421 obliga a bancos, brokers, VASPs y entidades financieras a reportar a ARCA". New (corrected per Referee regulatory verification): "RG 3421 obliga a bancos, brokers y entidades financieras... Las VASPs son sujeto separado: registradas en CNV bajo Res. 1058/2025 y obligadas a reportar a CNV; ARCA gana visibilidad indirecta via cross-match con flujos bancarios reportados bajo RG 3421 + algorithmic matching." Esto valida retrospectivamente la decisión de Phase K (identity.md L15 "VASPs reportan a CNV+AFIP" era ambiguo / overclaim).
- **BUG-031** `rules.md:197` — Mode-lock closing line ahora tiene EN + ES variants atomic per § Critical: Output Language.

**LOW (10):**

- **BUG-001** `reference/audit-response-playbook.md:93+` — "Cuándo escalar a contador" reescrito con hard-stop language.
- **BUG-002** `reference/audit-response-playbook.md` — Added new "Precedencia de escalación" section arriba de las dos listas. Resuelve overlap en "presunción de evasión" y "plazo": abogado tributarista gana siempre cuando aplica trigger; plazo decide ambigüedad (<5d → abogado, 5-10d → contador, >10d → contador).
- **BUG-003** `AGENTS.md` — Added `reference/glossary.md` al read order como #5 con justificación operacional.
- **BUG-009** `reference/glossary.md:11` — Cat-K USD ceiling ahora cita dual anchor (MEP $76,415 + oficial $77,675) con cross-ref a `monotributo-categorias.md` rate-anchor caveat.
- **BUG-017** `rules.md:128-138` — Routing Options table tiene "illustrative for English-output context" note + cross-reference al ES-anchored equivalent en `reference/usd-routing-options.md`. Resuelve cross-file label inconsistency framing.
- **BUG-019** `rules.md:38-48` — Full audit-pack label translation: INVOICE→FACTURA, SIGNALS→SEÑALES, RATIONALE→FUNDAMENTO, CONFIDENCE→CONFIANZA, SNAPSHOT→COTIZACIÓN, TRIGGER→CRITERIO. Resuelve atomic-language violation in canonical label table.
- **BUG-020** `reference/usd-routing-options.md:202` — "catched" → "detectados" (en mismo edit que BUG-016).
- **BUG-021** `reference/monotributo-categorias.md` table — Added explicit "USD X" notation alongside Spanish-thousands format ("~$7.250 (USD 7,250)"). Disambigua cross-locale parsing (US readers no malinterpretan $7.25).
- **BUG-024** `reference/monotributo-categorias.md:11` — Clarified "ajuste 14,28% IPC 2H 2025 — la fila K refleja la 14,30% aritmética post-redondeo". Pre-empt math-checker confusion.
- **BUG-034** `reference/afip-audit-signals.md:22` — Rewrote "libro IVA digital opcional" clause: monotributistas NO están obligados a Libro IVA Digital; el desvío FX queda en reconciliación interna, no en libro AFIP.

#### Phase L deferred (5 LOW — interpretive / minor)

Documentados con razón explícita en `identity-examples/MARINA-AUDIT.md` § Phase L. Candidatos a v1.0.4 si surge bandwidth o si próximo external review los flagea:

- **BUG-007** `mode-triage.md` + `rules.md:72` — "Routing Mode (default)" vs "Never silently default" semantic tension. Decisión de diseño, no fix mechanical.
- **BUG-008** `usd-routing-options.md:107` — $20K Mercury arithmetic ~7K ARS off post-recompute. Within "~" rounding pero math estricta no cierra. Defer recomputación full.
- **BUG-011** `usd-routing-options.md:54` — Wise mid (1.385) shown below oficial (1.395) sin explicit cost-vs-friction reasoning. Trade-off real está documentado a la siguiente línea pero podría explicitarse más.
- **BUG-013** `usd-routing-options.md:71` + `afip-audit-signals.md:60` — "$50K USD acumulado" Bienes Personales threshold sin cita a Ley/Decreto. Cross-file consistent. Defer hasta verificar Bienes Personales mínimo 2026 contra fuente oficial.
- **BUG-014** `usd-routing-options.md:235-241` — Decision tree branch ordering: VASP+USDT path skips volumen >$10K check. Defer restructure.

#### Phase L false positives (18, adjudicated)

BUG-004, 005, 006, 012, 015, 018, 022, 023, 025, 026, 027, 028, 029, 030, 032, 033, 035, 036. Mayoría son design decisions documentadas, redundant flags, o assumptions del Finder no válidas (cubierto en MARINA-AUDIT.md § Phase L).

### Files modified (Phase K + Phase L)

- **DELETED**: `identity.md` (Phase K).
- **MODIFIED**: `README.md` (5 spots Phase K), `AGENTS.md` (3 spots: 2 Phase K + 1 Phase L), `rules.md` (3 fixes Phase L: BUG-017, BUG-019, BUG-031), `reference/usd-routing-options.md` (2 fixes Phase L: BUG-016+020 same edit), `reference/monotributo-categorias.md` (3 fixes Phase L: BUG-010+021+024 same edit), `reference/audit-response-playbook.md` (2 fixes Phase L: BUG-001+002), `reference/glossary.md` (1 fix Phase L: BUG-009), `reference/afip-audit-signals.md` (1 fix Phase L: BUG-034), `identity-examples/voice-tics-pending.md` (items 4 + 5 RESOLVED Phase K), `identity-examples/MARINA-AUDIT.md` (Phase K + Phase L sections appended).

### Lecciones nuevas (acumulado 19 → 26)

- **20. Council post-write detecta architectural decisions, no solo edits** (Phase K).
- **21. Distribution-facing files con primera-persona claims técnicas requieren bar más alto que internal artifacts** (Phase K).
- **22. ICM 5-slot contract no es dogma** (Phase K).
- **23. Adversarial-review como regression check post-council es complementario** (Phase L): council escala issues a "architecture"; adversarial baja issues a "spec-line". Los dos lentes son complementarios; usar ambos en files críticos = mejor cobertura.
- **24. Cross-pollination Phase K → Phase L produce valor compounding** (Phase L): el Finder Phase L heredó el risk hunt explícito del Phase K (SITER framing, VASP reporting flow). Esto permitió que detectara el mismo error VASP-reporting en usd-routing-options.md:202 que había llevado al BLOCK de identity.md. Pattern: cada audit Phase debería leer findings de Phases anteriores ANTES de risk hunt.
- **25. Adversarial Debunker false dismissal cost real** (Phase L): el Debunker disproved BUG-016 con argumento técnicamente plausible. Si el Referee no hubiera verificado contra source regulatorio independiente, el bug se habría false-positive-dismissed. Lesson: Referee SIEMPRE necesita acceso al ground truth real.
- **26. Finder 18/36 precision rate (~50%) = healthy over-report**: si Finder reporta >40 bugs en <500 LOC, está hallucinating; <10 sugiere under-coverage. 20-40 = healthy. Aceptable porque Referee discriminates correctly.

### Verificación post-v1.0.3 (Phase K + Phase L combined)

| Check | Result |
|-------|--------|
| identity.md exists | ❌ deleted ✅ |
| grep identity.md en source files (excluding history) | 0 references ✅ |
| README "Built by" intacto | ✅ |
| AGENTS.md read order: rules.md #1, glossary.md #5 added | ✅ |
| voice-tics-pending.md items 4, 5 RESOLVED | ✅ |
| BUG-016 fix: VASPs framing corrected en usd-routing-options.md:202 | ✅ |
| BUG-010 fix: monotributo USD equiv has rate-anchor footnote | ✅ |
| BUG-031 fix: mode-lock closing has EN+ES variants | ✅ |
| BUG-001+002 fix: audit-response-playbook tiene precedence rule + hard-stop wording | ✅ |
| BUG-019 fix: audit-pack labels fully translated ES | ✅ |
| BUG-009 fix: glossary cat-K dual anchor | ✅ |
| BUG-017 fix: rules.md routing table tiene EN-context note | ✅ |
| BUG-020 fix: "catched" → "detectados" | ✅ |
| BUG-021+024 fix: monotributo table improvements | ✅ |
| BUG-034 fix: libro IVA digital framing corregido | ✅ |
| BUG-003 fix: glossary en AGENTS.md read order | ✅ |
| 5 LOW deferred documentados | ✅ |
| 18 FALSE POSITIVES catalogados | ✅ |

### Pendiente post-v1.0.3

- ✅ NONE blocking pre-Pareto contact.
- 🟡 Opcional iteración futura (v1.0.4 candidate): extraer FALR framing (FX/Audit/Liquidity/Reporting) + las 5 beliefs (que vivían en identity.md L13-17 deleted) a LinkedIn post separado, **con factual fixes Phase L ya aplicados** (especialmente BUG-016 VASP reporting). Pattern El Expansionista capturado para futuro. Ahora SÍ es seguro extraer porque los factual errors fueron corregidos en Phase L.
- 🟡 Phase L deferred (5 LOW): BUG-007, BUG-008, BUG-011, BUG-013, BUG-014. No bloquean; promote a v1.0.4 si surge bandwidth o si external review los flagea.

---

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
