# Glossary

Reference vocabulary for this specialist. Two layers: (1) Argentine regulatory + financial terms used throughout the specialist's outputs and reference files; (2) specialist-internal terminology used in `rules.md` and `AGENTS.md`. The specialist consults this file to ground definitions in outputs and to disambiguate user input.

---

## Layer 1 — Argentine regulatory / financial vocabulary

### Tax regimes

- **Monotributo** — Argentine simplified tax regime for small contributors (self-employed, freelancers). Single monthly fee covers income tax, social security, and healthcare. Cats A-K with annual billing limits as of February 2026 recategorización. Cap: cat K (~$76,415 USD/year at MEP 1.418). Above cat K → forced transition to RI.
- **Cat A through K** — Monotributo categories ranked by annual billing volume. See `monotributo-categorias.md` for current thresholds. Recategorization windows: February and August every year.
- **RI (Responsable Inscripto)** — Argentine general tax regime. Required when monotributo K ceiling is exceeded or when activity is incompatible with monotributo (e.g., sociedades, real estate). Includes IVA monthly + Ganancias annual filings. Higher administrative cost (~$80-150 USD/month contador), no automatic ceiling.
- **Recategorización** — Periodic monotributo cat reassignment based on rolling 12-month invoicing. Two windows per year: February and August.
- **Factura E** — Argentine export invoice type, used for services or goods sold to non-resident clients. IVA-exempt under export regime. Required for legal USD invoicing to foreign clients. Setup via AFIP portal.

### Tax authorities and regulators

- **AFIP / ARCA** — Argentine federal tax authority. Renamed from AFIP (Administración Federal de Ingresos Públicos) to ARCA (Agencia de Recaudación y Control Aduanero) in October 2024. Both names still in active use; reference files use AFIP for continuity. Regulates monotributo, Factura E, RG issuances.
- **CNV (Comisión Nacional de Valores)** — Argentine Securities Commission. Regulator for VASPs (crypto exchanges) since CNV Resolución 1058/2025. Mandates registration for all crypto platforms operating in Argentina.
- **BCRA (Banco Central de la República Argentina)** — Argentine Central Bank. Regulator of FX market access. Issues Comunicaciones that govern legal USD/ARS conversion lanes (oficial, MEP, CCL).
- **IIBB (Ingresos Brutos)** — Argentine provincial gross-income tax. Each province sets its own rates and exemptions. Most monotributistas-export are exempt under federal export-services regime, but verify per-province rules.
- **Convenio Multilateral** — Cross-jurisdictional IIBB allocation rule when services are rendered to clients in multiple Argentine provinces. Relevant only for mixed local-export practices.

### FX market routes

- **Tipo de cambio oficial** — Official exchange rate set by BCRA. Most restrictive rate; used for AFIP-mandated invoice cotización (exchange rate quote).
- **MEP (Mercado Electrónico de Pagos)** — Legal Argentine FX route via Argentine sovereign bonds (AL30, GD30 typical). Buy bonds in USD, sell in ARS; difference between buy and sell rate is the spread captured. Better rate than oficial; requires broker.
- **CCL (Contado con Liquidación)** — Variant of MEP for offshore settlement (USD lands abroad, not in local Argentine bank). Used when the operator wants USD to stay in foreign account.
- **Cueva** — Informal FX house. Operates outside legal channels (blue dollar). **The specialist refuses to recommend cueva routing under any circumstances.**
- **Blue dollar** — Informal market USD price, traded via cuevas. Higher rate than oficial, but post-SIRA enforcement (2025+) carries severe audit risk.

### Banking and payment infrastructure

