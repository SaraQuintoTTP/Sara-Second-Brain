# BRUTO — Unit Economics & Stress Test Finanziario
**Data:** 2026-05-20
**Agente:** Calculator — TTP AI Agency
**Task:** T025
**Status:** FINAL

> **Avvertenza metodologica:** Ogni numero è classificato come [BENCHMARK] (fonte settoriale citata), [STIMA] (derivato da proxy o analogia) o [ASSUNZIONE] (input deliberato con razionale esplicito). Il modello privilegia il caso conservativo. Un modello pessimistico realistico è più utile di uno ottimistico.

---

## SEZIONE 1 — Dimensioni di Mercato e SOM Realistico

### 1.1 Struttura del mercato online

| Livello | Valore | Fonte |
|---------|--------|-------|
| Pet food Italy totale | €3.600M | [BENCHMARK] NIQ 2025 |
| Pet food Italy online | €451M | [BENCHMARK] NIQ 2025 |
| Quota online su totale | 12,5% | [BENCHMARK] derivato |
| Crescita online YoY | +8,2% | [BENCHMARK] NIQ 2025 |
| Proiezione online 2027 (2 anni) | ~€528M | [STIMA] applicando tasso composto |

**Composizione del canale online (€451M):**

| Sub-canale | Quota stimata | Valore stimato | Nota |
|------------|---------------|----------------|------|
| Amazon.it | 45-50% | €203-226M | [STIMA] da benchmark Explorer TTP |
| Zooplus.it | 20-25% | €90-113M | [STIMA] |
| Arcaplanet online | 10-12% | €45-54M | [STIMA] |
| D2C brand proprietari | 10-15% | €45-68M | [STIMA] |
| Altri marketplace | ~5% | €23M | [STIMA] |

**DTC subset stimato:** €45-68M [STIMA]. Di questo importo, circa il 60-70% è concentrato su pochi player consolidati (Next Dog, Dog Heroes, Amusi). Il mercato DTC indipendente e "aperto" per nuovi entranti è stimabile in **€15-25M** [STIMA].

### 1.2 Benchmark competitivi

| Brand | Modello | Status | ARR stimato | Fonte |
|-------|---------|--------|-------------|-------|
| Dog Heroes | Fresh DTC, funded | ~€5M+ raccolti | €2-4M ARR [STIMA] | Analisi comparativa TTP |
| Amusi | Kibble DTC, non-funded | Attivo | €200-500K ARR [STIMA] | Proxy dimensionale |
| Next Dog | Personalizzato DTC | Startup attiva | €300-700K ARR [STIMA] | Proxy |

> **Nota metodologica:** Dog Heroes opera nel fresh/refrigerato (segmento diverso da BRUTO), ha raccolto €5M+ in funding e presuppone una struttura di costi (cold chain, freschezza) incompatibile con il modello BRUTO. Non è un benchmark diretto per ARR — è un upper bound di "cosa può diventare un DTC pet food IT con funding".

### 1.3 Serviceable Obtainable Market (SOM) Anno 1

| Scenario | SOM Anno 1 | Logica | Quota implicita del DTC aperto |
|----------|-----------|--------|-------------------------------|
| **Conservativo** | **€80-120K ARR** | Brand nuovo, <€200K budget totale, 0 brand awareness. Corrisponde a ~150-220 clienti attivi con AOV €50/mese | ~0,4-0,6% del DTC aperto |
| **Base** | **€180-280K ARR** | Buona esecuzione paid+organico, 1-2 viral content. ~300-500 clienti attivi | ~0,9-1,4% |
| **Ottimistico** | **€400-600K ARR** | Virality TikTok + forte word-of-mouth + esecuzione eccellente. ~700-1.000 clienti attivi | ~2-3% |

**Raccomandazione:** pianificare su scenario conservativo, gestire su scenario base. Lo scenario ottimistico richiede un evento esterno (viral) non pianificabile.

---

## SEZIONE 2 — Costi del Prodotto (COGS)

### 2.1 SKU A — Crocchette Premium (Dry Kibble), 2 kg

**Ingredienti premium kibble:** proteina animale >70%, grain-free, clean label.

