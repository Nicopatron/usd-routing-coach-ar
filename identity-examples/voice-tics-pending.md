# Identity examples — Voice tics pending

Items captured during use of the specialist with operators matching one of the three identity profiles (Marina cat F single-anchor, Diego cat I→K RI-transition, Federica post-vista audit-response).

**Promotion rule:** promote a tic to the canonical identity file when 3+ instances observed across distinct sessions, or when the tic measurably affects routing-output quality (e.g., specialist starts using "SIRA" again when SITER is the correct term post-2023 derogation, or operator vocabulary shifts faster than the identity file).

**Audit-trigger refresh:** every Feb / Aug recategorización window, sweep this file and promote items to the relevant identity-examples file.

---

## Pending observations

**Date observed:** 2026-05-12
**Profile:** transversal (los 3 identity files)
**Tic / phrase:** Sec 4 "Voice in one sentence" abre con tercera persona referencial uniform — Marina ("Marina ya pasó por dos recategorizaciones..."), Diego ("Diego opera bajo presión asimétrica..."), Federica ("Federica está en el medio de una vista AFIP...").
**Context:** detectado por adversarial reviewer del re-audit 2026-05-12. Pattern procedural del template aplicado tres veces, no orgánico de cada voz. Lectura side-by-side de los 3 lo expone como tic. El Ejecutor del council lo identificó como "convención de template, no bug" — defendible pero detectable.
**Type:** structure / template artifact
**Action:** wait for next identity file (4to operator) — si también arranca con tercera persona referencial uniform, refactor template a primera persona o factual neutral. Promotion target: si se confirma, externalizar regla a `rules.md` § Identity file conventions o reescribir los 3 Sec 4 existentes en primera persona.

---

**Date observed:** 2026-05-12
**Profile:** transversal (los 3 identity files)
**Tic / phrase:** "Em dashes anywhere" como banned-words bullet duplicado literal en Sec 6 de marina.md, diego.md, federica.md.
**Context:** detectado por adversarial reviewer del re-audit 2026-05-12. Regla de formato del repo (Voiceprint Rule 2), no característica de voz de cada persona. El Ejecutor del council lo identificó como cosmético, lector no compara Sec 6 lado-a-lado. Pero técnicamente es voice-file polluted con repo policy.
**Type:** banned-word policy bleed
**Action:** wait for next identity file — si también lo duplica, externalizar a `rules.md` § Banned words y dejar Sec 6 de cada identity file solo con banned-words específicos a la persona (advisor-speak, jargon profesional irrelevante, etc.). Mientras tanto, mantener consistency.

---

**Date observed:** 2026-05-12 (post-Phase F greenlight check)
**Profile:** federica
**Tic / phrase:** post-Phase A (Upwork-Payoneer diagnosis fix), Federica se sintió "más pedagógica que persona" para el consultor AR re-impersonado (Marcelo). Verdict directo: "vive en loop emocional del descargo... construida para enseñar el playbook, no orgánica."
**Context:** trade-off explícito conocido. El re-audit detectó que Federica como flagship del Audit Response Mode NO diagnosticaba la causa probable de su propia vista (fatal flaw del Contrario). Phase A fix agregó la diagnosis Upwork-Payoneer en federica.md Theme 1 + Sec 6 Vocabulary + Sec 1 Background + Example 3 diagnosis section. Eso resolvió el fatal flaw pero empujó la voz hacia "vehículo de enseñanza del playbook". Diego salió de "charlatán" (pre-fix) a "con asterisco" (post-fix); Federica fue de "en el medio" a "NO la paso a un colega". Trade-off neto: + flagship case completo / − Federica como persona auténtica.
**Type:** structural trade-off (pedagogical clarity vs personal authenticity)
**Action:** wait — re-evaluar si futura iteración de identity files puede separar mejor "operator persona" de "case study vehicle". Posible refactor: dejar `federica.md` más naked (menos diagnosis-pedagogy) y mover el diagnosis playbook a `reference/audit-response-playbook.md` § Upwork-flow mismatch pattern. Sin acción inmediata — el repo ya pasó dos rondas de audit + remediation y la trilogía cumple su función como composite illustrative de 3 stages distintos del journey.

---

