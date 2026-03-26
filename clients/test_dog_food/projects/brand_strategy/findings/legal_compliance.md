# BRAMO — Checklist Compliance Legale
*Agente: Legal | Data: 2026-03-26 | Stato: BOZZA — richiede revisione avvocato*

> AVVISO: Questo documento ha scopo informativo e non sostituisce consulenza legale professionale. Prima del lancio, far revisionare da un avvocato specializzato in diritto digitale italiano.

---

## AREE DI RISCHIO ELEVATO

- **[RISCHIO ALTO]** Pixel Meta/TikTok senza consenso preventivo = sanzione GDPR fino a €20M o 4% fatturato
- **[RISCHIO ALTO]** Abbonamento con rinnovo automatico senza disclosure esplicita = pratica commerciale scorretta (D.Lgs. 206/2005)
- **[RISCHIO ALTO]** Recesso abbonamento: diritto di recesso entro 14 gg ma con eccezioni per prodotti deperibili — gestire con attenzione
- **[RISCHIO MEDIO]** Claim salutistici su cibo per animali: normativa EU 767/2009 limita ciò che si può affermare

---

## 1. GDPR — Privacy & Consenso

### Documenti obbligatori
- [ ] **Privacy Policy** — redatta in italiano, conforme GDPR art. 13. Deve includere: titolare del trattamento (ragione sociale, P.IVA, indirizzo), finalità e basi giuridiche per ogni trattamento, categorie di dati raccolti, trasferimenti extra-UE (Shopify/Klaviyo/Meta sono USA), tempi di conservazione, diritti dell'interessato, DPO se applicabile
- [ ] **Cookie Policy** — documento separato o sezione dedicata nella Privacy Policy. Elenco analitico di ogni cookie con: nome, finalità, durata, gestore
- [ ] **Informativa al checkout** — versione sintetica della privacy policy, obbligatoria prima dell'acquisto
- [ ] **DPA (Data Processing Agreement)** — accordi firmati con tutti i processor: Shopify, Klaviyo, Meta, TikTok. Verificare che abbiano SCCs aggiornate post-Schrems II

### Basi giuridiche per ogni trattamento
| Trattamento | Base giuridica |
|---|---|
| Gestione ordini e abbonamento | Esecuzione contratto (art. 6.1.b) |
| Email marketing a clienti | Legittimo interesse OPPURE consenso (preferire consenso) |
| Email marketing a prospect | Consenso esplicito obbligatorio |
| Analytics (GA4 anonimizzato) | Legittimo interesse (con opt-out) |
| Pixel Meta/TikTok per remarketing | Consenso esplicito obbligatorio |
| Profilazione per personalizzazione | Consenso esplicito obbligatorio |

### DPIA (Valutazione d'Impatto)
- [ ] Valutare se necessaria: obbligatoria per trattamenti ad alto rischio. Con pixel di terze parti + profilazione comportamentale + abbonamento ricorrente, **è fortemente consigliata**. Consultare Garante Privacy italiano per linee guida settoriali.

---

## 2. Requisiti E-commerce Italia (D.Lgs. 70/2003 + D.Lgs. 206/2005)

### Informazioni obbligatorie sul sito (visibili senza navigazione)
- [ ] **Ragione sociale** completa dell'azienda
- [ ] **Partita IVA** (P.IVA)
- [ ] **Indirizzo della sede legale** (non PO Box)
- [ ] **Indirizzo email** di contatto operativo
- [ ] **Numero di telefono** (obbligatorio per ecommerce dal 2022 — verifica applicabilità)
- [ ] **REA / Registro Imprese** — numero iscrizione Camera di Commercio
- [ ] **Capitale sociale** se S.r.l. o S.p.A.

### Termini e Condizioni di Vendita
- [ ] Redatti in italiano, chiari e non ambigui
- [ ] Devono includere: descrizione prodotti e abbonamento, prezzi IVA inclusa, modalità di pagamento, consegna (tempi e costi), politica resi, diritto di recesso, foro competente (può essere tribunale del consumatore), legge applicabile (italiana)
- [ ] **Approvazione specifica** (doppio click/checkbox separata) per clausole onerose ex art. 1341-1342 c.c.: limitazioni di responsabilità, foro competente, rinnovo automatico
- [ ] T&C devono essere accettate prima del completamento ordine — flag obbligatorio, non pre-spuntato

