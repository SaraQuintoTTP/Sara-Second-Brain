# EVA — God Mode Quality Scorecard
## analisi_mercato_2026 | Tre deliverable: Strategist + Calculator + Voice
### God Mode | 2026-06-06 | v1.0

---

> **Knowledge Skills status:** ttp-7dimensions-quickref.md e klein-premortem-quickref.md trovati ma sono placeholder (status: TODO). Audit condotto su base knowledge 7-dimension standard. Flag a Orchestrator per completamento skills in sessione dedicata.
> **Files auditati:**
> - strategist_positioning.md (v1.0)
> - calculator_financials.md (v1.0)
> - voice_messaging.md (v1.0)
> **Reference documents letti:** brief.md ✓ | EVA_context.md ✓

---

## VERDETTO GLOBALE

### **PASS WITH RESERVATIONS**

Nessun blocking issue di tipo FAIL assoluto. Un'anomalia significativa nel modello finanziario (Scenario A incoerente con le premesse dichiarate) e due gap strutturali (dati cliente non originali nel Calculator, coerenza cross-deliverable parziale) richiedono revisione prima della consegna a Sara. I tre deliverable sono individualmente solidi ma il Calculator contiene numeri che non reggono allo stress test interno.

---

## TABELLA SCORECARD: 7 DIMENSIONI × 3 DELIVERABLE

*Scale: 1 (blocking), 2 (conditional — revisione richiesta), 3 (accettabile con nota), 4 (buono), 5 (eccellente)*

| Dimensione | Strategist | Calculator | Voice | Note sintetiche |
|---|---|---|---|---|
| **1. Completeness** | 5 | 4 | 5 | Strategist: 8 sezioni complete, nessuna richiesta mancante. Calculator: manca la sezione su Boschetti come risorsa vincolante nel calcolo ore (nominata ma non quantificata nella break-even). Voice: completo. |
| **2. Strategic accuracy** | 5 | 3 | 5 | Strategist e Voice: coerenti con brief e con dati verificati. Calculator: Scenario A problematico — vedi blocking issues §3. |
| **3. First Principles grounding** | 5 | 3 | 4 | Strategist: ogni claim tracciato a EVA_context.md o brief.md. Calculator: pricing non ha fonte cliente, ma flaggato [ASSUMPTION] correttamente. Voice: l'affermazione "no European law firm offers structured comparative advice" (Pillar 2) è strong claim senza citazione specifica — usato Enthous report come fonte indiretta ma non esplicitata nel testo. |
| **4. Actionability** | 5 | 4 | 4 | Strategist: 5 azioni concrete, go/no-go metriche per ogni leva. Calculator: KRS (Key Reference Summary) operativa. Voice: copy pronto all'uso ma la CTA "Book your free 30-minute profile call" per Digital Nomads (§5, Profile 1) introduce il termine "free" — non allineato con il modello di pricing T1 (€400–800 minimum). |
| **5. Framework application** | 5 | 3 | 5 | Strategist: De Veglia Test del Contrario e Test dei Limiti applicati esplicitamente a EVA, non come template generico. Calculator: Profit First e Staircase of Value non caricati (skills mancanti — flaggato correttamente). Framework sostitutivo adeguato ma non esplicitato. Voice: Messy Middle e JOLT Effect applicati specificamente ai profili EVA. PAS visibile nei pillars. |
| **6. Assumption transparency** | 5 | 5 | 4 | Strategist: 7 assunzioni numerate con risk level e validation method. Calculator: 18 assunzioni con confidence level e action required — il migliore della triade su questa dimensione. Voice: 1 assunzione implicita non dichiarata — il "free 30-minute call" come CTA assume che Boschetti voglia offrire chiamate gratuite; mai validato nel brief. |
| **7. Format compliance** | 5 | 4 | 5 | Strategist: struttura attesa rispettata, sezioni ben titolate. Calculator: tabella Sensitivity Matrix §8 ha una nota metodologica ambigua (vedi §3 conditional items). Voice: struttura pulita, tabelle where/how to speak corrette. |

**Media Strategist: 5.0 | Media Calculator: 3.7 | Media Voice: 4.6**

