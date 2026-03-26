# BRAMO — Piano Tecnico di Implementazione
**Agente:** Web Tech | **Data:** 2026-03-26
**Progetto:** Brand Strategy — Funnel & Tech Stack

---

## 1. TECH STACK CONSIGLIATO

### Piattaforma ecommerce
**Shopify Basic (€32/mese)** — sufficiente per il lancio.
- Upgrade a Shopify (€92/mese) solo se servono report avanzati o + staff account.
- Dominio: registrare `bramo.it` su Namecheap o Shopify (~€15/anno).

### Abbonamenti
**Seal Subscriptions (gratuito fino a 150 abbonati, poi €7,95/mese)**
- Alternativa entry-level a Recharge (€99/mese) — non giustificabile al lancio.
- Copre: frequenza variabile, pausa, skip, cancellazione self-service.
- Se il volume supera 500 abbonati attivi: valutare migrazione a Recharge o Bold.

### Email Marketing
**Klaviyo (gratuito fino a 500 contatti / 5.000 email/mese)**
- Integrazione nativa con Shopify + Seal Subscriptions.
- Alternativa low-cost: Omnisend (gratuito fino a 500 email/mese) — meno potente sui flow abbonamenti.
- Raccomandazione: Klaviyo dalla partenza per evitare migrazioni costose.

### Analytics
- **GA4** — gratuito, obbligatorio.
- **Meta Pixel** — gratuito, obbligatorio per advertising.
- **TikTok Pixel** — gratuito, consigliato dal giorno 1.
- **Hotjar** (piano gratuito) — heatmap + session recording per ottimizzare la landing.

### Pagamenti (Italia)
- **Stripe** — commissione 1,5% + €0,25 per transazione (carte EU). Setup rapido.
- **PayPal** — commissione ~3,4% + €0,35. Aggiungere per fiducia del consumatore italiano.
- **Scalapay** (Buy Now Pay Later) — valutare al mese 3 per aumentare conversione su AOV alti.

**Costo mensile stimato tech stack:**
| Strumento | Costo |
|-----------|-------|
| Shopify Basic | €32 |
| Seal Subscriptions | €0 (lancio) |
| Klaviyo | €0 (lancio) |
| Dominio .it | €1,25 |
| Hotjar Free | €0 |
| **Totale lancio** | **~€33/mese** |
| **Totale mese 6+** | **~€80-120/mese** |

---

## 2. ARCHITETTURA DEL SITO

### Pagine essenziali
```
/                          → Homepage (hero + value prop + CTA abbonamento)
/prodotti/                 → Catalog page
/prodotti/[nome-cibo]/     → Product page (PDP) — con configuratore abbonamento
/abbonamento/              → Pagina dedicata "Come funziona l'abbonamento"
/chi-siamo/                → Brand story BRAMO
/blog/                     → Content hub (SEO + trust)
/faq/                      → Domande frequenti (abbonamento, spedizione, resi)
/contatti/                 → Form + email
/account/                  → Portal abbonato (Seal Subscriptions widget)
/checkout/                 → Shopify native
/pages/privacy-policy/     → Obbligatorio GDPR
/pages/termini-condizioni/ → Obbligatorio
```

### Flusso UX abbonamento (PDP → Checkout)
1. PDP: seleziona prodotto → toggle "Acquisto singolo / Abbonamento"
2. Abbonamento selezionato: dropdown frequenza (ogni 2/4/6/8 settimane)
3. Sconto abbonamento visibile (es. "Risparmia 15%")
4. Add to cart → checkout standard Shopify
5. Post-acquisto: email di conferma + accesso portale abbonato

---

## 3. FLUSSI EMAIL AUTOMATION (KLAVIYO)

### Flow 1 — Welcome Series (trigger: primo acquisto o iscrizione newsletter)
- **Email 1** (immediata): Benvenuto in BRAMO — storia del brand, cosa aspettarsi
- **Email 2** (+2 giorni): "Perché il cibo premium fa la differenza" — content educativo
- **Email 3** (+5 giorni): Guida alla transizione alimentare del cane
- **Email 4** (+10 giorni): Invito a lasciare recensione + sconto 10% prossimo ordine

