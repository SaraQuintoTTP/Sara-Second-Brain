# EVA — Modello Finanziario Anno 1–2
## Studio Legale Internazionale Boschetti
### Prodotto il: 2026-06-06 | Agente Calculator

> **Stato Knowledge Skills:** michalowicz-profit-first-quickref.md e staircase-of-value-quickref.md non trovati nei percorsi attesi. Modello costruito su base knowledge + dati dal brief e da EVA_context.md. Segnalare all'Orchestratore per audit dei percorsi skills.

> **Lacune dati chiave:** Il pricing dei servizi EVA non è ancora stato formalizzato dal cliente. Tutte le cifre di prezzo in questo modello sono **ipotesi** basate su benchmark del mercato premium europeo dell'immigrazione e sono esplicitamente marcate come `[IPOTESI]`. Il cliente deve validarle prima di utilizzarle in qualsiasi comunicazione esterna o decisione d'investimento.

---

## §1 — Framework di Pricing

### Razionale
EVA si posiziona come broker neutrale multi-paese (il "MutuiOnline dell'immigrazione"). Questo giustifica un pricing premium rispetto ai consulenti locali mono-paese perché il cliente ottiene: (1) eliminazione del conflitto di interessi, (2) analisi comparativa su 5 giurisdizioni, (3) qualità di livello legale garantita da un avvocato italiano identificabile. Il premium sui competitor è difendibile al 20–40%.

### Architettura dei Livelli di Servizio

| Tier | Nome Servizio | Descrizione | Prezzo Ancora | Prezzo Target | Prezzo Floor |
|------|--------------|-------------|--------------|--------------|--------------|
| T1 | Comparative Snapshot | Consulenza 1h + report scritto di comparazione 5 paesi (nessuna esecuzione) | €800 | €600 | €400 |
| T2 | Advisory + Roadmap | Assessment completo + roadmap consigliata per 1 paese + 3h di follow-up | €2.000 | €1.500 | €1.000 |
| T3 | Gestione Caso Completa — Standard | Caso completo: un paese, un richiedente (es. PT D7 / DE Blue Card) | €5.500 | €4.000 | €2.800 |
| T4 | Golden Visa / HNWI | Caso completo: programma HNWI (PT GV, IT Investor Visa, FR Talent Passport) | €9.000 | €7.500 | €5.500 |
| T5 | Retainer B2B | Retainer mensile per agenzia di relocation / HR / studio legale straniero. Include fino a 3 consulenze/mese + accesso prioritario | €2.000/mese | €1.500/mese | €1.000/mese |

**Note sul pricing:**
- Tutte le cifre T1–T4 sono `[IPOTESI]` — derivate da benchmark del mercato premium europeo della consulenza immigrazione (range tipico: consulenza iniziale €200–500; caso completo €1.500–8.000 da dati pubblici di mercato; consulenza HNWI €5K–15K dai pattern Henley/IMI). `[DA CONFERMARE CON CLIENTE]`
- Il Retainer B2B T5 è `[IPOTESI]` basato su benchmark di consulenza legale frazionale per PMI europee. `[DA CONFERMARE CON CLIENTE]`
- Floor = prezzo minimo accettabile per preservare il posizionamento del brand. Non scendere mai sotto il floor nemmeno per referral.
- Ancora = prezzo aspirazionale mostrato nelle proposte iniziali per ancorare la trattativa.
- T1 Snapshot è un "door opener" strategico — progettato per convertire in T2/T3 entro 60–90 giorni. Non è un prodotto commodity.

### Posizionamento del Pricing vs. Competitor
`[IPOTESI — basata sull'analisi dei siti web dei competitor in EVA_context.md]`
- Oliveira Lawyers (PT): ~€1.500–3.500 per caso D7 completo (mono-paese)
- Balcells Group (ES): ~€2.000–4.000 per NIE/residenza (mono-paese)
- Il prezzo target EVA è un premium del 15–30%, giustificato dal valore comparativo multi-paese e dal posizionamento neutrale