---

## §1 — BLOCKING ISSUES (score 1) — NESSUNO

Nessun deliverable riceve score 1 in nessuna dimensione. Nessun blocking issue di livello FAIL assoluto identificato.

---

## §2 — CRITICAL ISSUES (score 2–3 con impatto elevato) — 3 TROVATI

### ISSUE 1 — Calculator: Scenario A è internamente incoerente con le proprie premesse [CRITICO]
**Localizzazione:** calculator_financials.md §3 Scenario A
**Problema:** Lo Scenario A è dichiarato "Conservative" con premessa esplicita: "Slow site SEO traction, Brazilian campaign yields 2 conversions, B2B does not activate in Year 1, no Golden Visa cases Year 1." Tuttavia il totale indicato è **~20 incarichi** per **~€59,500** gross.

Verifica interna: La tabella mensile mostra:
- Sep 2026: 1 incarico → €1,500
- Oct 2026: 2 → €5,500
- Nov 2026: 2 → €5,500
- Dec 2026: 2 → €4,500
- Jan 2027: 2 → €4,500
- Feb 2027: 3 → €7,500
- Mar 2027: 3 → €8,000
- Apr–Jun 2027: 3/mo → €22,500

Somma incarichi tabella: 1+2+2+2+2+3+3+9 = **24 incarichi** (non 20).
Somma revenue tabella: €1.500+5.500+5.500+4.500+4.500+7.500+8.000+22.500 = **€59,500** (questo è corretto).

Ma: il Mix per Feb–Mar 2027 include T3×2 = €8,000/mese (T3 target €4,000) + T2×1 = €1,500. Revenue per Feb: 2×4.000+600=€8.600 ≠ €7.500 dichiarato. Incoerenza nel mix → revenue non quadra in alcuni mesi.

Più grave: Scenario A assume "2 conversions from Brazilian campaign" e "no B2B, no Golden Visa" — ma il ritmo da ottobre in poi (2–3 incarichi/mese) è sostenuto da fonti non esplicitate (né SEO né referral sono descritti). Il modello non specifica l'origine di questi 18+ incarichi aggiuntivi oltre ai 2 brasiliani.

**Impatto:** Sara non può usare Scenario A come "conservative floor" perché l'assunzione generatrice dei numeri non è dichiarata. Il rischio è che Boschetti usi questo come piano di riferimento conservativo e prenda decisioni (capacity, pricing, timing) su una base non verificata.

**Azione richiesta:** Calculator deve (a) riconciliare il conteggio incarichi, (b) esplicitare la fonte degli incarichi da ottobre in poi in Scenario A, (c) correggere le discrepanze di revenue mensile nel mix.

---

### ISSUE 2 — Calculator: la "Net Contribution" nel Summary Table non è comparabile cross-scenario [SIGNIFICATIVO]
**Localizzazione:** calculator_financials.md §3 Year 1 Scenario Summary Table + righe Base e Optimistic

**Problema:** La riga "Net Contribution" nei tre scenari usa metodologie diverse:
- **Light:** Net Contribution = ~€20,650 calcolato come (Direct Costs – GTM). Formula dichiarata: "~€29,750 – €9,100 = ~€20,650". Ma €29,750 è il direct cost, non la contribution. La formula dovrebbe essere Revenue – DirectCosts – GTM = €59,500 – €29,750 – €9,100 = €20,650. Numericamente corretto ma la formula dichiarata è errata (scrive "~€29,750 – €9,100" senza sottrarre i costi variabili da revenue).
- **Base:** Net Contribution = ~€56,625 = "~€68,500 – €11,875 GTM". Ma €68,500 non è mai definito nel testo precedente. Dovrebbe essere Revenue – DirectCosts = €122,500 – €54,000 = €68,500. Corretto numericamente ma €68,500 appare senza spiegazione nella formula inline.
- **Optimistic:** Net Contribution = ~€96,350 = "~€109,500 – €13,150". €109,500 = €194,500 – €85,000 = €109,500. Corretto.