### Flow 2 — Abandoned Cart (trigger: carrello abbandonato dopo 1h senza acquisto)
- **Email 1** (+1h): Reminder gentile — "Hai dimenticato qualcosa?"
- **Email 2** (+24h): Benefici chiave BRAMO + social proof (recensioni)
- **Email 3** (+72h): Sconto 5% con scadenza 48h (solo se non convertito)

### Flow 3 — Subscription Reminder (trigger: 3 giorni prima di ogni rinnovo abbonamento)
- **Email unica**: "Il tuo prossimo ordine BRAMO è in arrivo" + riepilogo ordine
- Link diretto a portale per modificare/saltare ordine

### Flow 4 — Re-engagement (trigger: nessun acquisto negli ultimi 90 giorni)
- **Email 1**: "Ci manchi" — tone empatico, cosa è cambiato/migliorato
- **Email 2** (+7 giorni): Offerta di riattivazione (sconto o regalo)
- **Email 3** (+14 giorni): Ultima chance — se no risposta, spostare in lista inattivi

### Flow 5 — Review Request (trigger: 7 giorni dopo consegna stimata)
- **Email unica**: "Come sta andando?" — link a pagina recensione (Trustpilot o Google)
- Variante per abbonati: chiedere anche NPS (scala 1-10)

### Flow 6 — Subscription Winback (trigger: cancellazione abbonamento)
- **Email 1** (+1 giorno): "Ci dispiace — possiamo fare qualcosa?" + survey motivazione
- **Email 2** (+7 giorni): Offerta personalizzata in base a risposta survey
- **Email 3** (+30 giorni): "Quando sei pronto, siamo qui" — no pressione

---

## 4. GESTIONE ABBONAMENTI (SEAL SUBSCRIPTIONS)

### Opzioni di frequenza
- Ogni 2 settimane
- Ogni 4 settimane (default consigliato)
- Ogni 6 settimane
- Ogni 8 settimane

### Portale abbonato (self-service)
Accessibile da `/account/` — il cliente può:
- **Saltare** il prossimo ordine (skip) — max 1 volta consecutiva
- **Posticipare** la data del prossimo ordine
- **Mettere in pausa** (fino a 60 giorni) — riduce churn vs cancellazione
- **Cancellare** — con survey exit obbligatoria (3 domande max)
- **Cambiare prodotto** o quantità
- **Aggiornare** indirizzo di consegna e metodo di pagamento

### Sconti abbonamento
- 15% su tutti gli abbonamenti (da testare vs 10% nei primi mesi)
- Sconto visibile sia in PDP che in carrello — mai nascosto

### Gifting (fase 2 — mese 3)
- Funzione "Regala abbonamento" — 1, 3 o 6 mesi prepagati
- Richiede app aggiuntiva (Gift Subscriptions by Recharge ~€0 base) o sviluppo custom

---

## 5. ANALYTICS & TRACKING

### GA4 Setup
Eventi obbligatori da configurare:
- `purchase` — con revenue, items, coupon
- `add_to_cart`
- `begin_checkout`
- `subscription_start` (evento custom)
- `subscription_cancel` (evento custom)
- `view_item` (PDP view)

Conversioni da marcare in GA4:
- `purchase`, `subscription_start`, `lead` (iscrizione newsletter)

### Meta Pixel
- Installare via Shopify App (Meta — Facebook & Instagram)
- Evento chiave: `Purchase`, `AddToCart`, `InitiateCheckout`, `Lead`
- Attivare Conversions API (CAPI) per bypassare ad blocker — disponibile nativamente in Shopify

### TikTok Pixel
- App ufficiale TikTok su Shopify App Store (gratuita)
- Stessi eventi standard: `Purchase`, `AddToCart`, `PlaceAnOrder`