- **Wise** — UK-based fintech offering multi-currency accounts. Standard lane for low-volume Argentine consultores invoicing US/EU clients. All-in cost ~1.5-2.5%.
- **Mercury** — US-based bank for startups and freelancers. Used for higher-volume invoicing where MEP route via broker is justified.
- **Deel** — Global payroll/contractor platform. Direct ARS payment to Argentine contractor with platform-handled CAE compliance. Net cobrado may differ from gross declarado due to platform-side U.S./EU withholdings (e.g., Deel's own residency rules, 1099 reporting if U.S. tax nexus applies); reconcile mes a mes against Factura E.
- **VASP (Virtual Asset Service Provider)** — CNV-regulated crypto platform. Mandatory registration since May 2025. Examples: Lemon, Belo, Buenbit, Binance Argentina. Required for any compliant USDT routing.
- **Lemon, Belo, Buenbit, Binance Argentina** — CNV-registered VASPs as of May 2026. The specialist treats these as compliant USDT lanes. Other unlisted exchanges may not be CNV-registered.

### AFIP enforcement and audit terms

- **SIRA** — AFIP system that tracks bank deposits and matches against declared income via algorithmic flagging. Automated inconsistency detection. Catch-up window typically 6-12 months.
- **Vista** — AFIP communication initiating a review. Lower severity than intimación; requests documentation without alleging a specific tax debt yet. Standard response window: 15 business days.
- **Intimación** — AFIP communication formally claiming a tax debt or specific violation. Higher severity; requires immediate contador/abogado involvement.
- **Requerimiento** — AFIP general request for information. Less formal than vista or intimación; usually answerable without escalation.
- **Cuenta CERA** — Special AFIP-monitored account used during the 2024 tax amnesty. Funds held there were liberated for general use as of January 1, 2026.

### Regulations cited

- **RG 5616/2024** — AFIP regulation on Foreign-Currency E-Invoicing. Streamlined Factura E in USD.
- **RG 5824/2026** — ARCA regulation (BO 2026-02-13, vigencia 1-Jul-2026) introducing comprobantes de liquidación electrónica mensual + ampliación de obligados a facturación electrónica (directores SA, gerentes SRL, profesionales en juicios). Operationally low-impact for monotributistas exportando servicios (Factura E ya es electrónica).
- **RG 5700/2025** — ARCA regulation (BO 2025-05-27, vigente desde mayo 2025) que eleva a 10M ARS el umbral para identificar al consumidor final en facturas con DNI/CUIL/CDI/pasaporte. NO aplica a Factura E al exterior (no es consumidor final).
- **CNV Resolución 1058/2025** — CNV regulation mandating VASP registration.
- **BCRA Comunicaciones 8226+** — BCRA series since April 2025 on FX market liberalization.

### Historical context

- **Blanqueo Milei** — One-time tax amnesty 2024, closed for residents May 7, 2025. Funds liberated from CERA accounts January 1, 2026.

---

## Layer 2 — Specialist-internal terminology

These terms appear in `rules.md`, `AGENTS.md`, and reference files. Defined here for cross-reference.

- **Audit-pack** — Shadow artifact produced parallel to every Routing Mode output. Fixed format: contemporaneous record of signals analyzed, alternatives considered, decision made, FX rate snapshot, documents to retain. Designed to be saved in `AFIP/YYYY/Q[N]/` for defensive bookkeeping. See `rules.md` for canonical format.
- **Intake gate** — Pre-output verification step. Specialist confirms 5 core inputs are present (cat monotributo, monthly USD volume, this invoice details, IIBB jurisdiction, banking infrastructure) before producing any mode's synthesis. See `intake-checklist.md`.
- **Mode triage** — Auto-detection of which output mode applies to a given paste (Routing / Audit Response / Year-End / Pattern Memo). Signal patterns and decision tree in `mode-triage.md`. Runs before intake gate.
- **Mode lock** — Once a mode is selected for a conversation, it persists unless signals clearly shift. If user pastes an AFIP vista mid-routing-conversation, specialist switches to Audit Response and explicitly announces the switch.
- **Pattern Memo** — Output mode triggered after 3+ Routing decisions accumulate in the same conversation. Surfaces emergent quantitative patterns: dominant lane, cost loss vs theoretical optimum, anomalies, cat-K threshold projection.
- **RI transition** — Process of moving from monotributo to RI regime. Triggered by exceeding cat K ceiling, or proactively before forced jump. Includes IVA filings setup, contador engagement, regime change registration with AFIP.
- **Decision Trace** — Closing section of every output. 3-5 lines citing the specific input signals that drove major calls (mode detection, lane choice, confidence score, refused options). Auditable trail.
- **Override** — Explicit user request to bypass the intake gate. Format: "Dale, hacé un best-effort con lo que tenés." Specialist proceeds but caps confidence at 65% and flags every guessed line with `⚠ guessed — confirmar antes de actuar`.
- **Lane** — A routing channel for receiving USD invoices. Five viable lanes documented: Wise + Factura E, Mercury + MEP via broker, Deel + ARS direct, USDT via VASP-registered exchange, refused (informal cuevas / unregistered crypto P2P). See `usd-routing-options.md`.
- **Headroom** — Remaining annual billing capacity in current monotributo cat, calculated as `(annual ceiling - YTD invoiced)`. Drives forward-looking flags (e.g., "post-invoice cumulative reaches 70% of cat F ceiling").
- **Refusal discipline** — The specialist's three classes of refused requests: informal channels (cuevas, unregistered crypto P2P), thin intake (4+ inputs missing), out-of-scope work (sociedades SAS, IVA for RI, blue dollar as investment). Tone: operator-direct, no apology.

---

## Calibration date

**Glossary current as of May 2026.** Full citation list and forward-looking validity rule in `rules.md` § Calibration date — single source of truth.

For the most current AFIP / CNV / BCRA citations, verify against:
- AFIP: https://www.afip.gob.ar (now also at https://www.arca.gob.ar)
- CNV: https://www.cnv.gov.ar
- BCRA: https://www.bcra.gob.ar
