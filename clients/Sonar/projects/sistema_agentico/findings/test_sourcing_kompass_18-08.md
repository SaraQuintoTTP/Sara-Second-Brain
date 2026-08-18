# SONAR — Primo test di estrazione database aziende (Kompass EasyBusiness)
### 2026-08-18 | Orchestrator

## Cosa è stato fatto
Primo test reale del componente C1 (Sourcing), su richiesta di Sara. Account di prova gratuita (14 giorni, 10 crediti) creato su **Kompass EasyBusiness** (Sara ha effettuato lei stessa login/registrazione — vedi regola: non inseriamo mai password anche se fornite).

## Filtri applicati
- **Categoria**: "Tessili, abbigliamento, cuoio, orologeria, gioielleria" + "Elettricità, elettronica, ottica" (tassonomia propria di Kompass, non ATECO) — **solo tipo "Produttore"** (escluso Distributore/Servizio: un primo giro con questi inclusi aveva fatto entrare commercio al dettaglio, es. un negozio di abbigliamento — filtro corretto dopo verifica)
- **Provincia**: Padova, Venezia, Treviso, Vicenza (P1 del documento)
- **Addetti**: 10-50 esatti
- **Fatturato**: 0,5-20 milioni EUR

**Universo risultante: 2.432 aziende.** Coerente con l'obiettivo di 40 aziende vertical + 60 generaliste del pilota Sprint 0 — questo è il bacino da cui pescare, non il bacino finale.

## Esportazione (5 crediti su 10, ne restano 5)
Esportate le prime 5 righe visibili in prova gratuita (3 aziende uniche, 2 con doppia sede). Dati ottenuti per azienda: **P.IVA, indirizzo, forma giuridica, ATECO, fatturato per anno (fino a 3 anni), EBIT/EBITDA, utile netto, capitale sociale, classe di rischio, certificazioni, sito/PEC/telefono**. Qualità nettamente superiore alla ricerca web libera usata per l'arricchimento del portafoglio clienti storico (voce 1 checklist).

## Esito: 2 su 3 aziende inserite in `Aziende` (schema Allegato B)

| Azienda | ATECO | Fatturato | Esito |
|---|---|---|---|
| **AUDES GROUP S.R.L.** (Limena, PD) | 14.19 - abbigliamento e accessori | 14,76M€ (2025) | **Candidato pulito** — utile netto positivo e in crescita 2022-2025, certificazioni ISO, nessun segnale anti-ICP evidente |
| **GS PELLETTERIE S.R.L.** (Vicenza) | 15.12 - pelletteria | 1,67M€ (2023) | **Da verificare prima di procedere** — controllata di RICHEMONT INTERNATIONAL HOLDING SA (gruppo lusso multinazionale): rischio anti-ICP "governance" (funzione marketing/IT centralizzata, decisore difficile da raggiungere senza filtro corporate). Utile netto negativo 2 anni consecutivi |
| ~~COSTRUZIONI DONDI S.P.A.~~ | 42.21 - costruzione opere pubbliche/fluidi | 9,77M€ | **Esclusa, non inserita** — rumore di classificazione: è entrata perché Kompass classifica alcune infrastrutture sotto "Elettricità, elettronica, ottica", ma è edilizia/impiantistica, fuori dal vertical Manifattura/produzione B2B (moda-tessile-calzature) |

Entrambe scritte in `Aziende` con `stato = "Sourcing completato - in attesa contatti/segnali (C2/C4)"`: **non sono pronte per un contatto commerciale**. Mancano ancora: analisi asset digitale (sito/e-commerce/social, per i flag FIT), ricerca contatti/decisore (C2), verifica anti-ICP completa, calcolo punteggi (C4). `base_giuridica` segnata come provvisoria in attesa del responsabile conformità (checklist voce 9, ancora aperta).

## Secondo test: segnali e classificazione (C4), sulle 2 aziende sourciate

Completata l'analisi FIT (S1 struttura + S2 maturità digitale, verificata con ricerca reale) e la ricerca segnali TIMING (S3-S6) per entrambe le aziende, poi eseguito il motore deterministico (`sonar_engine.py score`).

**Verifica digitale:**
- **Audes Group**: sito audes.com attivo (WordPress, blog aggiornato a 2026, social attivi) — ma è un'agenzia B2B che *offre* e-commerce ai clienti (Abarth, Vodafone), non ha un proprio e-commerce transazionale
- **GS Pelletterie**: nessun sito web trovato (confermato anche fuori da Kompass, con ricerca web dedicata)