---

## §2 — Unit Economics per Tipo di Incarico

### Metodologia
- Tariffa oraria effettiva di Sara a EVA: €50/h (definita nel brief)
- Costo partner locale: `[IPOTESI]` €80–150/h fatturati a EVA a costo — stimato €500–1.500 per caso in base alla complessità. Nessun dato nel brief. `[DA CONFERMARE CON CLIENTE — variabile chiave]`
- Allocazione overhead per caso: `[IPOTESI]` €150 flat (amministrazione, strumenti, documenti di compliance, invii Brevo proporzionali). Basato su benchmark overhead micro-PMI.
- Target margine TTP: 40% sulle ore di Sara fatturate al cliente EVA

### Tabella Unit Economics

| Metrica | T1 Snapshot | T2 Advisory | T3 Standard | T4 HNWI | T5 B2B/mese |
|---------|------------|------------|------------|---------|------------|
| Ricavo (prezzo target) | €600 | €1.500 | €4.000 | €7.500 | €1.500 |
| Ore Sara (stim.) `[I]` | 2,5h | 6h | 20h | 30h | 8h |
| Costo Sara a EVA | €125 | €300 | €1.000 | €1.500 | €400 |
| Costo partner locale `[I]` | €0 | €200 | €600 | €1.500 | €200 |
| Overhead flat `[I]` | €150 | €150 | €150 | €150 | €150 |
| **Costo diretto totale** | **€275** | **€650** | **€1.750** | **€3.150** | **€750** |
| **Margine di contribuzione €** | **€325** | **€850** | **€2.250** | **€4.350** | **€750** |
| **Margine di contribuzione %** | **54%** | **57%** | **56%** | **58%** | **50%** |

`[I]` = Ipotesi. Ore Sara stimate sulla base di benchmark comparabili di pratiche consulenziali in ambito immigrazione. Costi partner stimati — non formalizzati. Tutti da verificare.

### Stime LTV per Profilo Cliente
`[IPOTESI — basata su pattern di acquisto ripetuto nei servizi professionali]`

| Profilo | 1° Incarico Medio | Probabilità Ritorno | Referral (2 anni) | LTV Stimato (2 anni) |
|---------|------------------|--------------------|--------------------|---------------------|
| Nomad Digitale (T2→T3) | T2: €1.500 | 20% upgrade a T3 | 0,5 referral | €2.100 |
| Investitore HNWI (T4) | T4: €7.500 | 30% follow-on (seconda giurisdizione) | 1,2 referral | €12.000 |
| Pensionato (T3) | T3: €4.000 | 10% follow-on | 0,8 referral | €6.200 |
| Manager ICT (T3) | T3: €4.000 | 40% ripetizione corporate | 1,5 referral | €9.500 `[I]` |
| Brasiliano (T3) | T3: €3.500 | 15% fratello/famiglia | 2,0 referral | €8.400 `[I]` |
| Partner B2B (T5) | T5: €1.500/mese | 70% retention 12 mesi | — | €18.000/anno |

Insight chiave: il retainer B2B ha il LTV più alto con il costo di acquisizione più basso una volta stabilita la relazione. Il T4 HNWI ha il contributo singolo per caso più alto. Dare priorità a questi due segmenti nell'Anno 2 è finanziariamente ottimale.

---

## §3 — Proiezioni Anno 1 — 3 Scenari

### Ipotesi Condivise per Tutti gli Scenari
- Avvio GTM: luglio 2026 (post-lancio sito)
- Campagna brasiliana: settembre 2026 (Fase 2)
- Outreach B2B: ottobre 2026 (Fase 3)
- Vincolo capacità Boschetti: `[IPOTESI]` max 5 casi attivi/mese alla qualità target. Questo è il vincolo vincolante — non la domanda. `[DA CONFERMARE CON CLIENTE]`
- Mix assunto per scenario base: 40% T3, 25% T2, 20% T1, 10% T4, 5% avvii B2B
- Tutti i costi GTM come da proposta di Sara (dal brief — dato confermato)