Il Summary Table mostra "Net Contribution" come: ~€20,650 / ~€56,625 / ~€96,350 — questi numeri sembrano corretti, ma le formule narrative nei singoli scenari contengono imprecisioni di presentazione che creano ambiguità per il lettore.

**Impatto:** Moderato — i numeri finali sono probabilmente corretti, ma le formule intermedie sono incomplete e potrebbero ingenerare errori se Sara o Boschetti cercano di ricostruire il calcolo autonomamente.

**Azione richiesta:** Aggiungere una nota metodologica sotto la tabella che esplicita: Net Contribution = Gross Revenue – Direct Costs – GTM Investment.

---

### ISSUE 3 — Voice: CTA "free 30-minute profile call" non è allineata con il modello di pricing [MODERATO]
**Localizzazione:** voice_messaging.md §5, Profile 1 (Digital Nomads), CTA block

**Testo:** *"Book your free 30-minute profile call → Receive your comparative report in 5 working days."*

**Problema:** Il modello di pricing del Calculator definisce T1 (Comparative Snapshot) con un floor di €400 e una nota esplicita: "T1 Snapshot is a strategic 'door opener' — designed to convert to T2/T3. Not a commodity product. Never go below floor even for referrals." La CTA del Voice introduce "free" per la chiamata iniziale — che non è necessariamente in contrasto se la chiamata è separata dal report, ma:
1. Crea un'aspettativa di gratuità che può fare resistenza quando arriva il preventivo T1.
2. Non è mai discussa nel brief come policy aziendale di Boschetti.
3. Il Strategist (§5, Lever 1, GO/NO-GO) parla di "EVA Comparative Assessment — book your slot" senza menzionare "free call" come step preliminare.

Questa discrepanza non è critica, ma è un esempio di incoerenza cross-deliverable che Sara dovrà risolvere prima dell'implementazione.

**Azione richiesta:** Voice deve riallineare la CTA con il modello di pricing. Opzioni: (a) "Book a 30-minute profile call — no obligation" oppure (b) "Start with a €X profile assessment" se il T1 si decide a prezzo fisso.

---

## §3 — CONDITIONAL ITEMS (score 3, da migliorare ma non bloccanti)

### C1 — Voice §5 Pillar 2: claim "no European law firm offers structured comparative advice" non è sourced inline
**Localizzazione:** voice_messaging.md §3, Pillar 2, headline e body
**Nota:** Il claim è forte ("We verified this. We built the one that does.") e la fonte esiste (Enthous SEO report, EVA_context.md) ma non è citata nel deliverable Voice. Nel copy web non è necessaria una citation formale, ma in materiali B2B o editoriali il claim senza fonte crea rischio reputazionale se un prospect la sfida.
**Raccomandazione:** Aggiungere in §7 (Words to Use) o in una nota di utilizzo: "Questo claim richiede footnote o link all'Enthous report quando usato in contesti editoriali/B2B."

### C2 — Calculator §8 Sensitivity Matrix: metodologia non esplicitata
**Localizzazione:** calculator_financials.md §8, Sensitivity Matrix
**Nota:** La nota sotto la matrice dice "Contribution margin at ~56% applied. GTM costs subtracted from totals. Volume held constant at 30 incarichi." Ma le celle mostrano Revenue Gross (non Net Contribution). Per esempio, la cella "Conv 5% / €4,000" = €60,000 — che non corrisponde a Revenue Gross (che sarebbe 30×4.000=€120.000) né a Net Contribution. Le celle sembrano essere solo una variazione del Revenue basata su conversion rate, non su volume fisso. La metodologia non è chiara.
**Raccomandazione:** Aggiungere una riga di intestazione che chiarisca cosa rappresentano i valori nella matrice (Revenue? Contribution? Conversion-adjusted revenue?).

