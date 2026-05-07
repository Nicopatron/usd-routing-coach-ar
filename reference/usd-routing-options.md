# USD Routing Options — Comparativa, Costos, Setup, Failure Modes

**Calibrado mayo 2026.** Tipos de cambio referencia: Oficial ~1.395, MEP ~1.418, CCL ~1.470, Blue cueva ~1.410, USDT VASP ~1.445 ARS/USD. Spreads se mueven semana a semana — el specialist usa estos como anchor pero confirma contra fuente live ([rueda.live](https://rueda.live/en)) antes de routing decisions de alto monto.

---

## Tabla maestra de comparación

| Option | All-in cost % | Speed | Tax visibility | Audit risk | Liquidez ARS | Confidence-OK signal |
|--------|---------------|-------|----------------|------------|---------------|----------------------|
| **Wise + Factura E (oficial)** | 1.5-2.5% | 1-2 días | Total | **Baja** | Diaria | ✓ Default para mayoría de cases |
| **Wise → USD multi-currency hold** | 0% (sin conversión) | Same day | Declarable | Baja | Postpuesta | ✓ Si no necesitás ARS ya |
| **Mercury → wire → MEP via broker** | 2-3% | 5-7 días | Total | Media | Semanal | ✓ Si volumen >$10K/mo justifica |
| **Deel → ARS direct (CAE platform)** | 2-4% | 2-5 días | Total (CAE) | Media | 1-3 días | ✓ Si Deel ya integrado por cliente |
| **USDT vía Lemon/Belo/Buenbit (VASP-registrada)** | 2-3% | <1 día | Declarable | Media-Alta | Instantánea | ✓ Solo si VASP registrado + valuación al oficial documentada |
| **Western Union** | 4-6% | 1-3 días | Declarable | Media | 1-2 días | Raro para freelancers — costo alto |
| **Payoneer** | 2-4% | 2-4 días | Declarable (con withholding 2025+) | Media | 1-3 días | OK pero verifica platform-withholding RG 5319/2025 |
| **❌ Blue dollar cueva** | 0-1% | Instantáneo | Cero | **Muy Alta** | Inmediata | **REFUSED** — ver sección Refused |
| **❌ Crypto P2P informal (cueva crypto, sin VASP)** | 0.5-1.5% | Instantáneo | Cero | **Muy Alta** | Inmediata | **REFUSED** — ver sección Refused |

---

## Wise + Factura E (default lane)

**Cuándo es óptimo:**
- Volumen mensual <$10K USD
- Cliente externo paga por Wise transfer (US ACH, EU SEPA, UK BACS)
- Necesitás liquidez ARS dentro de 5 días pero no ya mismo
- Querés trazabilidad AFIP-clean sin overhead administrativo

**Setup checklist:**

1. Cuenta Wise con USD multi-currency activada (profile personal o business — para monotributista, personal alcanza)
2. Factura E habilitada en AFIP (CAE/CAF approved) — si todavía no, este es el primer step antes de cualquier routing
3. Datos del cliente externo cargados (razón social + país + tax ID si aplica)
4. Cuenta bancaria local en pesos para retiros desde Wise (Galicia, Santander, BBVA, Mercado Pago — todos integran)

**Flujo operativo:**

1. Cliente paga $X USD a tu Wise USD account
2. Emitís Factura E #N a la razón social del cliente, por $X USD, con cotización del día (oficial AFIP del momento de emisión)
3. Wise → ARS conversion al mid-market rate cuando necesites cash (típico fee 0.5-0.8% + spread)
4. ARS llegan a tu cuenta local en 1-2 días desde la conversión
5. Reconciliá: Factura E + Wise statement + cuenta bancaria = AFIP audit-ready

**Failure modes:**

- **Factura E no emitida o emitida tarde:** AFIP detecta inflows USD sin invoice match. Disparador clásico de auditoría.
- **Cotización mal documentada:** si el día que emitís la factura era oficial 1.400 pero declaraste 1.420 (porque cobraste después), inconsistencia detectable.
- **Cliente paga con apellido distinto al de la razón social:** Wise puede flag por AML; verificar que sender = receptor de la factura.

**Cost example (May 2026):**

Invoice $5.000 USD → Wise convierte a 1.385 ARS/USD (mid-market) – 0.8% Wise fee → 6.870.000 ARS netos. Si hubieras hecho oficial-bank-direct: 6.975.000 ARS pero con audit overhead. Si MEP: 7.090.000 ARS pero con broker overhead. Para invoices <$10K, Wise gana en cost-vs-friction.

---

## Wise → USD multi-currency hold (cuando NO necesitás ARS ya)

**Cuándo es óptimo:**
- No necesitás convertir a ARS este mes (gastos en USD ya cubiertos, o esperando una compra grande tipo software/hardware/viaje)
- Querés evitar el spread de conversión hasta que el ARS rate mejore
- Mantenés balance USD como hedge contra devaluación

**Implicación tax:**

Mantener USD en Wise no es "ingreso no declarado" — el ingreso lo declarás cuando emitís la Factura E al momento del cobro. Lo que mantenés en USD multi-currency es un **activo en moneda extranjera**. Esto puede afectar Bienes Personales si excede el threshold (verifica con contador).

**Failure modes:**

- **Bienes Personales si superás threshold de activos en exterior:** Wise USD account cuenta como activo en exterior. Threshold 2026: ~$50K USD acumulado.
- **Devaluación inversa (poco probable May 2026):** Si ARS se aprecia inesperadamente, mantener USD pierde plata vs convertir.

---

## Mercury + wire + MEP via broker

**Cuándo es óptimo:**
- Volumen mensual >$10K USD
- Tenés cuenta US (Mercury, Wise Business, Brex)
- Tenés broker argentino habilitado (Grupo SBS, Invertir Online, Balanz, Bull Market)
- Aceptás 5-7 días de processing por mejor rate

**Setup checklist:**

1. Cuenta US (Mercury típicamente — apertura remota, sin SSN, requiere business entity)
2. Cuenta broker argentino (CNV-regulated, comitente account)
3. Acuerdo MEP con broker (compra dólar MEP via títulos AL30/GD30 o similar, sale a tu cuenta)

**Flujo operativo:**

1. Cliente paga a Mercury (US bank account)
2. Mercury → wire transfer a Argentine commercial bank (Galicia/Santander/BBVA en USD)
3. USD llega a tu cuenta argentina en USD
4. Operás MEP via broker: comprás títulos AL30 con USD, vendés en ARS, ARS van a tu cuenta argentina
5. Emitís Factura E al momento del cobro inicial en Mercury (no al MEP step)

**Failure modes:**

- **Wire transfer fails or delays:** US-AR wires pueden tardar 5-10 días, especialmente si la AR bank pide documentación adicional.
- **Broker compliance pide documentación:** la operación MEP por montos altos puede triggerear AML check del broker. Tener Factura E + contrato + Mercury statement listos.
- **AFIP scrutiny en MEP de alto monto:** trades MEP grandes son visibles por SIRA. Documentar el trade con fundamento (ingreso por export-service) es crítico.
- **Costo total subestimado:** wire fee ($15-25) + broker fee (~0.5-1%) + spread MEP vs oficial. Suma a ~2-3% all-in, no 1% como muchos calculan.

**Cost example:**

Invoice $20.000 USD → Mercury → wire ($20 fee) → AR bank USD account → MEP via broker (1.418 ARS/USD, 0.5% broker fee) → ~28.221.500 ARS netos. Wise alternativo daría ~27.700.000. **Diferencia: ~520.000 ARS (~$370 USD) a favor de MEP.** Solo justifica el friction si vas a hacer esto cada mes y >$15K mensuales.

---

## Deel + ARS direct (platform-issued CAE)

**Cuándo es óptimo:**
- Cliente ya usa Deel para pagar contractors
- Querés evitar el setup de Factura E porque Deel emite CAE-compliant en tu nombre
- Velocidad importa más que costo (1-3 días)

**Setup checklist:**

1. Cuenta Deel onboarded por el cliente (no podés iniciar vos sin cliente Deel)
2. Tax classification correcta en Deel (monotributo activo, cat actual)
3. Cuenta bancaria local linked

**Flujo operativo:**

1. Cliente registra el pago en Deel
2. Deel emite invoice CAE-compliant en tu nombre
3. Deel hace conversión USD → ARS con su FX
4. ARS llegan a tu cuenta en 2-5 días
5. Vos no emitís Factura E aparte (Deel ya lo hizo)

**Failure modes:**

- **Tax-class mismatch en Deel:** si tu cat monotributo cambió y no actualizaste en Deel, el CAE emitido puede tener errores.
- **Platform-withholding RG 5319/2025:** desde 2025 las plataformas digitales (incluida Deel) están sujetas a withholding regimes ampliados. Verifica el net actual mes a mes.
- **Costo Deel vs Wise:** Deel es 2-4%, vs Wise 1.5-2.5%. Deel gana en convenience (no setup Factura E), pierde en costo.

---

## USDT via Lemon / Belo / Buenbit (VASP-registered)

**Cuándo es óptimo:**
- Cliente externo prefiere pagar en USDT (común en clientes crypto-native, Web3, gaming)
- Necesitás liquidez ARS instantánea (USDT P2P es <1 hora)
- VASP elegida está registrada en CNV (Lemon, Belo, Buenbit, Ripio, Bitso, Binance Argentina están registradas a may 2026)

**Crítico — VASP registration:** Solo plataformas registradas. Plataformas no-CNV-registered = REFUSED por specialist. CNV Resolución 1058/2025 exige registro desde Aug-Sep 2025; plataformas no compliantes pueden sufrir suspensión de servicio o multas.

**Setup checklist:**

1. Cuenta en una VASP registrada (verificar status en [CNV Registro](https://www.cnv.gov.ar/SitioWeb/RegistroPSAV))
2. KYC completado (>$100K/año transactions disparan enhanced KYC desde 2025)
3. Cliente capaz de transferir USDT a tu wallet de la VASP

**Flujo operativo:**

1. Cliente transfiere $X USDT a tu wallet en Lemon (o equivalente)
2. **Documentar valuación al oficial AFIP del momento de recepción** — esto es el monto que cuenta para tu monotributo
3. Emitir Factura E al cliente externo con monto USD (tipo de cambio AFIP oficial del día)
4. Convertir USDT → ARS via P2P de la plataforma cuando necesites cash
5. Reconcilá: Factura E + VASP statement + transferencia onchain + ARS landing

**Failure modes:**

- **Valuación incorrecta del USDT al recibirlo:** debe ser oficial AFIP del día de recepción, no del día de conversión. Equivocarse aquí = invoice-FX mismatch detectable.
- **VASP cambia status de registro:** si tu plataforma pierde el registro (raro pero posible), tus operations futuras pueden quedar en zona gris. Verificar status semestralmente.
- **Travel Rule 2.0 (implementada late 2025):** transfers inter-VASP >$3K USD requieren info de pagador/receptor. Puede demorar 24-48h en casos.
- **Audit risk medium-high comparado con Wise:** AFIP escrutinio sobre crypto es más alto que sobre Wise. Documentación tiene que estar 100%, no 90%.

**Cost example:**

Invoice $5.000 USDT → Lemon → P2P sell at 1.445 ARS/USDT, fee 0.5% → 7.189.250 ARS. Wise alternativo: 6.870.000 ARS. USDT da +$220 USD pero suma audit risk + reporting friction.

---

## Western Union (raro pero existe)

**Cuándo aplica:** cliente externo prefiere WU (común en MX/CL/PE para freelancers que no tienen Wise/Mercury).

**Costo:** 4-6% all-in (fee + FX spread). Más caro que Wise, mismo audit profile.

**Failure mode:** WU reporta a AFIP transfers >umbral. Sin Factura E asociada = audit trigger.

**Recomendación specialist:** evitar salvo que cliente NO TENGA otra opción y monto sea pequeño (<$2K USD). Para mayor monto o frecuencia, mover al cliente a Wise.

---

## Payoneer

**Cuándo aplica:** clientes platform-based (Upwork, Toptal, Fiverr) suelen integrar Payoneer.

**Costo:** 2-4% (fee + FX). Comparable a Deel.

**Failure mode 2025+:** RG 5319/2025 expandió platform-withholding. Verificar net mes-a-mes.

**Recomendación specialist:** OK pero validar withholding actual. Si volumen >$5K/mo, comparar contra Wise direct.

---

## REFUSED — Blue dollar cueva

**Por qué refused:** SIRA (Sistema de Información de Requerimientos de Activos Externos) trackea bank deposits >100K ARS. Algorithmic matching detecta inconsistencia entre invoicing declarado y deposits aparente. Casos típicos catched dentro de 6-12 meses.

**Después del cierre del blanqueo Milei (May 2025):** los pesos de origen blue no tienen vía legal de "blanqueo retrospectivo." Riesgo se acumula.

**El specialist NO recomienda blue cueva incluso cuando:**
- El user lo pide explícito ("dale Wise está caro")
- El user dice que "lo hace todo el mundo"
- El monto parece chico (<$1K USD)

La regla: **AFIP audit cost > spread savings**. Una recategorización forzada + intereses + multa de 25-75% sobre el monto disputado supera el ahorro de cualquier cueva en monto razonable.

---

## REFUSED — Crypto P2P informal (sin VASP)

**Por qué refused:** Mismo principio que blue cueva — sin trazabilidad institutional, sin valuación contemporánea documentada, sin registro CNV. Post Aug-Sep 2025 el regulatory framework exige VASP registration; operations que la sortean entran en zona roja.

**Casos comunes que el specialist refuses:**
- Cliente paga USDT a wallet personal del operator y luego se cambia P2P en cueva crypto
- Operator recibe USDT en exchange no registrado en CNV (típicamente exchanges descentralizados o exchanges operating sin presencia local registrada)
- Mix de USDT recibido en VASP registrada + USDT recibido en wallet privada sin documentación de origen

**El specialist tiene una sola excepción:** si el operator declara que va a hacer la operación de todas formas (override explícito), el specialist puede explicarle qué documentación generar para minimizar riesgo. Pero NO recomienda la lane.

---

## Decision tree resumen para Routing Mode

```
Invoice viene → ¿VASP-registered crypto disponible?
                ├─ Sí → ¿Cliente paga en USDT?
                │       ├─ Sí, urgencia → USDT-VASP lane
                │       └─ No urgencia → Wise lane (default)
                └─ No → ¿Volumen mensual >$10K Y broker disponible?
                        ├─ Sí → Mercury+MEP lane
                        └─ No → Wise lane (default)
                
Cualquier branch → Confidence calibration + Audit pack shadow + Decision Trace
```

**Default 80% del tiempo:** Wise + Factura E. El specialist tiene que justificar específicamente cuando recomienda otra lane.