| Componente COGS | Conservativo | Base | Note |
|-----------------|--------------|------|------|
| Ingredienti (€/kg × 2) | €3,00 | €4,00 | [BENCHMARK] kibble premium EU: €1,50-3,50/kg ingredienti; fascia alta per clean label grain-free |
| Produzione/co-packing (€/sacco) | €1,20 | €1,00 | [STIMA] co-packer IT per lotti >500 sacchi: €0,80-1,50/sacco |
| Packaging — sacco 2kg | €1,40 | €1,20 | [STIMA] — vedi nota packaging |
| Labeling + QR + conformità | €0,20 | €0,18 | [STIMA] stampa + compliance cost ammortizzato |
| Riempimento/sigillatura | €0,25 | €0,20 | [STIMA] incluso nel co-packing se ordine >1.000 pz |
| Subtotale COGS/sacco | **€6,05** | **€6,58** | Prima di spedizione |

**Nota packaging (BRUTO-specifico):** Il sistema packaging BRUTO usa sacco nero matte con stampa spot fluo (giallo #FFFDA + colori proteina). Questo è un **premium packaging vs. standard**:

| Tipo packaging | Costo stimato 2kg | Delta |
|----------------|-------------------|-------|
| Sacco standard (Kraft/bianco, 1-2 colori) | €0,55-0,70 | baseline |
| Sacco matte laminato, 4 colori | €0,85-1,10 | +€0,30-0,40 |
| **Sacco matte nero + spot fluo (BRUTO)** | **€1,20-1,60** | **+€0,50-0,90 vs. standard** |

[STIMA] basata su benchmark packaging premium food Italia. La differenza reale dipende dal lotto minimo (MOQ): sotto le 5.000 unità il costo aumenta del 15-25%.

**Analisi margini SKU A a diversi prezzi di vendita:**

| Prezzo vendita | COGS base | Margine lordo € | Margine lordo % |
|----------------|-----------|-----------------|-----------------|
| €12,00 | €6,58 | €5,42 | 45,2% |
| €15,00 | €6,58 | €8,42 | 56,1% |
| €18,00 | €6,58 | €11,42 | 63,4% |
| €12,00 | €6,05 (cons.) | €5,95 | 49,6% |
| €15,00 | €6,05 (cons.) | €8,95 | 59,7% |
| €18,00 | €6,05 (cons.) | €11,95 | 66,4% |

> **Raccomandazione pricing SKU A:** €15-16 per sacco 2kg è il punto di equilibrio tra competitività (Farmina N&D 2kg = €12-15, Carnilove 2kg = €14-18) e margine sostenibile. A €12 il margine lordo scende al 45-50% — accettabile solo se il volume è alto. A €18 il posizionamento è possibile ma richiede forte brand equity percepita fin dall'inizio.

### 2.2 SKU B — Umido Premium (Wet Food), 400g lattina

| Componente COGS | Conservativo | Base | Note |
|-----------------|--------------|------|------|
| Ingredienti (€/kg × 0,4) | €1,60 | €2,00 | [BENCHMARK] umido ha % acqua alta; costo ingredienti secchi effettivi €4-5/kg = €1,60-2,00 per 400g |
| Produzione/co-packing lattina | €0,60 | €0,50 | [STIMA] lattina alluminio + riempimento + sterilizzazione, lotti >2.000 pz |
| Lattina + coperchio | €0,35 | €0,30 | [STIMA] lattina 400g alluminio premium |
| Label wrap + stampa spot | €0,25 | €0,20 | [STIMA] label con sistema colore proteina BRUTO |
| Conformità/labeling | €0,08 | €0,07 | [STIMA] |
| **Subtotale COGS/lattina** | **€2,88** | **€3,07** | |

**Margini SKU B:**

| Prezzo vendita | COGS base | Margine € | Margine % |
|----------------|-----------|-----------|-----------|
| €3,50 | €3,07 | €0,43 | 12,3% — insufficiente |
| €4,50 | €3,07 | €1,43 | 31,8% |
| €5,50 | €3,07 | €2,43 | 44,2% |
| €6,50 | €3,07 | €3,43 | 52,8% |

> **Nota critica:** La singola lattina 400g a meno di €5 non regge il modello DTC. L'umido si vende profittevolmente come multipack (es. 12 lattine × €4,80 = €57,60 per box, COGS ~€37 = margine 36%). Il formato singolo è acquisition tool, il multipack è il revenue driver.

### 2.3 COGS riepilogativo per analisi LTV

| Metrica | SKU A (2kg) | SKU B (400g) | Mix stimato |
|---------|-------------|-------------|-------------|
| COGS per unità | €6,05-6,58 | €2,88-3,07 | — |
| Prezzo target | €15-16 | €4,80-5,50 (o box) | — |
| Margine lordo % | 56-60% | 32-44% | ~50-55% [STIMA] |

---

## SEZIONE 3 — Modello di Ricavi

### 3.1 Struttura dell'ordine medio (AOV)

Scenari di acquisto tipico per DTC kibble:

| Composizione ordine | AOV stimato | Note |
|--------------------|-------------|------|
| 1 × kibble 2kg | €15-16 | Solo secco, ordine minimo |
| 2 × kibble 2kg | €30-32 | Taglia media/grande, mensile |
| 2 × kibble + 4 × umido | €48-56 | Mix tipico DTC pet food IT |
| **AOV stimato subscription media** | **€42-52** | [STIMA] benchmark DTC pet food EU |

> [BENCHMARK] Da dati Explorer TTP: abbonamento DTC pet food IT medio €35-50/mese a seconda della taglia del cane. AOV base €40 è confermato da analisi interna precedente (BRAMO model). Si usa €42 come punto base per BRUTO (posizionamento premium rispetto a baseline).

### 3.2 Split subscription vs. one-time

| Metrica | Benchmark | Fonte |
|---------|-----------|-------|
| % clienti in subscription dopo 3 mesi | 40-60% | [BENCHMARK] EU DTC pet food (Zooplus, Butternut Box UK reports) |
| % subscription al lancio (prime 90 giorni) | 15-25% | [STIMA] — i nuovi clienti testano prima di abbonarsi |
| Target subscription Anno 1 medio | 35% | [ASSUNZIONE] conservativo |

### 3.3 Churn e LTV

| Metrica | Conservativo | Base | Ottimistico | Fonte |
|---------|--------------|------|-------------|-------|
| Churn mensile subscription | 10% | 8% | 5% | [BENCHMARK] DTC food EU: 5-12% mensile |
| Vita media cliente (1/churn) | 10 mesi | 12,5 mesi | 20 mesi | Derivato |
| LTV lordo (AOV €42 × vita) | €420 | €525 | €840 | Calcolato |
| LTV netto (margine 52%) | **€218** | **€273** | **€437** | Calcolato |

**LTV a 12 e 24 mesi:**

| Scenario churn | LTV 12 mesi | LTV 24 mesi |
|----------------|-------------|-------------|
| Churn 10%/mese | €218 | €269 (plateau) |
| Churn 8%/mese | €273 | €389 |
| Churn 5%/mese | €374 | €583 |

> **Nota metodologica:** LTV 24 mesi a churn 10% non raddoppia rispetto a 12 mesi perché la coorte si esaurisce rapidamente. Il churn elevato distrugge il LTV in modo non lineare — è la leva più critica dell'intero modello.

---

## SEZIONE 4 — Customer Acquisition Cost (CAC)

### 4.1 CAC per canale — mercato Italia

**Organico (SEO + Social/UGC):**
- CAC diretto: teoricamente €0 [ASSUNZIONE]
- Realtà: cost of content creation €500-1.500/mese per produzione costante
- Tempi: SEO 9-18 mesi per risultati organici in keyword competitive pet food
- CAC effettivo se si ammortizza il costo content: **€15-40 per cliente acquisito** [STIMA] su 12 mesi

**Meta Ads (Facebook + Instagram) — Italia pet food:**

| Metrica | Range | Fonte |
|---------|-------|-------|
| CPM (costo per 1.000 impressioni) | €8-18 | [BENCHMARK] Meta Italia, categoria pet/food, dato 2024-2025 |
| CTR medio | 1-2% | [BENCHMARK] |
| CPC (costo per click) | €0,40-1,80 | Derivato da CPM/CTR |
| CVR (click → acquisto) | 1,5-3,5% | [BENCHMARK] ecommerce niche IT |
| CAC da Meta | **€25-80** | [STIMA] range ampio — dipende da creatività e targeting |

> [STIMA] CAC Meta conservativo per brand nuovo senza social proof = €60-80. Con buona creatività e ottimizzazione dopo 60 giorni = €35-50. Sotto €35 su Meta con brand nuovo è difficile da sostenere sistematicamente.

**TikTok Ads — Italia pet:**

| Metrica | Range | Fonte |
|---------|-------|-------|
| CPM TikTok IT | €5-12 | [BENCHMARK] TikTok Ads Manager benchmark 2024 |
| CVR (più basso per intento meno diretto) | 0,8-2% | [STIMA] |
| CAC TikTok | **€20-55** | [STIMA] — vantaggio: brand nuovo può avere CPM basso per novità algoritmo |

**Micro-influencer (pet niche, <50K follower, Italia):**

| Profilo | Costo collaborazione | Reach stimata | Conv. stimate | CAC stimato |
|---------|---------------------|---------------|---------------|-------------|
| Nano (1K-10K) | €0 gifting + prodotto (€15) | 300-800 view | 2-8 | €2-8 [STIMA] |
| Micro (10K-50K) | €50-300 + gifting | 2K-10K view | 10-40 | €8-25 [STIMA] |
| Mid-tier (50K-150K) | €300-1.000 | 10K-30K view | 30-80 | €10-30 [STIMA] |

> **Nota:** I micro-influencer del pet niche italiano hanno engagement rate 5-12% [STIMA — superiore alla media] per contenuti di cibo. Il gifting puro (prodotto, no fee) è praticabile per nano-influencer e genera CAC sotto €15 se il tasso di conversione regge.

### 4.2 CAC blended Anno 1

Assunzione mix marketing [ASSUNZIONE]:
- 40% Meta Ads
- 25% TikTok Ads
- 20% Micro-influencer
- 15% Organico (SEO/UGC ammortizzato)

| Scenario | CAC blended | Logica |
|----------|-------------|--------|
| **Conservativo** | **€55-70** | Brand nuovo, creatività non ottimizzata, landing page non testate |
| **Base** | **€35-50** | Dopo 60-90 giorni di ottimizzazione, buon mix influencer |
| **Ottimistico** | **€20-35** | Viral content organico + micro-influencer gifting massiccio |

> **Flag critico:** I dati di benchmark per CAC specifici del mercato DTC pet food italiano sono limitati. Amusi e Next Dog non pubblicano metriche. I range sono derivati da benchmark EU (UK, DE, FR) e adattati per dimensione mercato IT. Fonte gap dichiarata.

### 4.3 LTV:CAC ratio e soglia di viabilità

| Scenario | LTV netto 12m | CAC blended | LTV:CAC | Viabile? |
|----------|--------------|-------------|---------|---------|
| Worst case | €218 | €70 | **3,1:1** | Limite — appena sopra soglia |
| Conservativo | €218 | €55 | **4,0:1** | Accettabile |
| Base | €273 | €45 | **6,1:1** | Buono |
| Ottimistico | €437 | €30 | **14,6:1** | Eccellente |

**Soglia minima di viabilità DTC:** LTV:CAC ≥ 3:1 [BENCHMARK] — sotto questa soglia il business brucia cassa senza prospettiva di recupero.

> **Conclusione Sezione 4:** BRUTO è finanziariamente viabile anche nel caso conservativo (3,1:1), ma il margine è stretto. Qualsiasi deterioramento simultaneo di LTV e CAC — ad esempio churn al 12% e CAC a €80 — porta il ratio a ~2:1, territorio non sostenibile. La priorità operativa è ridurre il churn prima ancora di scalare l'acquisizione.

---

## SEZIONE 5 — Conto Economico Semplificato Anno 1

### 5.1 Ipotesi operative

| Parametro | Conservativo | Base | Ottimistico |
|-----------|--------------|------|-------------|
| Clienti acquisiti Anno 1 | 200 | 400 | 700 |
| Clienti attivi fine Anno 1 (post-churn 10%/8%/6%) | ~130 | ~290 | ~560 |
| AOV mensile medio | €42 | €44 | €46 |
| MRR fine Anno 1 | €5.460 | €12.760 | €25.760 |
| ARR run-rate fine Anno 1 | €65.520 | €153.120 | €309.120 |

**Ricavi totali Anno 1** (non il run-rate finale — la somma dei 12 mesi):

| Scenario | Ricavi totali Anno 1 |
|----------|---------------------|
| Conservativo | €38.000-45.000 |
| Base | €80.000-100.000 |
| Ottimistico | €150.000-200.000 |

### 5.2 Conto Economico Anno 1 — Scenario Base

| Voce | Anno 1 | % su ricavi | Note |
|------|--------|-------------|------|
| **Ricavi** | **€90.000** | 100% | |
| COGS (prodotto) | €40.500 | 45% | Margine lordo 55% — include packaging premium |
| Fulfillment (imballaggio + spedizione) | €12.600 | 14% | [STIMA] €3,50-4/ordine × ~3.000 ordini Anno 1 |
| **Gross Profit** | **€36.900** | **41%** | Margine lordo post-fulfillment |
| Marketing (CAC × clienti) | €18.000 | 20% | 400 clienti × €45 CAC medio |
| Tech stack (Shopify, email, tools) | €3.600 | 4% | [STIMA] €300/mese |
| Fotografia / content production | €4.000 | 4% | [ASSUNZIONE] produzione asset Anno 1 |
| Legal / compliance / UIBM | €3.000 | 3% | [STIMA] marchio + T&C + cookie policy |
| Admin / contabilità / varie | €2.400 | 3% | [STIMA] |
| **Totale Costi Operativi** | **€31.000** | **34%** | |
| **EBITDA** | **€5.900** | **6,6%** | Positivo, ma marginale |

### 5.3 Conto Economico — Scenario Conservativo

| Voce | Anno 1 | % su ricavi |
|------|--------|-------------|
| Ricavi | €40.000 | 100% |
| COGS + fulfillment | €23.600 | 59% |
| Gross Profit | €16.400 | 41% |
| Marketing | €13.000 | 33% (200 clienti × €65) |
| Tech + admin + legal + content | €13.000 | 33% |
| **EBITDA** | **-€9.600** | **-24%** — PERDITA |

> **Nota critica:** Nel conservativo, il business è in perdita Anno 1. È normale per un DTC pre-PMF che investe in acquisizione. Il punto non è la redditività Anno 1 — è il percorso verso il break-even.

### 5.4 Break-even mensile

| Parametro | Valore |
|-----------|--------|
| Costi fissi mensili (tech + admin + legal amm.) | €750-900/mese |
| Marketing mensile (costante) | €1.200-1.800/mese |
| Totale costi cash mensili (escluso COGS) | ~€2.000-2.700/mese |
| Margine per cliente attivo/mese (AOV €42 × 41%) | ~€17/cliente |
| **Clienti necessari per break-even** | **118-159 clienti attivi** |
| **Timing break-even (scenario base)** | **Mese 6-8** |
| **Timing break-even (scenario conservativo)** | **Mese 10-14** |

---

## SEZIONE 6 — Fabbisogno Finanziario e Runway

### 6.1 Budget minimo di lancio

| Voce | Importo | Note |
|------|---------|------|
| Sviluppo prodotto (ricette, campionatura co-packer) | €3.000-6.000 | [STIMA] 2-3 cicli campionatura |
| Prima produzione (500-1.000 unità SKU A + B) | €8.000-15.000 | [STIMA] lotto minimo co-packer IT |
| Packaging setup (fotolito, stampe) | €2.000-4.000 | [STIMA] costi di avviamento stampa sacco nero matte |
| Sito web (Shopify + design) | €3.000-6.000 | [STIMA] sviluppo custom |
| Fotografia prodotto + content hero | €2.500-4.000 | [ASSUNZIONE] — il packaging BRUTO richiede art direction dedicata |
| Registrazione marchio UIBM | €800 | [BENCHMARK] citato nel brief |
| Certificazioni + compliance etichette | €1.000-2.000 | [STIMA] |
| 3 mesi di paid acquisition | €5.000-8.000 | [ASSUNZIONE] €1.500-2.700/mese × 3 |
| Riserva operativa (3 mesi fissi) | €3.000-4.000 | [ASSUNZIONE] buffer imprevedibili |
| **Budget minimo launch** | **€28.300-49.000** | |

### 6.2 Cosa compra ogni budget

**€50.000 (budget minimo di senso):**
- Lancio con 1 SKU kibble + 1 SKU umido
- ~500-800 unità di prima produzione
- Sito funzionale (non premium)
- 3 mesi di acquisizione pagata con budget limitato (~€1.500/mese)
- Runway: 5-6 mesi prima di aver bisogno di ricavi o rinforzo
- **Rischio:** pochissimo margine per errori. Se la prima produzione ha difetti o il CAC è più alto del previsto, il budget non regge.

**€150.000 (budget operativo consigliato):**
- Lancio con gamma completa (2-3 SKU kibble + 2-3 SKU umido)
- Prima produzione 2.000-3.000 unità per SKU
- Sito Shopify completo con UX ottimizzata
- 6 mesi di acquisizione a €1.500-2.500/mese
- Budget fotografico/content adeguato (€8-10K)
- Riserva per ottimizzazione creativa e test A/B
- Runway: 10-12 mesi con costi base
- **Probabilità di raggiungere break-even entro Anno 1:** 50-60% [STIMA]

**€300.000 (budget aggressivo):**
- Launch completo + scala dopo validazione iniziale (mesi 1-4)
- Budget acquisizione €3.000-5.000/mese da mese 5
- Influencer partnership retribuiti (non solo gifting)
- PR + stampa settoriale
- Stock buffer per evitare rotture
- Possibilità di tentare Amazon IT da mese 6 come canale secondario
- **Probabilità break-even entro mese 8-9:** 65-75% [STIMA]
- **Proiezione ARR fine Anno 1:** €150-200K

### 6.3 Soglia finanziamento esterno

Il founder non ha bisogno di funding esterno se il budget disponibile è ≥€150K e il break-even viene raggiunto entro il mese 10-12.

**Segnali che indicano necessità di funding:**
- Budget totale disponibile <€80K
- Fine dei 12 mesi con clienti attivi <100 (suggerisce PMF non trovato)
- Churn costantemente >12% (problema prodotto, non di marketing)
- CAC blended che non scende sotto €70 dopo 6 mesi di ottimizzazione

---

## SEZIONE 7 — Rischi Finanziari Quantificati

### Rischio 1 — CAC più alto del previsto

**Scenario:** CAC blended = 2× stima base (da €45 a €90)

| Metrica | Base | CAC ×2 | Delta |
|---------|------|--------|-------|
| Budget marketing Anno 1 | €18.000 | €36.000 | +€18.000 |
| Clienti acquisibili con €18K | ~400 | ~200 | -200 |
| ARR run-rate fine Anno 1 | €153K | €76K | -50% |
| LTV:CAC (churn 8%) | 6,1:1 | 3,0:1 | Soglia critica |
| EBITDA Anno 1 | +€5.900 | -€17.000 | Perdita significativa |

**Probabilità:** media-alta per un brand nuovo senza storico creativo [STIMA 40-50%].
**Mitigazione:** fissare il CAC target a €50 nei primi 90 giorni come KPI go/no-go per scaling. Se supera €70 dopo 90 giorni di ottimizzazione, rivedere creatività o canale prima di aumentare il budget.

---

### Rischio 2 — Churn più alto del previsto

**Scenario:** churn mensile = 15% invece di 8% (es. prodotto non convince alla ripetizione, qualità percepita inferiore alle aspettative, prezzo troppo alto)

| Metrica | Base (8%) | Churn 15% | Delta |
|---------|-----------|-----------|-------|
| Vita media cliente | 12,5 mesi | 6,7 mesi | -46% |
| LTV lordo (AOV €42) | €525 | €281 | -46% |
| LTV netto (52%) | €273 | **€146** | -46% |
| LTV:CAC (CAC €45) | 6,1:1 | **3,2:1** | Quasi soglia |
| Clienti attivi fine Anno 1 | ~290 | ~165 | -43% |
| ARR run-rate fine Anno 1 | €153K | €86K | -44% |

**Nota:** con churn 15% e CAC €65+ (caso non ottimizzato), LTV:CAC scende sotto 2,5:1 — non sostenibile.
**Probabilità:** media per brand nuovo [STIMA 30-40%]. Il rischio churn elevato è tipico dei primi 3 mesi quando il cliente non è ancora abituato e non ha visto risultati sul cane.
**Mitigazione:** investire in onboarding (email sequence mese 1-2, guida transizione alimentare, check-in a 30 giorni). Il churn nel DTC pet food si riduce drasticamente se il cliente vede miglioramenti fisici nel cane entro 4-6 settimane.

---

### Rischio 3 — Squeeze di margine da packaging premium

**Scenario:** costo packaging 2kg aumenta di €0,80 per unità rispetto al piano base (es. lotti piccoli, fornitore specializzato per nero matte + spot fluo, costi avviamento)

| Metrica | COGS base | COGS +€0,80/sacco | Delta |
|---------|-----------|-------------------|-------|
| COGS per sacco 2kg | €6,58 | €7,38 | +12,2% |
| Margine lordo a €15 | 56,1% | 50,8% | -5,3 pp |
| Margine lordo a €16 | 58,9% | 53,9% | -5 pp |
| Impatto su EBITDA Anno 1 (base, ~3K sacchi) | — | -€2.400 | Materiale |
| Impatto su LTV netto per cliente | -€13 | LTV netto: €260 invece di €273 | -4,8% |

**Probabilità:** alta nei primi 12 mesi [STIMA 60-70%]. I costi di packaging premium si normalizzano con volumi >5.000 unità/SKU/anno — ma nei primi 12 mesi BRUTO difficilmente raggiungerà questi volumi nel caso conservativo.
**Mitigazione primaria:** negoziare il prezzo packaging su volume aggregato (2kg + altre SKU). Oppure accettare il costo e compensare con pricing a €16 anziché €15 per il kibble 2kg.

---

## RIEPILOGO ESECUTIVO

| Indicatore chiave | Conservativo | Base | Ottimistico |
|-------------------|--------------|------|-------------|
| Clienti acquisiti Anno 1 | 200 | 400 | 700 |
| ARR run-rate fine Anno 1 | €65K | €153K | €310K |
| EBITDA Anno 1 | -€9.600 | +€5.900 | +€45.000 |
| CAC blended | €65 | €45 | €28 |
| LTV netto (12m, churn 8%) | €218 | €273 | €437 |
| LTV:CAC | 3,4:1 | 6,1:1 | 15,6:1 |
| Break-even mensile (mese) | M10-M14 | M6-M8 | M4-M5 |
| Budget necessario | €50K (stretto) | €150K | €300K |

**Verdetto finanziario:** BRUTO è **condizionatamente viabile**. Il modello regge nel caso base e ottimistico con margini accettabili. Nel caso conservativo l'Anno 1 è in perdita — ma è strutturalmente normale per un DTC in fase di lancio che investe in acquisizione. Il business non è distrutto dal conservativo, ma richiede un founder con runway finanziario personale o un budget ≥€150K.

**Il rischio più sottovalutato non è il CAC — è il churn.** Il kibble ha un vantaggio naturale rispetto al fresh: shelf life lunga, nessuna catena del freddo, riordino automatico. Il rischio churn per BRUTO è più basso della media del settore [STIMA] — ma va presidiato attivamente nei primi 60 giorni con onboarding strutturato.

**Il packaging premium è un costo inevitabile, non negoziabile.** Il nero matte + spot fluo è il differenziatore visivo che giustifica il prezzo premium. Tagliarlo o renderlo "più economico" distrugge il posizionamento. L'unico modo per gestirlo è aumentare i volumi e negoziare il packaging in anticipo su volumi aggregati.

---

*Report elaborato da Calculator — TTP AI Agency*
*Salvato in: /clients/test_dog_food/projects/bruto_analysis/findings/calculator_unit_economics.md*
*Data: 2026-05-20*