### C3 — Strategist: la risposta "perché il regista" si basa su 3 eventi documentati, ma uno merita verifica
**Localizzazione:** strategist_positioning.md §4, tabella "Three documented regulatory collapses"
**Nota:** I tre eventi sono: (1) Spain GV abolished April 2025 (LO 1/2025) — **verificato** in EVA_context.md. (2) Portugal NHR → IFICI May 2026 — **verificato** in EVA_context.md. (3) Malta direct citizenship invalidated by ECJ 2025 — **verificato** in EVA_context.md come "Malta: cittadinanza diretta invalidata da sentenza CE 2025." La fonte è citata come "ECJ ruling" nel Strategist ma in EVA_context.md è citata come "sentenza CE" senza numero di causa o data precisa. Non è un errore fatale, ma in pitch HNWI un prospect potrebbe chiedere il numero della sentenza.
**Raccomandazione:** Aggiungere il numero della causa ECJ (se reperibile) come footnote nella sezione §4 e in §7 del Voice (Pillar 3). Non blocca il deliverable ma rafforza l'E-E-A-T.

---

## §4 — VERIFICA SPECIFICHE DI AUDIT

### 4.1 — I dati di mercato citati (AIMA, BAMF, Henley, Eurostat, Enthous) sono usati correttamente?

**PASS.** Verifica sistematica:
- **AIMA:** Brasiliani in PT citati nel Voice come "19.000 clienti brasiliani" (Boschetti) e "484.596 residenti" (AIMA) — correttamente distinti. Strategist usa "525.000+ fascicoli AIMA" dalla EVA_context.md correttamente come pain point per il profilo brasiliano. Calculator non usa direttamente dati AIMA.
- **BAMF:** EU Blue Card "41.000+ emessi nel 2023, India 25%+" — usato nel Strategist §2 Profile 4 (ICT Manager). Il dato è presente in EVA_context.md. Usato correttamente.
- **Henley:** "142.000 HNWI in movimento nel 2025" e "UK outflow –16.500" — citato nel Strategist come push factor per HNWI. Corretto.
- **Eurostat:** Non citato esplicitamente nei deliverable ma è fonte di background in EVA_context.md. Non viene distorto.
- **Enthous SEO:** Usato nel Strategist per il Brandshot (21 competitor, gap per NHR/IFICI, Beckham Law). Il claim "65% cluster EVA-core: competizione BASSA" viene citato nel Lean Canvas del Strategist implicitamente attraverso la scelta dei canali SEO. Nessuna distorsione rilevata.

**Unica nota:** Il dato "14.870 ricerche/mese per Spain GV" appare nel Strategist §5 Lever 3 come "14,870 orphan searches/month." In EVA_context.md il dato è "14.870 ricerche/mese" — coerente. La fonte originale è Ministerio Vivienda / Enthous. Il dato non è verificabile indipendentemente da God Mode, ma è consistente internamente tra i documenti.

---

### 4.2 — Le raccomandazioni GTM sono calibrate per studio mono-risorsa con basso budget?

**PASS.** La calibrazione per mono-risorsa è uno dei punti più forti del Strategist. Evidenze:
- §5 "Max 5 agents in parallel" e la nota "mono-resource studio, attempting all three [levers] in parallel generates dilution" — esplicitamente dichiarato.
- Lean Canvas (§3): "Critical omission risk: Boschetti's own time is the binding constraint — not budget" — identificato correttamente.
- Action 3 (database segmentation) è esplicitamente calibrata per proteggere l'asset più prezioso evitando effort sprecato.
- Il Calculator §5 calcola il break-even operativo come "2 T3-equivalent cases/month" — raggiungibile per uno studio mono-risorsa.
- Il Voice non propone campagne paid o strumenti ad alta manutenzione non richiesti.

**Rischio residuo (non bloccante):** Il Scenario Optimistic del Calculator (48 incarichi anno 1, €194.500) richiede una capacità operativa di Boschetti che è dichiaratamente assunta ([A09]: max 5 casi/mese). 48 casi/12 mesi = 4 casi/mese in media — tecnicamente compatibile con A09. Tuttavia il Q2 2027 mostra 18 incarichi in 3 mesi = 6/mese, che supera il cap dichiarato. Non è un errore nell'Optimistic (per definizione ottimistico) ma dovrebbe essere flaggato nel testo come "richiede espansione capacità Boschetti."

---

### 4.3 — La risposta all'obiezione "perché il regista?" è basata su argomenti concreti verificabili?