### UTM Structure
```
utm_source=    meta / tiktok / google / newsletter / influencer
utm_medium=    paid_social / email / organic / referral
utm_campaign=  [nome_campagna] (es: lancio_q1_2026)
utm_content=   [variante_creativa] (es: video_cane_labrador)
utm_term=      [parola_chiave] (solo Google)
```
Convenzione naming: tutto minuscolo, underscore al posto di spazi.

---

## 6. MAPPA INTEGRAZIONI

```
SHOPIFY (hub centrale)
    │
    ├── Seal Subscriptions
    │       └── eventi abbonamento → Klaviyo (webhook)
    │
    ├── Klaviyo
    │       ├── segmenti abbonati / one-time / inattivi
    │       └── flow automatici (vedere sezione 3)
    │
    ├── Meta Pixel + CAPI
    │       └── audience personalizzate per retargeting
    │
    ├── TikTok Pixel
    │       └── eventi acquisto per ottimizzazione campagne
    │
    ├── GA4
    │       └── report performance + attribution
    │
    └── Stripe / PayPal
            └── gestione pagamenti + rimborsi

Flusso dati abbonamento:
Seal → webhook → Klaviyo (tag "abbonato_attivo") → flow email dedicati
Seal → Shopify orders → GA4 (evento subscription_start)
```

---

## 7. LAUNCH CHECKLIST TECNICA

### Pre-lancio (2 settimane prima)
- [ ] Dominio `bramo.it` acquistato e puntato a Shopify
- [ ] SSL attivo (automatico Shopify)
- [ ] Seal Subscriptions installato e testato con ordine reale
- [ ] Klaviyo connesso a Shopify — lista principale sincronizzata
- [ ] Tutti i flow Klaviyo in modalità LIVE (non draft)
- [ ] Meta Pixel attivo + evento Purchase verificato con Pixel Helper
- [ ] TikTok Pixel attivo + verificato
- [ ] GA4 property creata + connessa + conversioni configurate
- [ ] Stripe + PayPal testati con pagamenti reali (poi rimborsati)
- [ ] GDPR: banner cookie (app gratuita: Cookiebot o CookieYes)
- [ ] Privacy Policy + T&C aggiornati con info abbonamento
- [ ] Pagina FAQ pubblicata con sezione abbonamento
- [ ] Portale abbonato testato: skip, pausa, cancellazione funzionanti
- [ ] Email transazionali Shopify personalizzate (conferma ordine, spedizione)
- [ ] Test mobile completo su iOS e Android
- [ ] Velocità pagina: Lighthouse score > 70 (immagini ottimizzate, lazy load)

### Lancio
- [ ] Rimuovere password Shopify store
- [ ] Annuncio social + email lista waitlist
- [ ] Monitoraggio real-time su GA4 + Shopify dashboard

### Post-lancio (settimana 1)
- [ ] Verificare tutti i flow Klaviyo attivati correttamente
- [ ] Controllare tasso conversione abbonamento vs one-time
- [ ] Prima sessione Hotjar review (heatmap homepage + PDP)

---

## 8. COSTI MENSILI STIMATI

| Voce | Lancio (mese 1-3) | Crescita (mese 4-6) | Scale (mese 7+) |
|------|-------------------|---------------------|-----------------|
| Shopify Basic | €32 | €32 | €92 (upgrade) |
| Seal Subscriptions | €0 | €7,95 | €7,95 |
| Klaviyo | €0 | €20 (1k contatti) | €60 (5k contatti) |
| Dominio .it | €1,25 | €1,25 | €1,25 |
| Hotjar | €0 | €0 | €32 (plan Plus) |
| CookieYes (GDPR) | €0 | €0 | €0 |
| **TOTALE** | **~€33** | **~€61** | **~€193** |

Note: non inclusi costi pubblicitari (budget separato) né commissioni Stripe/PayPal (variabili su transato).

---

*Documento generato da Web Tech — TTP AI Agency*
*Prossimo step: validare tech stack con Sara, poi procedere con setup Shopify.*
