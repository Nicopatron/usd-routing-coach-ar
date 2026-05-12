# AFIP Audit Signals — Triggers que aumentan probabilidad de auditoría

**Calibrado mayo 2026.** AFIP / ARCA enforcement 2025-2026 está en modo restrictivo: RG 3421/2012 (régimen unificado de información financiera, modificado por RG 4298/2018 que redefinió la sub-sección de transacciones económicas relevantes — SITER) + actualizaciones de umbrales RG 5512/2024 y RG 5699/2025 + algorithmic matching + RG 5616/2024 (e-invoicing) + RG 5700/2025 (Consumer-ID ≥10M ARS) + RG 5824/2026 (liquidación electrónica mensual + ampliación de obligados, vigencia julio 2026) → menos zona gris, más auditoría algorítmica.

**Job de este file:** documentar qué signals disparan auditoría, para que Routing Mode los identifique y los flagee en su recomendación + audit-pack.

**Para Audit Response Mode** (qué hacer cuando ya recibiste la notificación), ver `reference/audit-response-playbook.md`.

---

## Top 3 mistakes que disparan auditoría (frecuencia + severidad real)

### Mistake #1 — Invoice-FX mismatch

**Qué es:** facturás $5K USD a 1.395 ARS oficial el día de emisión, pero declarás esa Factura E al tipo de cambio del cobro (1.450 dos semanas después). El sistema AFIP auto-valida invoice metadata contra inflows reportados — la inconsistencia es detectable algorítmicamente.

**Severity:** alta. Penalty 25-75% del monto desfasado + intereses + back-tax. Cross-check ARCA (SITER + RG 3421) flagea automático en 3-6 meses.

**Cómo se evita:**
- Emitir Factura E en USD con cotización oficial AFIP del día de emisión.
- Reconciliar el dato del Wise statement contra la Factura E al cierre de mes.
- Si hay diferencia FX entre emisión y cobro, eso es ganancia/pérdida de cambio. En RI se imputa como renglón aparte de Ganancias / Bienes Personales (y el RI con Libro IVA Digital obligatorio lo registra ahí). En monotributo no afecta directamente la cat porque la cat se calcula sobre el monto de Factura E al tipo de cambio del día de emisión (no sobre el cobro real); el desvío FX queda en tu reconciliación interna, no en un libro contable AFIP — el monotributista no está obligado a Libro IVA Digital.

### Mistake #2 — Factura C (doméstica) a cliente foreign

**Qué es:** emitís Factura tipo C (régimen doméstico) cuando el cliente es no-residente. Type B para clientes locales finales, type A para empresas locales registradas, type E para exportación. Mezclar = audit trigger.

**Severity:** alta. Reclasificación a IIBB (gross income) provincial sin la exención de exportación. Pérdida del beneficio export = potencial salto de cat o forzado a RI.

**Cómo se evita:**
- Siempre Factura E para no-residentes.
- Verificar que el campo "país del receptor" esté correcto en el sistema AFIP.
- Mantener contrato firmado con el cliente externo on file (sirve como respaldo de export-service).

### Mistake #3 — Cash deposits sin invoice trail correspondiente

**Qué es:** declarás $3K USD/mes en monotributo via Factura E, pero hacés deposits cash adicionales (referidos, freelance side, friends-and-family) por otros $1-2K USD/mes en pesos. SITER reporting + RG 3421 cuentas bancarias + algorithmic deposit-vs-income matching te encuentra.

**Severity:** muy alta. ARBA/AFIP pueden disallowed full monotributo deduction + reclasificación + criminal referral si hay evidencia de intencionalidad.

**Cómo se evita:**
- Cada ingreso requiere Factura. Sin excepciones.
- Side-projects = segunda actividad code o aceptar que entran al mismo monotributo bucket (sumando para el límite de cat).
- Cash recibido informal (regalo familiar, devolución personal) tiene que tener fundamento documentable distinto a "ingreso".

---

## Otros triggers comunes (frecuencia menor pero relevantes)

### Salto sostenido de invoicing sin recategorización

Si pasás de cat F a cat H de un mes a otro (doble de invoicing) y no recategorizás dentro de 30 días, AFIP detecta y te recategoriza ellos con multa.

### Multiple monotributo registrations sin actividad clara

Tener múltiples actividades dentro de monotributo es legal pero requiere coding distinto. Si todas tus actividades están bajo el mismo code (ej: "consultoría informática") pero el flujo sugiere actividades distintas (consultoría + venta productos digitales + alquileres), audit trigger.

### Holding USD sustancial sin justificación

Mantener Wise USD account (o cualquier activo en exterior) sin declarar en Bienes Personales cuando tu patrimonio total supera el mínimo no imponible es audit trigger. **Mínimo no imponible 2026 (fiscal year 2025): ARS 384.728.044,57** (~$271K USD @ MEP 1.418), oficializado por ARCA en el marco de actualización automática por inflación. Patrimonio total = Wise + AR bank balances + propiedades + auto + crypto en VASP + otros activos al 31/12. Casa habitación exenta hasta ARS 1.346.548.155,99. Pre-BCRA-liberalization 2025 era más estricto (Cuenta CERA reporting + percepción 35% RG 4815); post-liberalization el régimen de Bienes Personales sigue vigente con los thresholds actuales. Source: [ARCA Bienes Personales — Alícuotas](https://www.afip.gob.ar/gananciasYBienes/bienes-personales/conceptos-basicos/alicuotas.asp). Vencimiento DDJJ 2025: junio 2026.

### Crypto receipts sin tax basis documentation

USDT recibido sin valuación al oficial del día de recepción documentada = AFIP escrutinio. CNV obliga a VASPs a reportar; si tu estatement de la VASP no matchea con tu declaración mensual, flag.

### Platform payments sin compliance withholding

Deel, Payoneer, Upwork pueden aplicar withholdings propios según su lógica interna y residencia (p.ej. 1099 reporting si hay U.S. tax nexus). NO hay un RG argentino específico que extienda withholding a estas plataformas para consultores AR (RG 5319/2023, a veces mal citada para esto, es un régimen de percepción IVA sobre portales virtuales locales tipo Mercado Libre y excluye explícitamente a monotributistas). Si tu net cobrado no matchea con el bruto declarado, eso por sí solo es audit trigger — independientemente del origen del withholding.

---

## Calibration sources

- AFIP RG 5616/2024 — Foreign-Currency E-Invoicing
- ARCA RG 5824/2026 — Liquidación electrónica mensual + ampliación de obligados a facturación electrónica (vigencia July 2026)
- ARCA RG 5700/2025 — Consumer-ID threshold ≥10M ARS (vigente desde mayo 2025)
- CNV Resolución 1058/2025 — VASP Registration
- BCRA Comunicaciones 8226+ — FX market liberalization
- KPMG flash alert 2026/015 — statute of limitations changes
- Reddit r/devsfinanzas — practitioner audit experiences (May 2026)

Si la fecha actual >Aug 2026 y no hay refresh, el specialist flagea antes de aplicar este file en routing decisions.
