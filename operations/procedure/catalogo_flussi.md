# CATALOGO FLUSSI — TTP Agency v5.0
## Mappa completa dei flussi operativi

> L'Orchestratore consulta questo file per determinare quale procedura attivare
> in base alla richiesta di Sara. Se la richiesta non e' mappata, segue il
> Protocollo Richiesta Non Mappata (in fondo a questo file).

| # | Flusso | Trigger | File procedura |
|---|--------|---------|----------------|
| 1 | Strategia Marketing Completa | "strategia per", "piano marketing", "posizionamento", "lancio" | flusso_01_strategia_marketing.md |
| 2 | Pre-Sales (5 fasi) | "nuovo prospect", "qualificazione", "proposta per", "preventivo" | flusso_02_presales.md |
| 3 | Solo Content / Social | "piano editoriale", "contenuti per", "social per", "PED" | flusso_03_content_social.md |
| 4 | Revisione / Aggiornamento | "rivedi", "aggiorna", "modifica pricing", "refresh" | flusso_04_revisione.md |
| 5 | Business Coaching | "coaching", "sessione", "obiettivi", "crescita personale", "sblocco" | flusso_05_coaching.md |
| 6 | Audit / Quality Review | "audit", "revisione qualita'", "check deliverable" | flusso_06_audit.md |
| 7 | Formazione / Academy | "corso", "formazione", "workshop", "academy", "materiale didattico" | flusso_07_formazione.md |
| 8 | Operativo Web / Tech / Automazioni | "sito", "seo", "analytics", "automazioni", "email marketing", "funnel" | flusso_08_web_tech.md |

---

## PROTOCOLLO RICHIESTA NON MAPPATA

Quando la richiesta di Sara non rientra in nessun flusso:

1. L'Orchestratore RICONOSCE che la richiesta non ha un flusso mappato
2. L'Orchestratore PROPONE a Sara come intende procedere:
   - Quali agenti attivare e in che ordine
   - Perche' questa sequenza
   - Stima di complessita' (leggero/medio/pesante)
3. Sara DECIDE:
   a) Approva → l'Orchestratore esegue
   b) Modifica → l'Orchestratore adatta il piano
   c) "Mettilo a sistema" → l'Orchestratore esegue E crea un nuovo flusso in
      /operations/procedure/flussi_custom/flusso_[nome].md
4. Se Sara sceglie (c), il nuovo flusso diventa disponibile per richieste future