**Ricerca segnali TIMING:** nessun segnale valido trovato per nessuna delle due. Non per mancanza di ricerca: per Audes sono stati trovati 2 eventi reali (cambio sede giugno 2021, lancio prodotto "Clolife®" gennaio 2024) ma **entrambi fuori dalla finestra di validità di 180 giorni** prevista dal motore — quindi correttamente esclusi, non forzati.

**Risultato del motore** (`sonar_engine.py score` + `queue`):

| Azienda | FIT | TIMING | PONTE | Coda | Comportamento previsto |
|---|---|---|---|---|---|
| AUDES GROUP S.R.L. | 70 | 0 | 0 | **C** | Coltivazione (contenuti, inviti a eventi), rilettura a 90 giorni — **nessuna azione commerciale ora** |
| GS PELLETTERIE S.R.L. | 50 | 0 | 0 | **Fuori (residuale)** | Esclusa: FIT insufficiente (30-59) senza un Ponte ≥60 a compensare |

`sonar_engine.py queue --cap 25` → correttamente 0 aziende in coda (coda C non genera assegnazione settimanale, per disegno del documento). Il motore ha funzionato end-to-end su dati reali senza errori.

**Cosa dimostra questo test:** il sistema non "promuove" tutto quello che passa il primo filtro di sourcing — su 2 aziende reali con buoni fondamentali di fatturato/settore/dimensione, nessuna è arrivata pronta per un contatto commerciale. È il comportamento corretto e atteso (par. 7.4): serve un Ponte forte o un segnale di timing fresco, non basta il FIT. Conferma anche che la fase C4 "scanner segnali" è il collo di bottiglia reale del sistema — richiede ricerca mirata e ripetuta nel tempo, non un'esecuzione una tantum.

## Terzo test: componente Ponte (C3), sulle 2 aziende sourciate

Verificate a mano le 3 fonti previste dal documento (cap. 6) per entrambe le aziende:
1. **Portafoglio clienti storico ATMAN** (74 clienti in `Portafoglio_Clienti_ATMAN`)
2. **Rete professionale ATMAN** (non ancora popolata — checklist voce 2 parziale)
3. **Segnalatori attivi** (i 3 registrati in `Rete_Professionale_Segnalatori`: Fabio Righetto/Zucchetti, Alessandro Murador/Rapax Mangimi, Valeria Apolloni)

**Risultato: nessun collegamento trovato per nessuna delle due aziende — PONTE = 0 per entrambe.** Nessuna sovrapposizione di settore plausibile tra i 3 segnalatori (software gestionale, mangimistica, grafica) e moda/pelletteria; nessun amministratore/socio in comune identificabile gratuitamente (dietro visura camerale a pagamento per entrambe le aziende).

**Scoperta laterale utile per C2 (non è un Ponte, ma aiuta il prossimo passo):** durante la ricerca è emerso il decisore di Audes Group — **Alessandro Bozzoli**, fondatore/CEO/amministratore unico, esperienza precedente in PwC e Icona Real Estate SRL, attivo e raggiungibile su LinkedIn. Aggiornato `fit_decisore_raggiungibile=True` per Audes → **FIT sale da 70 a 75**, coda resta C (manca comunque Ponte o Timing).

**Cosa dimostra questo test:** il processo di ricerca Ponte è interamente manuale/guidato per costruzione (par. 6: "match assistito... fonte primaria è la memoria del team, non automatizzabile") ed è normale che l'esito sia "nessun collegamento" quando il perimetro di rete di ATMAN (73 clienti + 3 segnalatori, entrambi settorialmente distanti da moda/pelletteria) non copre il prospect. Più la rete professionale e i segnalatori si allargano (checklist voce 2, ancora aperta), più aumenta la probabilità di trovare un Ponte reale — è la ragione strutturale per cui completare quella voce vale più di aggiungere aziende al sourcing.

## Lezione per il prossimo giro
Filtrare solo su "Produttore" non basta a garantire pertinenza di settore quando la tassonomia della fonte (Kompass) non coincide con ATECO — utile un controllo a campione dei risultati prima di fidarsi del conteggio. Confermato però che **incrociare più fonti** (come raccomandato in `knowledge_base/fonti_sourcing_aziende.md`) avrebbe aiutato: Costruzioni Dondi non sarebbe comparsa incrociando con un filtro ATECO reale (Telemaco).