### Scenario A — Leggero (Conservativo)

**Ipotesi:** Lenta trazione SEO del sito, campagna brasiliana produce 2 conversioni, B2B non si attiva nell'Anno 1, nessun caso Golden Visa nell'Anno 1.

| Mese | Incarichi | Ricavo Lordo | Mix |
|------|-----------|-------------|-----|
| Lug–Ago 2026 | 0 | €0 | Costruzione sito |
| Set 2026 | 1 | €1.500 | T2 (lead campagna brasiliana) |
| Ott 2026 | 2 | €5.500 | T3 x1 + T2 x1 |
| Nov 2026 | 2 | €5.500 | T3 x2 |
| Dic 2026 | 2 | €4.500 | T3 x1 + T2 x1 |
| Gen 2027 | 2 | €4.500 | T3 x1 + T2 x1 |
| Feb 2027 | 3 | €7.500 | T3 x2 + T1 x1 |
| Mar 2027 | 3 | €8.000 | T3 x2 + T2 x1 |
| Apr–Giu 2027 | 3/mese | €22.500 | T3 x2 + T2 x1/mese |
| **TOTALE ANNO 1** | **~24 incarichi** | **~€59.500** | |

**Riepilogo Anno 1 Scenario Leggero:**
- Ricavo lordo: ~€59.500
- Costi diretti: ~€29.750 `[I]` (margine medio 50% = €59.500 × 50% = €29.750)
- Investimento GTM: €8.100–10.100 (scenario leggero dal brief); punto medio €9.100
- **Contribuzione netta prima del lavoro Sara/Stefano:** €29.750 – €9.100 = **~€20.650**
- Ricavo TTP (50€/h × ore Sara): `[I]` ~€15.000 (Sara ~300h Anno 1 su EVA)
- **Netto cliente (Boschetti) Anno 1:** ~€59.500 – costi partner – fee TTP – GTM = ~€20.000–25.000 `[I]`

---

### Scenario B — Base (Raccomandato)

**Ipotesi:** Sito live a luglio, campagna brasiliana attiva Q3, 3–5 casi T3 da organico + referral, pilota B2B (1 partner attivo Q4), 1 caso T4 HNWI in Q1 2027. Corrisponde alla proposta operativa di Sara.

| Mese | Incarichi | Ricavo Lordo | Mix |
|------|-----------|-------------|-----|
| Lug–Ago 2026 | 0 | €0 | Costruzione sito |
| Set 2026 | 2 | €3.500 | T2 x1 + T3 x1 (brasiliano) |
| Ott 2026 | 3 | €9.000 | T3 x2 + T2 x1 |
| Nov 2026 | 3 | €10.500 | T3 x2 + T2 x1 + avvio B2B |
| Dic 2026 | 3 | €10.000 | T3 x2 + T1 x1 |
| Gen 2027 | 4 | €14.500 | T3 x2 + T4 x1 + T2 x1 |
| Feb 2027 | 4 | €13.000 | T3 x3 + T1 x1 |
| Mar 2027 | 5 | €17.000 | T3 x3 + T4 x1 + T1 x1 |
| Apr–Giu 2027 | 4–5/mese | €45.000 | T3 x3 + T2 x1 + retainer B2B/mese |
| **TOTALE ANNO 1** | **~30–35 incarichi** | **~€122.500** | |

**Riepilogo Anno 1 Scenario Base:**
- Ricavo lordo: ~€122.500
- Costi diretti: ~€54.000 `[I]` (margine medio ~44% dato il mix più alto T4)
- Investimento GTM: €10.600–13.150 (scenario raccomandato dal brief); punto medio €11.875
- **Contribuzione netta:** (€122.500 – €54.000 costi diretti) – €11.875 GTM = €68.500 – €11.875 = **~€56.625**
- Ricavo TTP (ore Sara @50€/h): `[I]` ~€22.500 (Sara ~450h Anno 1)
- **Netto cliente (Boschetti) Anno 1:** ~€122.500 – costi partner – fee TTP – GTM = ~€45.000–55.000 `[I]`