**PASS, con nota C3.** La risposta è basata su tre argomenti strutturalmente solidi:
1. **Conflitto di interessi strutturale** — non dipende da opinioni, è una realtà economica verificabile.
2. **Prova empirica dei 3 collassi normativi** — tutti e tre presenti in EVA_context.md. La debolezza (C3) è che la sentenza Malta non ha numero di causa identificato.
3. **Analogia MutuiOnline** — chiara, non è un'opinione ma un modello verificabile (MutuiOnline esiste e opera esattamente come descritto).

Il Voice §4 ("The Conductor Objection") sviluppa il medesimo argomento in tre versioni (homepage, LinkedIn, B2B email) — tutti coerenti con il Strategist §4. Nessuna distorsione.

---

### 4.4 — Il modello finanziario ha tutti gli assumption flaggati? I numeri sono internamente consistenti?

**ASSUMPTION FLAGGING: PASS.** Il Calculator è il deliverable più rigoroso su questa dimensione. 18 assunzioni numerate con source e confidence level. Il flag [ASSUMPTION] o [A] è presente su ogni numero non derivato da brief.md o EVA_context.md.

**CONSISTENZA INTERNA: FAIL PARZIALE** — Issue 1 e Issue 2 identificati. Scenario A ha incoerenza nel conteggio incarichi (24 vs 20 dichiarati) e le formule narrative dei Net Contribution nei tre scenari sono incomplete. I numeri finali della Summary Table sembrano corretti, ma il percorso per arrivarci è opaco in due dei tre scenari.

---

### 4.5 — Il messaging rispetta il vincolo deontologico (mai "esperto diritto estero")?

**PASS PIENO.** Il Voice §7 (Words to Avoid) elenca esplicitamente "esperto di diritto estero" come vietato con la nota "Deontological violation. Use instead: 'avvocato italiano' + 'certified local partner'." Il vincolo è applicato sistematicamente in tutto il documento:
- Ogni riferimento al ruolo di Boschetti usa "avvocato italiano."
- I partner locali sono sempre "advogada PT certificata," "abogado ES," etc. — mai presentati come sotto-ordinati diretti di Boschetti né come suoi agenti nell'esercizio del diritto locale.
- La B2B email (§6) usa "Italian lawyer coordinating everything" — corretto: coordination non è pratica del diritto estero.

---

### 4.6 — C'è coerenza tra posizionamento (Strategist), numeri (Calculator) e messaggi (Voice)?

**SOSTANZIALMENTE COERENTE con 1 disallineamento operativo (Issue 3).**

**Coerenze confermate:**
- Sequenza GTM: Strategist define Fase 0 → 1 → 2 → 3 → 4. Calculator §6 riflette le stesse fasi e gli stessi costi (€5.000–6.000 sito, €600 email, €1.700–2.550 GTM Setup). Allineamento perfetto.
- Pricing range: Strategist (Lean Canvas §3) dichiara "EVA Comparative Assessment: €800–1,500." Il Calculator (§1) ha T1: €600 target, T2: €1.500 target. Lieve divergenza: Strategist indica €800 come floor del range, Calculator indica €600 come target e €400 come floor. Non è un errore logico (target ≠ floor) ma comunicare "€800–1.500" in un documento e "target €600" nell'altro è fonte di confusione per Sara.
- Target profiles: Tutti e 5 i profili del Strategist §2 sono coperti nel Voice §5 (3 espansi + B2B). Allineamento confermato.
- Il Strategist dichiara "GO/NO-GO: 0 assessment requests in first 30 days → revisit UVP." Il Voice non cita go/no-go (non è suo compito) ma il processo "assessment → report → recommendation" del Voice §3 Pillar 4 è coerente con la struttura del prodotto nel Strategist Lean Canvas.

**Disallineamento operativo (Issue 3):** "Free 30-minute call" nel Voice vs. nessuna menzione di gratuità nel Strategist GTM e nel pricing del Calculator.

---

## §5 — RACCOMANDAZIONE ALL'ORCHESTRATOR

### Azione richiesta prima della consegna a Sara:

