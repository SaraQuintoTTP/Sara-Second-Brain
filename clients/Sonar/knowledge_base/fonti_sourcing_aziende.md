# SONAR — Fonti per il sourcing (C1) di database aziende
### Ricerca comparativa | 2026-08-18

Riferimento permanente per il componente C1 (Sourcing). Confronta 9 fonti/sistemi per estrarre aziende italiane target (ragione sociale + **P.IVA** + sede + ATECO + fatturato + addetti — P.IVA è il campo chiave obbligatorio per la deduplica, par. 4.4 del documento).

## Tabella comparativa

| Fonte | Accesso | Copertura Italia/PMI | Filtri ATECO/fatturato/addetti/provincia | P.IVA affidabile | Attendibilità | Giudizio |
|---|---|---|---|---|---|---|
| **Telemaco / Registro Imprese** (InfoCamere) | A pagamento ma economico: 5€ fisso + 0,02-0,12€/posizione. ~100 aziende ≈ 17€ | Ottima — fonte camerale primaria, 100% imprese registrate | Sì, tutti e 4 nativamente | Sì — fonte ufficiale | Massima | **Consigliata — fonte primaria** |
| **Atoka** (SpazioDati) | Freemium/abbonamento (prezzo su richiesta) | Buona — 6M aziende, prodotto italiano pensato per PMI, dati aggiornati quotidianamente | Sì, incl. crescita fatturato — dichiaratamente superiore al solo ATECO | Presumibilmente sì (aggrega dato camerale) | Alta | **Consigliata — incrocio/arricchimento** |
| **Kompass Italia** | Base gratuita; export/funzioni avanzate a crediti | Media-buona — 1,9M aziende in 70 paesi | Sì (in scheda azienda) | Sì, dichiarata in scheda | Media (in parte auto-dichiarato) | Utilizzabile con cautela — verificare P.IVA incrociando con Telemaco |
| **Cribis D&B** (gruppo CRIF) | A pagamento, enterprise (sconto 20% Confindustria) | Ottima — valuta il 100% delle imprese italiane | Sì, molto granulare (rischio, bilanci, legami societari) | Sì, alta qualità | Massima | Sproporzionata per un test da 15-20 aziende — valutare se si scala oltre il pilota |
| **Apollo.io** | Free plan; paid da 49$/utente/mese | Debole per l'Italia — copertura/accuratezza EMEA nettamente inferiore agli USA | Filtri presenti ma dati finanziari EMEA inaffidabili | No — non fonte camerale, spesso assente per aziende italiane | Bassa-media per l'Italia | Solo come arricchimento contatti/decisori dopo aver già identificato le aziende — non come fonte primaria |
| **Scraping Google Maps** | Gratuito ma contro i ToS di Google se automatizzato; alternativa lecita = Google Places API (a pagamento) | Buona per mappatura territoriale locale, meno per B2B manifatturiero puro | No ATECO/fatturato/addetti — solo categoria Maps e zona | No — Maps non espone P.IVA | Bassa (nomi commerciali, non ragioni sociali) | Sconsigliata come fonte primaria per questo vertical; nota GDPR: rischio basso su dati aziendali B2B, evitare scraping di nominativi/recensori privati |
| **Europages** | Gratuito consultazione base | Scarsa per l'Italia — solo ~3.251 aziende italiane elencate, auto-iscrizione | No filtri strutturati fatturato/addetti | No, non affidabile | Bassa (auto-dichiarato) | Sconsigliata come fonte primaria; solo scouting qualitativo aggiuntivo |
| **Sistema Moda Italia / Confindustria Moda** | Gratuito (consultazione pubblica limitata) | Molto rilevante per il vertical scelto (~64.000 imprese Made in Italy associate) ma nessun elenco pubblico scaricabile — richiede contatto diretto | Da verificare via contatto diretto | Non verificabile online | Alta se ottenuto | Utilizzabile con cautela — richiede un passo aggiuntivo, non self-service |
| **LinkedIn Sales Navigator** | A pagamento (~99€/mese/utente da fonti esterne) | Buona per individuare decisori per settore/dimensione dipendenti | Filtra settore/dipendenti, non fatturato né ATECO preciso, non provincia granulare | No — non fonte P.IVA | Media (dato dichiarato dagli utenti) | Più utile per C2 (trovare il decisore raggiungibile) che per C1 (sourcing con P.IVA) |

## Raccomandazione per il primo test (15-20 aziende, vertical Manifattura/produzione B2B)

**Combinazione consigliata — 3 fonti incrociate, non una sola:**
1. **Telemaco come fonte primaria**: unica fonte con tutti e 4 i filtri nativi (ATECO, fatturato a fasce, addetti a fasce, provincia) + P.IVA verificata alla fonte. Costo trascurabile per un test (~15-20€ per 100-150 posizioni). Soddisfa direttamente il requisito di dedup del sistema (par. 4.4).
2. **Atoka come secondo incrocio**: aggiunge il layer di rilevanza/qualità del business che Telemaco (fonte solo camerale) non ha — utile a distinguere aziende dormienti da aziende commercialmente attive.
3. **Kompass come terzo controllo indipendente**: verifica a campione la coerenza dei dati dichiarati (fatturato/dipendenti) e aziende con presenza export/B2B strutturata.

**Perché non una fonte sola**: Telemaco è autorevole ma "cieco" su segnali di mercato; Atoka aggiunge rilevanza commerciale; Kompass fa da controllo indipendente. Coerente con il documento originale (par. 11), che parla di "fonti camerali/open data" al plurale.

**Non consigliate come fonte primaria di sourcing (C1)** per copertura/affidabilità italiana debole o assenza P.IVA: Apollo.io, scraping Google Maps, Europages, LinkedIn Sales Navigator. Restano utili più avanti nel flusso: Apollo.io e Sales Navigator per **C2 (trovare il contatto/decisore raggiungibile)** una volta identificata l'azienda, non per C1.

**Da tenere presente se il sistema scala oltre il pilota**: Cribis D&B (standard enterprise, sproporzionato per 15-20 aziende) e Sistema Moda Italia/Confindustria Moda (elenco associati potenzialmente prezioso per il vertical scelto, ma richiede contatto diretto con l'associazione, non self-service).