---

### Scenario C — Ottimistico

**Ipotesi:** Tutto lo Scenario B + B2B attivo a regime pieno in Q4 (3 partner firmati), il buzz sulla flat tax italiana HNWI genera 2–3 casi T4, referral Golden Visa IT attivati tramite rete partner, SEO genera traffico significativo da Q1 2027.

| Trimestre | Incarichi | Ricavo Lordo |
|-----------|-----------|-------------|
| Q3 2026 (Lug–Set) | 3 | €9.500 |
| Q4 2026 (Ott–Dic) | 12 | €42.000 |
| Q1 2027 (Gen–Mar) | 15 | €65.000 |
| Q2 2027 (Apr–Giu) | 18 | €78.000 |
| **TOTALE ANNO 1** | **~48 incarichi** | **~€194.500** |

Contribuzione retainer B2B Q4–Q2: 3 partner × €1.500/mese × 6 mesi = €27.000 inclusi nel totale sopra.

**Riepilogo Anno 1 Scenario Ottimistico:**
- Ricavo lordo: ~€194.500
- Costi diretti: ~€85.000 `[I]`
- Investimento GTM: ~€13.150 (tetto del range raccomandato)
- **Contribuzione netta:** ~€109.500 – €13.150 = **~€96.350**
- Ricavo TTP: `[I]` ~€35.000 (Sara ~700h Anno 1)
- **Netto cliente (Boschetti) Anno 1:** ~€65.000–80.000 `[I]`

---

### Tabella Riepilogativa Scenari Anno 1

| Metrica | Leggero | Base | Ottimistico |
|---------|---------|------|-------------|
| Incarichi chiusi | ~20 | ~30–35 | ~48 |
| Ricavo Lordo | ~€59.500 | ~€122.500 | ~€194.500 |
| Costi Diretti `[I]` | ~€29.750 | ~€54.000 | ~€85.000 |
| Investimento GTM | €8.100–10.100 | €10.600–13.150 | ~€13.150 |
| **Contribuzione Netta** | **~€20.650** | **~€56.625** | **~€96.350** |
| Ricavo TTP `[I]` | ~€15.000 | ~€22.500 | ~€35.000 |
| Netto Cliente `[I]` | ~€22.000 | ~€48.000 | ~€72.000 |

---

## §4 — Proiezione Anno 2

### Ipotesi per l'Anno 2
- Anno 1 Base validato. Boschetti si espande: desk ES attivo Q2 2027, desk DE attivo Q3 2027, desk FR Q1 2028.
- L'ingaggio TTP di Sara continua (formato retainer continuativo `[I]`).
- B2B: 4–5 partner in retainer attivi dall'inizio dell'Anno 2.
- SEO inizia a generare lead organici costanti (minimo 3–5/mese dal blog).
- Vincolo capacità alzato: `[IPOTESI]` Boschetti assume un coordinatore casi part-time a ~€1.500/mese, consentendo 8–10 casi/mese.

### Proiezione Trimestrale Anno 2 (range Base → Ottimistico)

| Trimestre | Incarichi | Ricavo Lordo | Note |
|-----------|-----------|-------------|------|
| Q3 2027 (Lug–Set) | 15–20 | €55.000–75.000 | Desk ES attivo, SEO in crescita |
| Q4 2027 (Ott–Dic) | 18–25 | €65.000–95.000 | Pilota desk DE, B2B scalato |
| Q1 2028 (Gen–Mar) | 20–28 | €75.000–105.000 | 4 desk semi-attivi |
| Q2 2028 (Apr–Giu) | 22–30 | €82.000–112.000 | Regime pieno |
| **TOTALE ANNO 2** | **75–103 incarichi** | **€277.000–387.000** | |