### Prezzi e IVA
- [ ] Tutti i prezzi mostrati con IVA inclusa (22% su pet food, verificare aliquota ridotta applicabile)
- [ ] Costi di spedizione indicati prima del checkout
- [ ] Nessun costo nascosto aggiunto in fase finale

---

## 3. Cookie & Tracking Compliance

### Cookie Banner — Requisiti Garante Privacy (Provvedimento 2021)
- [ ] Banner visibile al primo accesso, **prima** di qualsiasi cookie non tecnico
- [ ] **Nessun cookie di marketing depositato** prima del consenso — questo include Meta Pixel e TikTok Pixel
- [ ] Rifiuto deve essere facile quanto accettazione (stesso numero di click)
- [ ] Preferenze salvabili e modificabili in qualsiasi momento (link nel footer)
- [ ] Consenso granulare per categoria

### Categorie Cookie e Consenso
| Categoria | Consenso richiesto | Esempi BRAMO |
|---|---|---|
| Tecnici/necessari | NO | Shopify cart, sessione, sicurezza |
| Analitici aggregati anonimi | NO (ma informare) | GA4 con IP anonimizzato |
| Analitici non anonimi | SI — opt-in | GA4 senza anonimizzazione |
| Marketing/profilazione | SI — opt-in obbligatorio | Meta Pixel, TikTok Pixel, Klaviyo tracking |
| Funzionali (preferenze) | SI — opt-in | Lingua, valuta memorizzata |

### Implementazione Pixel Meta & TikTok — [RISCHIO ALTO]
- [ ] Pixel attivati **solo dopo consenso esplicito** — usare modalità condizionale nel tag manager
- [ ] Implementare **Conversions API (CAPI)** lato server come alternativa/complemento — riduce dipendenza da cookie del browser
- [ ] Per Meta: utilizzare **Advanced Matching** solo su dati hashati di utenti che hanno dato consenso
- [ ] Configurare eventi pixel solo per utenti con consenso attivo
- [ ] **Strumento consigliato:** Cookiebot, Axeptio, o iubenda (hanno integrazione nativa Shopify e gestione consenso pixel)

---

## 4. Abbonamento — Obblighi Specifici

### Disclosure Rinnovo Automatico (D.Lgs. 206/2005 + Omnibus Directive recepita 2023)
- [ ] Termini di rinnovo automatico devono essere **evidenziati esplicitamente** — non nascosti nel testo
- [ ] Indicare chiaramente: frequenza di addebito, importo, data prossimo rinnovo
- [ ] **Reminder pre-rinnovo** via email obbligatorio (prassi raccomandata, in alcuni contesti obbligatorio) — minimo 7 giorni prima per abbonamenti annuali
- [ ] Conferma abbonamento via email immediata con tutti i dettagli

### Diritto di Recesso (14 giorni) — [AREA CRITICA]
- [ ] Abbonamento con primo box = contratto di vendita a distanza: diritto di recesso 14 gg dalla prima consegna
- [ ] **Eccezione prodotti deperibili:** cibo per cani è deperibile — il recesso può essere escluso per prodotti già consegnati se deperibili (art. 59 lett. d D.Lgs. 206/2005)
- [ ] **Raccomandazione:** Far valutare da avvocato se escludere recesso su prodotti già consegnati oppure offrirlo comunque come plus commerciale
- [ ] Modulo di recesso standard deve essere allegato ai T&C e all'email di conferma
- [ ] Processo di cancellazione abbonamento deve essere **semplice quanto l'attivazione** — no dark pattern

### Cancellazione Abbonamento
- [ ] Utente deve poter cancellare senza contattare assistenza (self-service obbligatorio o fortemente raccomandato post-Omnibus)
- [ ] Cancellazione confermata via email con data effettiva di termine
- [ ] No addebiti dopo la data di cancellazione comunicata

### Variazioni di Prezzo
- [ ] Variazioni prezzo abbonamento: comunicare con **preavviso adeguato** (minimo 30 giorni raccomandati)
- [ ] Utente deve poter disdire senza penali se non accetta il nuovo prezzo
- [ ] Comunicazione via email (non solo notifica in-app/sito)

---

## 5. Pet Food — Normativa Specifica