**Date observed:** 2026-05-12 (Marcelo post-Phase F)
**Profile:** transversal (los 3 identity files)
**Tic / phrase:** Marcelo: "los tres tienen el mismo nivel de articulación sobre su propia operación. En la vida real, nadie es tan consciente de su propio voice pillar. Falta uno que sea más caótico, más contradictorio."
**Context:** meta-finding sobre el formato Voiceprint identity-file aplicado a operator profiles. Los 11 secciones template fuerzan articulación uniforme — Marina puede decirlo en su martes-a-la-tarde, Diego en su pricing-aware, Federica en su contador-first. En operadores reales esa coherencia es rara: la mayoría tiene un voice pillar declarado y dos o tres tensiones no resueltas. Limitación del template adoptado, no de la implementación.
**Type:** template limitation
**Action:** ✅ **RESOLVED via deletion (Phase K, 2026-05-13)**. ~~wait — si próximo identity file (4to operator) puede experimentar con "voz menos articulada"...~~ No aplica: identity.md (Nico-as-operator) fue deletado en Phase K post-council audit. La concern original era que faltaba un 4to operator caótico para balancear los 3 composites articulados; con identity.md deletado, los 3 composites quedan como referencia explícita ("composites by design" disclaimer en README L62) y el 4to slot ya no se necesita.

---

**Date observed:** 2026-05-12 (post-Phase D verification)
**Profile:** N/A (operator único, no de identity-example)
**Tic / phrase:** `identity.md` (Nico operator) contiene 11 em-dashes pre-existentes desde antes del Phase 1 remediation. Voiceprint Rule 2 (anti em-dash) aplica enforcement-strict a `identity-examples/marina.md`, `diego.md`, `federica.md` (specs de personas distinguibles) — los 3 están en 0/0/0. Pero `identity.md` quedó con su voice narrativa original.
**Context:** detectado durante Phase D verification. Phase D.1 limpió solo L14 (el em-dash dentro del fix de cross-reference); los otros 10 son legacy del repo pre-iteración. Decisión registrada: out-of-scope para esta closeout. Si el target audience real (consultor AR cat F→G) flagea identity.md em-dashes en futura lectura, considerarlos. Mientras tanto, Voiceprint Rule 2 enforcement queda en identity-examples/ donde fue diseñada.
**Type:** scope decision (consistency identity-examples/ vs identity.md)
**Action:** ✅ **RESOLVED via deletion (Phase K, 2026-05-13)**. ~~wait — si próximo external review...~~ identity.md fue deletado en Phase K. Sweep de em-dashes no aplica al file que no existe. Phase I había hecho sweep 11→0; Phase K eliminó el file completo. Voiceprint Rule 2 enforcement queda en identity-examples/* (donde fue diseñada originalmente) sin conflicto cross-file.

---

**Date observed:** 2026-05-12
**Profile:** N/A (artifact del worked example, no de identity file)
**Tic / phrase:** Confidence breakdown Example 2 (Diego) tiene patrón "+8% sostiene la lane" vs "−9% margen modesto" — tensión narrativa débilmente resuelta. La aritmética cuadra (+20+10+8−8−9−9 = +12 sobre baseline 60 = 72%) pero los bullets +8 y −9 dicen lo mismo en signos opuestos.
**Context:** detectado por adversarial reviewer del re-audit. Phase B remediation resolvió el verdict matiz ("Mercury+MEP o Deel") pero el pattern de confidence math con bullets contradictorios sigue presente — el operator que lo lea cuidadosamente puede notar la tension.
**Type:** confidence calibration mechanics
**Action:** wait for next worked example con confidence breakdown — si otros muestran el mismo pattern (+N% feature / −N% same feature debilitada), refactor mecánica de bullets en `rules.md` § Confidence Calibration para forzar un eje claro por bullet (no doble-cubrir el mismo signal con polaridad opuesta).

---

Format when added:

```
**Date observed:** YYYY-MM-DD
**Profile:** marina / diego / federica
**Tic / phrase:** "..."
**Context:** what the operator said, what the specialist said back
**Type:** vocabulary | voice pillar | content theme | banned-word slip
**Action:** wait for more instances / promote to [file] § [section]
```

---

## Promoted to identity files

_None yet._

Format when promoted:

```
**Date promoted:** YYYY-MM-DD
**Source observations:** [dates listed]
**Target file + section:** identity-examples/marina.md § 6. Vocabulary
**Final wording added:** "..."
```

---

## Cross-references

- Voiceprint Rule 11 source pattern: `analysis/voiceprint-winner/voice-tics-pending.md`
- Marina identity file: `marina.md`
- Diego identity file: `diego.md`
- Federica identity file: `federica.md`