**Riepilogo Finanziario Anno 2 (range Base–Ottimistico):**
- Ricavo Lordo: €277.000–387.000
- Costi diretti (inclusi 4 desk partner + coordinatore casi): `[IPOTESI]` ~€120.000–160.000
- GTM Anno 2 (SEO continuativo + esperimenti paid): `[IPOTESI]` ~€18.000–24.000/anno
- **Contribuzione Netta Anno 2:** ~€130.000–200.000
- Ricavo TTP Anno 2: `[IPOTESI]` €35.000–55.000

> **Verifica salute Anno 2:** Il netto Anno 2 del cliente (Boschetti) è nel range €90.000–145.000 `[I]` — questo è il momento in cui il modello diventa genuinamente autosufficiente con chiaro spazio per assunzioni.

---

## §5 — Analisi Break-Even

### Cosa Significa Break-Even in Questo Contesto?
Due punti di break-even distinti:
1. **Recupero investimento GTM:** Quando il margine di contribuzione cumulativo > spesa GTM
2. **Recupero costo TTP:** Quando il ricavo EVA giustifica le fee TTP a Boschetti (ROI positivo per il cliente)

### Break-Even GTM (Scenario Base)

- Investimento GTM totale (raccomandato): **€11.875** (punto medio di €10.600–13.150)
- Margine di contribuzione medio per incarico: **~€1.780** `[I]` (media ponderata sul mix T1–T4 ipotizzato nello scenario base)

> Break-Even GTM = €11.875 / €1.780 = **~6,7 incarichi**

Al ritmo dello scenario base (primi incarichi da settembre 2026), il break-even sull'investimento GTM viene raggiunto entro **novembre–dicembre 2026** — nel primo trimestre attivo.

### Break-Even Operativo Mensile

Costi ricorrenti mensili per Boschetti (Anno 1):
- Lavoro TTP continuativo: `[IPOTESI]` ~€1.500–2.000/mese (Sara ~30–40h/mese)
- Costi partner locale per caso attivo: variabile (~€500–1.500/caso)
- Costo del tempo di Boschetti (costo opportunità): `[IPOTESI]` €100–150/h tariffa professionale → ~€3.000–4.500/mese a 30h su EVA

**Costo mensile totale per sostenere EVA:** ~€5.000–8.000/mese `[I]`

**Incarichi/mese di break-even:**
- A ricavo medio per incarico €3.500 (ponderato T3): ~1,4–2,3 incarichi/mese
- **Minimo: 2 incarichi completati/mese per coprire tutti i costi correnti**

> Implicazione pratica: Da ottobre 2026 in poi, EVA ha bisogno di **2 casi equivalenti T3 chiusi/mese** per operare a cash-flow neutro. Raggiungibile nello scenario base. Non raggiungibile nello scenario Leggero fino a Q1 2027.

### Tabella Riepilogativa Break-Even

| Tipo Break-Even | Incarichi Necessari | Tempistica Stimata (Base) |
|----------------|--------------------|-----------------------------|
| Recupero investimento GTM | ~7 cumulativi | Nov–Dic 2026 |
| Cash-flow neutro mensile | ~2/mese | Ott–Nov 2026 |
| Fee TTP autofinanziate da EVA | ~3/mese | Gen 2027 |
| ROI Anno 1 positivo totale | ~18 cumulativi | Feb–Mar 2027 |

---

## §6 — Allocazione Budget GTM

### Budget Totale: €10.600–13.150 (Scenario Raccomandato)

Utilizzando il punto medio **€11.875** per l'analisi di allocazione.