**PRIORITÀ 1 — Calculator (Issues 1 e 2):**
Rispedire al Calculator per:
- Riconciliare Scenario A: correggi il conteggio incarichi (24 vs 20) e aggiungi esplicitamente la fonte degli incarichi Oct 2026 onward (referral? cold SEO? non dichiarato).
- Aggiungere formula esplicita sotto la Summary Table: "Net Contribution = Gross Revenue – Direct Costs – GTM Investment."
- Chiarire la metodologia della Sensitivity Matrix §8 (cosa rappresentano i valori nelle celle).

**PRIORITÀ 2 — Voice (Issue 3):**
Richiedere al Voice Agent di:
- Rivedere la CTA del Profile 1 Digital Nomads: sostituire "free 30-minute profile call" con una formulazione allineata al pricing model (suggerimento: "30-minute profile call — no commitment" oppure allinearsi con Boschetti su policy gratuità prima di pubblicare).

**PRIORITÀ 3 — Cross-deliverable (C1, C2, C3):**
Non bloccanti per consegna ma da comunicare a Sara come "da risolvere in implementazione":
- C1: Aggiungere nota di utilizzo per il claim "no European law firm..." nei contesti B2B.
- C2: Chiarire metodologia Sensitivity Matrix.
- C3: Verificare numero causa ECJ per Malta — aggiungere se reperibile.

**Se Calculator viene corretto su Issues 1 e 2 e Voice su Issue 3 → il bundle diventa PASS pieno.**

---

## §6 — AGENT LESSONS (obbligatorio)

### Strategist — Lezione positiva da replicare
Il Strategist ha prodotto l'assumption log (§8) più completo e correttamente strutturato tra i tre agenti: 7 assunzioni con risk level ("High/Medium/Low") e validation method specifici per ciascuna. Questo formato dovrebbe essere standard per tutti gli agenti che producono deliverable strategici. Il Test del Contrario e il Test dei Limiti (De Veglia) sono stati applicati esplicitamente con output verificabile — non come dichiarazione generica "abbiamo applicato il framework."

### Calculator — Lezione di processo
La mancanza delle Knowledge Skills (Profit First + Staircase of Value) è stata correttamente flaggata in apertura documento. Questo è il comportamento atteso. Tuttavia, l'incoerenza in Scenario A suggerisce che la verifica interna (self-check) tra tabella mensile e total dichiarato non è stata eseguita. **Regola da aggiungere:** ogni modello finanziario deve includere una cella di verifica automatica (somma bottom-up vs. totale dichiarato). Questo non richiede Excel — basta sommare le righe nel testo e confrontarle con il totale prima di scrivere il deliverable.

### Voice — Lezione di allineamento
Il Voice ha prodotto copy di alta qualità formale ma ha introdotto una modalità operativa ("free call") che non esisteva in nessun documento precedente. Questo è il rischio tipico degli agenti che lavorano in sequenza parallela: il Voice non aveva letto il Calculator (o non aveva prestato attenzione al pricing floor). **Regola da aggiungere:** ogni agente che scrive copy con CTA che implicano pricing, commitment o processo operativo deve verificare la coerenza con il documento del Calculator prima di finalizzare. Il Task Tool Prompt Protocol dovrebbe includere il Calculator come Input Reference obbligatorio per il Voice quando il progetto ha un modello economico attivo.

### God Mode — Auto-nota
Le Knowledge Skills di quality (ttp-7dimensions-quickref, klein-premortem-quickref) sono placeholder. L'audit è stato condotto su base knowledge standard — questo è accettabile per questo ciclo ma limita la riproducibilità e la standardizzazione del processo di audit. **Azione raccomandata all'Orchestrator:** schedulare una sessione dedicata al popolamento di queste due skills prima del prossimo ciclo di audit. L'assenza di un Pre-Mortem strutturato (Klein) significa che l'analisi dei rischi sistemici è stata fatta implicitamente piuttosto che attraverso un protocollo formale.

---

*God Mode Scorecard v1.0 — 2026-06-06*
*EVA | Studio Legale Internazionale Boschetti | analisi_mercato_2026*
*Salvo in: /clients/EVA/projects/analisi_mercato_2026/findings/god_mode_scorecard.md*
