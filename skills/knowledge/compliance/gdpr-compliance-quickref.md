---
framework: GDPR Compliance Checklist (Marketing-Oriented)
author: Regolamento (UE) 2016/679 del Parlamento Europeo e del Consiglio, 27 aprile 2016 (GDPR) — testo di legge, non opera di un singolo autore. Guidance applicativa: Garante per la Protezione dei Dati Personali (Italia).
type: quickref
category: compliance
status: active
---
# GDPR COMPLIANCE — Quick Reference (Marketing)
## Source: Regolamento (UE) 2016/679, in vigore dal 25 maggio 2018. Riferimenti puntuali: Art. 5 (principi), Art. 6 (basi giuridiche), Art. 7 (condizioni per il consenso), Art. 13-14 (informativa), Art. 15-22 (diritti dell'interessato), Art. 28 (responsabili del trattamento), Art. 33 (notifica violazioni). Integrazione: Direttiva ePrivacy 2002/58/CE per cookie ed email marketing.
## When to use: Prima di pubblicare un funnel, form, campagna email, sito o automazione che raccoglie dati personali. **Sessione tipica PMI: 1-2h per un audit di un singolo funnel/sito.**

## WHEN NOT TO USE
- Contrattualistica commerciale non legata a dati personali → giudizio legale generico, non questo framework
- Questioni di diritto del lavoro su dati dei dipendenti → area specialistica diversa (non copertura marketing)
- Aziende che operano esclusivamente fuori UE senza clienti/utenti europei → regime diverso, non applicabile
- Dispute legali reali o minacciate → non è un tool di audit, serve consulenza legale diretta

## CORE THESIS
Il GDPR per il marketing si riduce quasi sempre a una domanda sola per ogni dato raccolto: **"su quale delle 6 basi giuridiche dell'Art. 6 stiamo raccogliendo questo dato, e l'abbiamo dichiarato all'utente?"** Se la risposta non è immediata, c'è un problema di compliance — a prescindere da quanto sia "innocuo" il dato.

## LE 6 BASI GIURIDICHE (Art. 6) — quali usa davvero il marketing
| Base | Uso tipico marketing | Nota |
|---|---|---|
| Consenso | Newsletter, cookie non tecnici, retargeting | Deve essere libero, specifico, informato, revocabile — un banner con solo "OK" non basta |
| Contratto | Dati per evadere un ordine/servizio richiesto | Non serve consenso separato per questo |
| Legittimo interesse | Email marketing B2B a clienti esistenti (con opt-out) | Va documentato un bilanciamento interesse-vs-diritti, non è automatico |
| Obbligo legale | Fatturazione, conservazione fiscale | Non serve consenso |
| Interesse vitale / pubblico | Quasi mai rilevante per marketing PMI | — |

## CHECKLIST OPERATIVA (Art. 5, 13-14, 28)
1. **Minimizzazione**: si raccoglie solo il dato necessario allo scopo dichiarato? (Art. 5.1.c)
2. **Informativa presente e chiara**: privacy policy raggiungibile, linguaggio non legalese, finalità elencate una per una (Art. 13)
3. **Consenso granulare**: se ci sono più finalità (newsletter + retargeting + terze parti), consensi separati, non un unico blocco (Art. 7)
4. **Cookie non tecnici bloccati finché non c'è consenso**: banner opt-in reale, non solo informativo (ePrivacy + linee guida Garante)
5. **Diritti dell'interessato attivabili**: accesso, cancellazione, portabilità raggiungibili con un contatto reale, non solo teorici (Art. 15-22)
6. **Fornitori terzi (ESP, CRM, ad platform) coperti da DPA**: Data Processing Agreement firmato con ogni fornitore che tratta dati per conto del titolare (Art. 28)
7. **Piano di notifica violazioni**: chi avvisa il Garante entro 72h se c'è una fuga dati (Art. 33) — anche solo un referente designato è un inizio

## GUIDING QUESTIONS (da fare al titolare della PMI)
- "Se un cliente chiede di cancellare i suoi dati oggi, sapete esattamente cosa cancellare e dove si trova?"
- "Il vostro tool di email marketing ha firmato un DPA con voi, o non ve lo siete mai chiesti?"
- "Il banner cookie blocca davvero gli script di tracking finché non c'è consenso, o li carica comunque?"

## EXPECTED OUTPUT
1. Checklist compilata (7 punti sopra) con stato: conforme / non conforme / da verificare
2. Per ogni "non conforme": rischio (basso/medio/alto) + azione correttiva concreta
3. Nota esplicita se serve una verifica da un legale qualificato (casi contrattuali, dispute, interpretazioni non standard)

## ERRORI COMUNI NELLE PMI
- Cookie banner solo "informativo" (nessun vero blocco degli script prima del consenso) — la violazione più frequente in assoluto
- Un solo consenso onnicomprensivo per newsletter + retargeting + condivisione con terzi, invece di consensi separati
- Nessun DPA firmato con i fornitori (email marketing, CRM, ads) — spesso ignorato perché "sono strumenti standard"
- Informativa privacy copiata da un altro sito senza adattarla alle finalità reali del proprio trattamento

## QUICK EXAMPLE (PMI italiana — e-commerce artigianale, Toscana, 6 dipendenti)
**Decisione**: possiamo lanciare la campagna di retargeting su Meta Ads collegata al sito?

Audit: sito ha cookie banner ma gli script Meta partono al caricamento pagina, prima di qualsiasi click (**non conforme**, rischio alto — violazione diretta ePrivacy). Newsletter e retargeting condividono lo stesso checkbox di consenso (**non conforme**, rischio medio — Art. 7 richiede granularità). Nessun DPA con l'ESP usato per la newsletter (**da verificare**, rischio medio).

**Azione correttiva**: consent management platform che blocca gli script Meta fino al click "Accetta"; split del consenso in 2 checkbox separati; richiesta DPA firmato all'ESP prima del prossimo invio.

**GO/NO-GO**: campagna in pausa fino a fix del blocco script (rischio alto, non negoziabile); newsletter può proseguire nel frattempo con il consenso attuale ma va corretta entro 30 giorni.

## CROSS-REFERENCE
- `navigating-regulations` (Global Skills Arsenal) — per questioni di licensing/giurisdizione oltre il GDPR
- `legal/SKILL.md` — agente TTP che applica questa checklist sui deliverable dei clienti
- `web_tech/SKILL.md` — implementa tecnicamente consent management e blocco script
- `voice/SKILL.md` — scrive il testo dell'informativa privacy in linguaggio chiaro