| Fase | Componente | Costo | % del Budget | Ipotesi ROI |
|------|-----------|------|-------------|------------|
| **Fondamenta** | Registrazione dominio + configurazione DNS | €20–50 `[I]` | <1% | Prerequisito — nessun ROI senza questo. Urgenza = CRITICA |
| **Fase 1 — MVP Digitale** | Sito WordPress (multilingua IT/PT/EN) | €5.000–6.000 | 42–50% | Asset principale di conversione. Ogni incarico passa dal sito. ROI: il sito si ripaga a 2 casi T3. Payback: mese 2–3 dall'attivazione. |
| **Fase 1 — MVP Digitale** | Blog SEO + piano editoriale | €500 | 4% | Asset in crescita composta. ROI completo 12–18 mesi. Zero costo marginale per lead organico una volta in classifica. |
| **Fase 2 — Quick Win Brasiliani** | Campagna brasiliana 3-email (Brevo PT) | €600 | 5% | Canale a CAC più basso e volume più alto. ~19K contatti = miglior ROI per € nell'Anno 1. Target: 2–3 incarichi dalla campagna. ROI se 2 T3 chiusi: €600 → €8.000 ricavo lordo = 13x. |
| **Fase 3 — Setup GTM** | Opzione B: Setup & Run (1.700–2.550€ + 400–500/mese × 7 mesi) | €4.500–6.000 | 38–50% | Gestione continuativa dei canali + tracking. ROI misurato tramite lead velocity e CAC per canale. Non un ritorno una tantum ma un moltiplicatore operativo. |
| **TOTALE** | | **€10.620–13.150** | **~100%** | |

### Prioritizzazione Budget (se vincolati allo scenario leggero):
1. Dominio — non negoziabile (€50)
2. Campagna brasiliana — ROI immediato per € più alto (€600)
3. Sito MVP — versione minima viabile (€5.000)
4. Piano SEO — sfrutta l'investimento nel sito (€500)
5. Setup GTM — ridurre lo scope a "Go" non "Run" se necessario

---

## §7 — CAC per Canale

`[IPOTESI — tutte le stime CAC sono benchmark di settore adattati al contesto EVA. Il CAC reale varierà in modo significativo. Misurare dal Mese 3 in poi.]`

### Stime CAC per Canale

| Canale | Investimento | Lead Stimati | Conversione a Incarico | Incarichi Stimati | CAC per Incarico |
|--------|-------------|--------------|----------------------|-------------------|-----------------|
| Campagna email brasiliana (PT, 19K contatti) | €600 | 50–80 risposte | 5–10% | 3–8 incarichi | **€75–200/incarico** |
| Outreach LinkedIn B2B (manuale, Sara) | Solo tempo (~€2.000 ore Sara `[I]`) | 20–40 connessioni qualificate/mese | 10–15% a retainer | 2–4 partner B2B Anno 1 | **€500–1.000/partner** |
| SEO organico | €500 setup + tempo contenuto | 10–30/mese entro mese 8 `[I]` | 3–7% | 5–15 Anno 1 | **€100–200/incarico a regime** |
| Rete referral (clienti esistenti Boschetti) | €0 diretto | Variabile | 40–60% (lead caldo) | 5–10 Anno 1 `[I]` | **€0–50** (solo costo ore Sara) |
| Ricerca paid (non in budget Anno 1) | €0 | — | — | — | €300–600 `[I]` (benchmark legale EU) |

### Implicazioni CAC
- **Email brasiliana** è il canale a costo più basso e volume più alto nell'Anno 1. Il database dei 19K contatti è il singolo asset esistente più prezioso di EVA. Proteggerlo e attivarlo correttamente (sequenza PT in 3 step) è la priorità GTM principale dopo il sito.
- **Referral** ha CAC quasi zero e il tasso di conversione più alto — la fiducia esistente dei clienti di Boschetti si trasferisce. Tracciare e incentivare esplicitamente dal primo giorno.
- **SEO** ha CAC negativo dopo il break-even (capitalizzazione). Ogni articolo si posiziona una volta e genera lead a tempo indeterminato. Nel lungo periodo è il canale più efficiente in termini di capitale.
- **LinkedIn B2B** ha un alto costo in ore Sara ma genera alto LTV (€18K/anno per partner retainer). L'effort è giustificato una volta che il sito e gli asset di credibilità sono live (ottobre 2026+).

---

