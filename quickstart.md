# Quickstart

For people who don't read READMEs.

1. Open `claude.ai` → **New Project** → upload all the `.md` files in this folder (root + `reference/`) into **Project knowledge**.
2. Open a new chat in that project.
3. Paste your situation with these 5 inputs:
   - Monotributo category (A-K, RI, or unregistered)
   - USD volume / month last 3 months (range OK)
   - This invoice details (amount USD + client country + payment options the client offers)
   - IIBB jurisdiction (CABA / PBA / interior / N/A if export-services)
   - Banking infrastructure (Wise yes/no, Mercury yes/no, broker yes/no, VASP-registered crypto yes/no)
4. Ask: **`Synthesize this routing decision.`**
5. Read the structured 6-section output + audit-pack shadow artifact (~900-1100 words). Iterate with: *"draft just the audit pack,"* *"compare MEP vs Wise for this volume,"* *"if I switch to RI next quarter, how does this change."*

**Testing without a real invoice:** paste any of the worked syntheses from `examples.md` (Marina, Diego, Federica, Juan) into your project chat. Each is self-contained and produces the same output shape you'd get with your own invoice.

---

**Bilingual auto-detect.** Spanish input → Spanish output (Rioplatense). English input → English output. Mixed-language with no dominant → English by default.

**Four modes auto-detected:**
- **Routing** (default) for invoice decisions
- **Audit Response** if you paste an AFIP vista / intimación / requerimiento — switches to defensive playbook, no routing recommendation
- **Year-End Reconciliation** if you paste annual summary or RI transition question
- **Pattern Memo** after 3+ Routing decisions in the same conversation, OR explicit ask

**Refuses to synthesize when intake is too thin.** If 4 of 5 core inputs are missing, the specialist asks for the gaps in one short message instead of guessing. See `examples.md` Example 5 for what that refusal looks like.

**Refuses to recommend informal channels** (blue dollar cuevas, unregistered crypto P2P) — even if you ask. AFIP enforcement post-May-2025 closed those windows; the specialist will not pretend otherwise.

**Calibrated as of mayo 2026** against AFIP RG 5616/2024, RG 5824/2026, CNV 1058/2025, BCRA Comunicaciones 8226+. If today's date >Aug 2026, the specialist flags before any recommendation.

**Full README** at `README.md` (methodology, file map, glossary, source citations, how to fork for your country's tax landscape).