### Regolamento EU 767/2009 (alimenti per animali domestici)
- [ ] **Etichetta prodotto** (anche digitale sul sito) deve includere obbligatoriamente: denominazione del prodotto, specie animale di destinazione, peso netto, termine minimo di conservazione, numero di lotto, nome e indirizzo del responsabile (produttore o importatore), lista ingredienti in ordine decrescente di peso, composizione analitica (proteine, grassi, fibre, umidità, ceneri grezze)
- [ ] **Additivi:** se presenti, devono essere dichiarati con nome e numero E
- [ ] **Numero di autorizzazione** dello stabilimento di produzione (se applicabile)

### Claim e Comunicazione Marketing — [RISCHIO MEDIO]
- [ ] **Vietati claim salutistici non autorizzati** — es. "migliora la salute delle articolazioni", "previene malattie" richiedono evidenza scientifica e autorizzazione
- [ ] **Ammessi claim descrittivi:** "alta percentuale di carne", "senza cereali", "ricco di Omega-3" (se verificabile)
- [ ] **Vietato:** qualsiasi claim che implichi effetti terapeutici o preventivi su malattie animali (competenza veterinaria)
- [ ] **Natural/Naturale:** termine non regolamentato in pet food, ma uso ingannevole può essere contestato da AGCM (Autorità Garante della Concorrenza e del Mercato)
- [ ] Verificare con produttore/fornitore che i claim promozionali siano supportati dalla composizione reale del prodotto

### Sicurezza Alimentare Animali
- [ ] Produttore deve essere registrato presso ASL competente (reg. CE 183/2005)
- [ ] Tracciabilità ingredienti garantita dal fornitore — richiedere documentazione

---

## 6. Checklist Prioritaria Pre-Launch

### PRIORITA' 1 — Blockers assoluti (senza questi non si può aprire)
- [ ] Redazione Privacy Policy completa (avvocato)
- [ ] Redazione Termini e Condizioni di Vendita (avvocato)
- [ ] Implementazione cookie banner conforme Garante (es. Axeptio/Cookiebot su Shopify)
- [ ] Pixel Meta e TikTok condizionati al consenso cookie — ZERO pixel prima del consenso
- [ ] DPA firmati con Shopify, Klaviyo, Meta, TikTok
- [ ] Disclosure rinnovo automatico nel checkout (testo esplicito + checkbox separata)
- [ ] P.IVA, sede legale, email e dati aziendali visibili nel footer del sito

### PRIORITA' 2 — Obbligatori entro 30 giorni dal lancio
- [ ] DPIA (Valutazione d'Impatto) — valutare con avvocato se obbligatoria
- [ ] Modulo recesso allegato a T&C e email di conferma
- [ ] Processo self-service di cancellazione abbonamento
- [ ] Email reminder pre-rinnovo automatizzata (Klaviyo)
- [ ] Verifica etichette prodotto conformi Reg. EU 767/2009
- [ ] Revisione claim marketing con consulente pet food o avvocato specializzato

### PRIORITA' 3 — Best practice entro 60 giorni
- [ ] Implementare Conversions API (CAPI) Meta lato server
- [ ] Audit completo cookie con strumento automatico (Cookiebot scanner)
- [ ] Registro dei trattamenti (art. 30 GDPR) — obbligatorio per aziende con trattamenti sistematici
- [ ] Procedura interna per gestione richieste degli interessati (accesso, cancellazione, portabilità dati) — risposta entro 30 gg
- [ ] Procedura data breach — notifica Garante entro 72h se violazione dati personali

---

## Risorse e Riferimenti

- **Garante Privacy Italiano:** garanteprivacy.it — Provvedimento cookie 2021, FAQ GDPR
- **AGCM:** agcm.it — Pratiche commerciali scorrette, abbonamenti
- **Normativa pet food:** EUR-Lex Reg. 767/2009
- **Shopify GDPR resources:** shopify.com/legal/gdpr
- **Strumenti cookie management per Shopify:** Axeptio, Cookiebot, iubenda

---

*File: `clients/test_dog_food/projects/brand_strategy/findings/legal_compliance.md`*
*Agente: Legal — Digital Law & Compliance Specialist*
*Nota: Documento da revisionare con avvocato specializzato prima del lancio*