## §8 — Analisi di Sensitività

### Variabili Chiave
1. **Ricavo medio per incarico (Ricavo Medio)** — la più sensibile: pricing non confermato
2. **Tasso di conversione dai lead (Tasso Conv.)** — variabile comportamentale
3. **% attivazione B2B** — binario nell'Anno 1, continuo nell'Anno 2
4. **Costo partner locale** — non confermato, potrebbe erodere i margini

### Matrice di Sensitività: Contribuzione Netta Anno 1 (Scenario Base come Base)

*Variando Ricavo Medio per Incarico × Tasso di Conversione (a volume 30 incarichi, base)*

| Ricavo Medio / Incarico | Conv 3% | Conv 5% | Conv 8% | Conv 12% |
|------------------------|---------|---------|---------|----------|
| €2.500 | €22.500 | €37.500 | €60.000 | €90.000 |
| €3.500 | €31.500 | €52.500 | €84.000 | €126.000 |
| **€4.000 (base)** | **€36.000** | **€60.000** | **€96.000** | **€144.000** |
| €5.500 | €49.500 | €82.500 | €132.000 | €198.000 |

*Nota: Margine di contribuzione al ~56% applicato. Costi GTM sottratti dai totali. Volume mantenuto costante a 30 incarichi per isolare gli effetti prezzo/conversione.*

### Matrice di Sensitività: Ricavo Anno 1 × Attivazione B2B

| Partner B2B Attivi Q4 | 0 partner | 1 partner | 3 partner | 5 partner |
|----------------------|-----------|-----------|-----------|-----------|
| Ricavo B2B (7 mesi) | €0 | €10.500 | €31.500 | €52.500 |
| Ricavo B2C (base 30 inc.) | €122.500 | €122.500 | €122.500 | €122.500 |
| **Ricavo Lordo Totale** | **€122.500** | **€133.000** | **€154.000** | **€175.000** |

`[I]` Retainer B2B a €1.500/mese × 7 mesi attivi. Ricavo B2C costante.

### Principali Risultati dell'Analisi di Sensitività
1. **Il prezzo è la variabile con la leva più alta.** Passare da €3.500 a €4.000 di ticket medio (+14%) aumenta la contribuzione netta di ~€15.000 al volume base. La disciplina sul pricing vale più della crescita di volume nell'Anno 1.
2. **Il B2B è il motore dell'Anno 2, non dell'Anno 1.** Anche solo 1 partner in Q4 aggiunge €10.500 al ricavo lordo a costo marginale quasi zero — ma l'attivazione B2B dipende dagli asset di credibilità (sito + case study) che esistono solo dopo Q3 2026.
3. **I costi partner locali sono un rischio di margine.** Se i costi partner sono €1.500/caso invece dei €600 stimati, il margine di contribuzione scende dal 56% a ~40% sul T3. `[CRITICO — da confermare con Boschetti prima di qualsiasi impegno di pricing verso il mercato]`
4. **Sensitività al tasso di conversione:** EVA è un business ad alto ticket e basso volume. A prezzi T3, 2 casi chiusi aggiuntivi/mese = €8.000 ricavo lordo. Piccoli miglioramenti di volume assoluti hanno un impatto sproporzionato. Focus sul tasso di chiusura, non sul volume di traffico.

---

## §9 — Registro delle Ipotesi

Tutti i numeri in questo modello non direttamente ricavati dal brief o da EVA_context.md sono elencati qui con fonte e livello di confidenza.

