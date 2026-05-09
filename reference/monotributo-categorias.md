# Monotributo — Categorías, Límites, Recategorización, Salida a RI

**Calibrado mayo 2026.** Próxima recategorización oficial: **agosto 2026.** Si la fecha actual supera ese mes y este archivo no fue actualizado, validar contra fuente oficial antes de routing decisions.

Fuente primaria: [ARCA / AFIP — Monotributo Categorías](https://www.afip.gob.ar/monotributo/categorias.asp). Confirmaciones May 2026: [Ámbito](https://www.ambito.com/informacion-general/arca-confirmo-los-nuevos-topes-del-monotributo-y-cuanto-se-paga-mayo-2026-n6271407), [iProfesional](https://www.iprofesional.com/impuestos/446570-monotributo-2026-cuanto-aumentan-las-cuotas-los-topes-y-como-hacer-la-recategorizacion).

---

## Categorías y límites (mayo 2026)

Valores oficiales ARCA vigentes desde febrero 2026, confirmados para mayo 2026 (ajuste 14,28% IPC 2H 2025; próxima actualización agosto 2026).

| Cat | Límite anual ARS | USD equiv. @ MEP 1.418 | Cuota mensual servicios ARS |
|-----|------------------|------------------------|----------------------------|
| **A** | 10.277.988 | ~$7.250 | ~42.386 |
| **B** | 15.375.757 | ~$10.844 | ~48.250 |
| **C** | 21.521.795 | ~$15.178 | ~56.501 |
| **D** | 26.734.386 | ~$18.855 | ~72.414 |
| **E** | 31.427.408 | ~$22.164 | ~102.548 |
| **F** | 38.642.048 | ~$27.251 | ~129.045 |
| **G** | 46.211.109 | ~$32.589 | ~197.108 |
| **H** | 70.113.407 | ~$49.446 | ~447.300 |
| **I** | 78.479.212 | ~$55.345 | ~824.802 |
| **J** | 89.872.640 | ~$63.381 | ~874.069 |
| **K (máxima)** | **108.357.084** | **~$76.415** | **~1.381.687** |

Fuentes verificadas: [ARCA — Categorías oficiales](https://www.afip.gob.ar/monotributo/categorias.asp) · [iProfesional mayo 2026](https://www.iprofesional.com/impuestos/454000-monotributo-mayo-2026-arca-confirmo-cuanto-paga-cada-categoria-y-de-cuanto-son-cuotas) · [Ámbito mayo 2026](https://www.ambito.com/informacion-general/arca-confirmo-los-nuevos-topes-del-monotributo-y-cuanto-se-paga-mayo-2026-n6271407).

**La categoría K es el techo absoluto del régimen.** Superar el límite K = salida obligatoria del monotributo y pase a Responsable Inscripto (RI).

### Cómo se calcula el límite

El límite es **facturación bruta acumulada en los últimos 12 meses móviles** — no calendario. ARCA mira invoice-por-invoice contra los 12 meses anteriores, no Jan-Dec del año fiscal. Esto matters para el routing: un invoice grande en julio puede empujar el rolling-12 sobre el límite incluso si Jan-Dec todavía da bien.

### Cuándo USD invoicing matchea el límite

USD se convierte a ARS al tipo de cambio **del momento de emisión de la Factura E** (no al momento de cobro). Si emitís Factura E en mayo a 1.418 ARS/USD pero cobrás en junio a 1.450, el monto que cuenta para la cat es el de mayo. Documentar la cotización en cada Factura E es operator-discipline básica.

---

## Recategorización

ARCA hace recategorización oficial **dos veces al año**:

- **Febrero** (revisa Aug-Jan, ajusta cat para Feb-Jul)
- **Agosto** (revisa Feb-Jul, ajusta cat para Aug-Jan)

### Recategorización Feb 2026 (la que aplica hoy)

Aumentó los topes ~14,28% por IPC del segundo semestre 2025. Cat K subió de ~94.8M ARS a 108.357M ARS. Esto le dio aire a consultores en cats H-K que estaban cerca del techo.

### Próxima recategorización Aug 2026

Histórico: cada recategorización sube los topes 10-15% según inflación medida. Si el comportamiento del 2025-2026 se repite, esperá un nuevo aumento de ~10% en Aug 2026.

**Implicación para routing:** si tu trayectoria actual te pone cerca del techo de tu cat antes de Aug, podés decidir entre (a) bajar el ritmo de invoicing para esperar el ajuste, (b) prepararte para subir de cat, (c) prepararte para RI si estás en K.

### Recategorización proactiva

Podés recategorizar voluntariamente cualquier mes — no esperar Feb/Aug. Si en abril te diste cuenta que vas a cerrar el año en cat G y arrancaste el año en cat F, recategorizá ya. La cuota mensual sube pero el riesgo de auditoría por estar mal-categorizado baja a cero.

---

## Salida a Responsable Inscripto (RI)

### Cuándo es forzosa

Superar el límite anual de cat K (108.357M ARS Feb-Jul 2026, sujeto a actualización Aug). ARCA detecta automáticamente; te baja del régimen y entrás a RI desde el mes siguiente.

### Costo aproximado de operar como RI

- **IVA**: 21% sobre los servicios facturados (con créditos por insumos). Para servicios de exportación, IVA al 0% por régimen exportación.
- **Ganancias**: alícuota progresiva 5-35% sobre ganancia neta.
- **IIBB**: según jurisdicción (CABA: 3-5%; PBA: 5%; algunas exenciones para servicios exportación).
- **Honorarios contables**: ~$80-150 USD/mes promedio para consultor activo.
- **Tiempo administrativo**: ~4-8 hs/mes en filings y reconciliaciones.

### Beneficios de RI vs. monotributo

- Sin techo de facturación.
- Crédito fiscal por insumos deducible.
- Más legitimidad ante clientes corporate grandes.
- Permite estructuras más complejas (sociedad, holding, etc.).

### Cuándo NO conviene saltar antes de tiempo

Si estás cómodo en cat I-J y proyectás que con la recategorización Aug 2026 el techo te dará aire para 6-12 meses más, NO saltes a RI por defecto. El costo administrativo (~$1-2K USD/año en honorarios + tiempo) supera el beneficio fiscal salvo que estés escalando agresivamente.

### Trigger objetivo para considerar salto

- Trayectoria YTD proyecta superar K en 6 meses o menos.
- Volumen mensual estable >$8K USD/mes.
- Pipeline de clientes que excede el techo K dentro del año.
- Necesidad estructural de IVA crédito fiscal por gastos significativos en software/servicios B2B.

---

## Errores comunes en cat-management

### 1. Quedarte en cat baja por inercia

Inflación y aumentos de invoicing erosionan el headroom rápido. Revisar trayectoria YTD vs cat actual cada cierre de mes — no esperar a Feb/Aug.

### 2. Recategorizar tarde después de un mes pico

Si en marzo facturaste el doble de lo normal (cliente con proyecto puntual), no esperes a Aug para recategorizar. La diferencia entre cat F y cat G en cuota mensual (~15K ARS) es menor que el costo de una auditoría por sub-categorización.

### 3. Mezclar fuentes de ingreso sin separar actividades

Si facturás consultoría + venta de productos digitales + alquileres, ARCA puede pedirte separación de actividades. Una actividad puede empujarte de cat más rápido que las otras. Documentar separadamente desde el inicio.

### 4. Ignorar que USD se convierte al momento de Factura E

Operador emite Factura E en USD a 1.400, espera a cobrar a 1.500, y declara el monto al tipo de cambio del cobro. Eso es **incorrecto**. La cat se calcula contra el monto al momento de la factura. Diferencia detectable por SIRA.

### 5. Estimar mal el rolling-12

ARCA mira últimos 12 meses móviles. Un consultor que ve "mi año fiscal está bien" puede estar pasado de cat porque junio a junio supera el techo aunque enero a diciembre no.

---

## Lo que está por cambiar (Q3-Q4 2026)

### Recategorización agosto 2026 (esperado)

Aumento estimado de topes 10-15% por IPC medido Feb-Jul 2026. Cat K probablemente subiría a ~120-125M ARS. Esto le da más aire a high-volume consultores antes del salto a RI.

### RG 5824/2026 — Consumer-ID threshold (efectivo July 1, 2026)

Para Facturas a final-consumers ≥10M ARS hay que reportar DNI/CUIL/CDI del receptor. Para consultores monotributistas facturando export-services a clientes externos esto **NO aplica** directamente (Factura E a empresa externa no es a final consumer). Pero si tenés algún cliente local mayor a esa cifra, corresponde.

### Pre-llenado de declaraciones IVA (rollout July 2026)

ARCA va a auto-poblar declaraciones IVA usando datos del e-invoicing. Reduce el costo administrativo de RI marginal — re-balanceando levemente el cálculo monotributo vs RI.

### Enforcement VASP (post Aug-Sep 2025 deadlines)

Plataformas crypto sin registro CNV podrían sufrir suspensiones de servicio. Lemon, Belo, Buenbit, Binance Argentina ya están registrados. Si tu USDT routing pasa por una plataforma no listada, validar status.

---

## Trigger summary para el specialist

Esto es lo que el specialist usa para flagear en la sección "Próximo-mes flag" de Routing Mode:

- **YTD facturado >70% del techo de cat actual antes de mes 9** → flag recategorización proactiva.
- **YTD trajectory proyecta >100% del techo K antes del cierre del año** → flag RI transition consideration.
- **Acumulado rolling-12 >85% del techo cat actual** → flag verificación inmediata, posible mis-categorización ya activa.
- **Próxima Factura E >20% del headroom restante en la cat** → flag review de cat-jump trigger (¿conviene aceptar el invoice y saltar cat, o postponer/dividir?).