| # | Ipotesi | Valore Utilizzato | Fonte | Confidenza | Azione Richiesta |
|---|--------|------------------|-------|------------|-----------------|
| A01 | Pricing T1 Comparative Snapshot | €400–800 (target €600) | Benchmark mercato advisory immigrazione EU | Bassa | Confermare con Boschetti |
| A02 | Pricing T2 Advisory + Roadmap | €1.000–2.000 (target €1.500) | Benchmark advisory premium EU | Bassa | Confermare con Boschetti |
| A03 | Pricing T3 Caso Completo Standard | €2.800–5.500 (target €4.000) | Proxy competitor Oliveira/Balcells + premium 20% | Bassa-Media | Confermare con Boschetti |
| A04 | Pricing T4 HNWI | €5.500–9.000 (target €7.500) | Range advisory premium Henley/IMI | Bassa | Confermare con Boschetti |
| A05 | Pricing T5 Retainer B2B | €1.000–2.000/mese (target €1.500) | Benchmark legale/advisory frazionale PMI EU | Bassa | Confermare con Boschetti |
| A06 | Ore Sara per caso T3 | 20h | Stima advisory servizi professionali | Media | Confermare con Sara dopo primi casi |
| A07 | Costo partner locale per caso T3 | €600 media | Nessun dato — derivato dal target di margine | Molto Bassa | CRITICO — confermare con Ioana (desk PT) immediatamente |
| A08 | Overhead per caso | €150 flat | Benchmark servizi professionali micro-PMI | Media | Monitorare il reale |
| A09 | Vincolo capacità Boschetti | 5 casi/mese max | Ipotesi studio mono-risorsa | Bassa | Confermare con Boschetti — determina il tetto |
| A10 | Ore totali Sara Anno 1 su EVA | 300–700h (per scenario) | Derivato da volume casi × ore/caso | Media | Tracciare dal Giorno 1 |
| A11 | Conversione email brasiliana | 5–10% a lead qualificato | Benchmark email marketing, lista warm | Bassa-Media | Misurare dopo Fase 2 |
| A12 | Volume lead organico SEO Mese 8 | 10–30/mese | Benchmark SEO advisory immigrazione | Bassa | Verificare al Mese 6 |
| A13 | Volume referral Anno 1 | 5–10 incarichi | Stima dai 2K+ clienti esistenti di Boschetti | Bassa | Tracciare la fonte referral dal Giorno 1 |
| A14 | Costo coordinatore casi Anno 2 | €1.500/mese | Tariffa professionale part-time italiana | Bassa | Decisione per pianificazione Anno 2 |
| A15 | Tariffa oraria professionale Boschetti | €100–150/h | Tariffa di mercato avvocato immigrazione italiano | Media | Usata solo per calcolo costo opportunità |
| A16 | Tasso retention retainer B2B | 70% a 12 mesi | Benchmark retention servizi professionali | Bassa | Misurare dopo 6 mesi |
| A17 | Pricing T3 competitor (mono-paese) | €1.500–4.000 | Analisi siti web, inferenza indiretta | Media | Monitorare pricing pubblico competitor |
| A18 | Aggiornamento flat tax italiana (€300K/anno nel 2026) | Come indicato | EVA_context.md — fonte verificata | Alta | Nessuna azione necessaria |

---

## Riferimento Rapido: Numeri Chiave per Sara

| Metrica | Valore |
|---------|--------|
| Break-even investimento GTM | ~7 incarichi cumulativi |
| Cash-flow neutro mensile | 2 incarichi equivalenti T3/mese |
| Ricavo target Anno 1 (Base) | ~€122.500 lordo |
| Contribuzione netta Anno 1 (Base) | ~€56.625 |
| Canale a ROI più alto Anno 1 | Email brasiliana (€600 → potenziale 13x) |
| Segmento a LTV più alto | Retainer B2B (€18K/anno per partner) |
| Variabile non confermata più critica | Costi partner locali per caso |
| Rischio pricing più critico | Disciplina sul floor pricing — mai sotto il floor |
| Range ricavo Anno 2 | €277K–387K (base→ottimistico) |

---

*Versione modello: v1.0 — 2026-06-06 | Agente Calculator*
*Trigger prossima revisione: dopo i primi 5 incarichi completati (dati reali sui costi disponibili)*
*Validazione critica richiesta: A07 (costi partner) e A01–A05 (tutti i prezzi) prima di qualsiasi utilizzo verso il cliente*
