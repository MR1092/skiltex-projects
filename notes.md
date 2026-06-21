# SKILTEX — Bæredygtige tiltag (case-noter)

Dokumentation til jobsamtale: designvalg, SEO, compliance, accessibility og præsentation.

---

## 1. Designvalg

### Farver (fra skiltex.dk)

| Token | Hex | Brug |
|-------|-----|------|
| Primær blå | `#21435f` | Hero, overskrifter, footer |
| Accent grøn | `#27a500` | CTA-knapper, links, accenter |
| Grøn hover | `#218b00` | Knap-hover |
| Brødtekst | `#656565` / `#858585` | Afsnit |
| Baggrund | `#f1f1f1` | Body og alternerende sektioner |

Grøn bruges **sparsomt** — kun til handlinger og accenter. Det undgår et “for natur-agtigt” B2C-look og holder fokus på troværdighed.

### Typografi

- **Body:** `Helvetica, Arial, sans-serif` — matcher shop-body
- **Headings/nav:** `Raleway` via Google Fonts — erstatter `futura-pt`, som SKILTEX bruger via Adobe Fonts i produktion
- **Vægt:** 700–900 på overskrifter (som FancyPop-komponenter på shoppen)

### Layout

- **Shop-chrome** (topbar, header, breadcrumb, footer) giver genkendelighed og viser, at siden er en del af webshoppen — ikke et isoleret marketing-site
- **8 indholdssektioner** med alternerende hvid/grå baggrund skaber visuel rytme og gør siden scannable
- **CSS Grid** til cards (4 kolonner → 1 på mobil) og proces (4 trin)
- **Max-width 1200px** — læsbar linjelængde og konsistent med professionel B2B-shop

### Hvorfor ikke JavaScript?

Case-krav: simpel HTML/CSS. FAQ bruger native `<details>`/`<summary>` — tilgængeligt, SEO-venligt, ingen dependencies.

---

## 2. SEO

### Meta-tags

| Tag | Værdi |
|-----|-------|
| `title` | Bæredygtige tiltag \| SKILTEX — B2B skilte og displays |
| `description` | Læs om SKILTEX' bæredygtige tiltag: genbrug, emballage, miljøbidrag og fremtidige initiativer. Gennemsigtig information til erhvervskunder. |
| `robots` | index, follow |
| `canonical` | https://www.skiltex.dk/shop/cms-baeredygtige-tiltag.html |
| `lang` | da (på `<html>`) |

### Open Graph og Twitter

- `og:type=website`, `og:locale=da_DK`
- `twitter:card=summary_large_image`
- I produktion: tilføj `og:image` med relevant hero-billede

### Heading-struktur

- **Én H1:** “Vores bæredygtige tiltag”
- **H2** pr. sektion, **H3** i cards og proces
- Logisk hierarki uden spring

### Intern linking

Links til eksisterende shop-sider:

- `/shop/cms-miljoebidrag.html`
- `/shop/cms-Levering.html`
- Produktkategorier (roll-up, ECO-infostander)
- Kontakt, handelsbetingelser

### Schema.org (JSON-LD)

1. **Organization** — firma, CVR, adresse, kontakt
2. **WebPage** — sideinfo, `isPartOf` WebSite
3. **FAQPage** — 4 spørgsmål/svar til rich results og GEO

### Søgeord (naturligt integreret)

bæredygtige tiltag, B2B webshop, emballage, genbrug, miljøbidrag, SKILTEX, erhvervskunder, ESG

---

## 3. GEO (Generative Engine Optimization)

Principper anvendt i indholdet:

- **Korte, faktuelle afsnit** (2–4 sætninger) — let at citere for AI-søgemaskiner
- **FAQ med konkrete Q&A** — struktureret data + læsbart indhold
- **Tydelige definitioner** — fx hvad miljøbidrag på 19 kr. dækker
- **Ingen vage claims** — undgå “100% grøn” eller “klimaneutral” uden dokumentation
- **Formuleringer alignet med** [eksisterende miljøbidrag-side](https://www.skiltex.dk/shop/cms-miljoebidrag.html)

---

## 4. Accessibility (WCAG 2.1 AA-mål)

| Krav | Implementering |
|------|----------------|
| Landmarks | `header`, `nav`, `main`, `footer` |
| Skip-link | “Spring til indhold” → `#main` |
| Heading-hierarki | Én H1, logisk H2→H3 |
| Fokus | `:focus-visible` med grøn outline |
| Kontrast | Hvid på `#21435f`; grøn CTA med hvid tekst |
| Billeder/ikoner | Dekorative ikoner: `aria-hidden="true"` |
| FAQ | `<details>` — keyboard-tilgængeligt |
| Links | Forståelig linktekst (“Læs om miljøbidrag”) |
| Breadcrumb | `aria-label="Brødkrumme"`, `aria-current="page"` |

**Næste skridt i produktion:** Kør Lighthouse/aXe audit; verificér kontrast med WebAIM Contrast Checker.

---

## 5. EU / B2B e-commerce compliance

### GDPR

- Ingen kontaktformular i casen (kræver backend + privacy policy)
- I produktion: cookie consent (DanDomain `DDCookiePolicy`) før tracking/analytics
- Kontakt via mail/tel — ingen persondata indsamlet på siden selv

### B2B-data

- Footer og CTA nævner: faktura, EAN, CVR/VAT ved erhvervskonto
- “Priser vises ekskl. moms” i topbar — standard for B2B

### Moms og fakturering

- Miljøbidrag angivet “ekskl. moms” (som på shoppen)
- Faktura/EAN som betalingsmetode i footer

### Green claims (vigtigt)

- **Undgå** uunderbyggede superlativer
- **Brug** formuleringer fra SKILTEX’ egen miljøbidrag-side
- “CO₂-neutral webshop” i footer — SKILTEX bruger dette allerede; i produktion bør der være dokumentation/link

### Geo-blocking / multi-market

- Links til .dk, .se, .no, .de — separate shops med lokale vilkår
- FAQ nævner, at tiltag kan variere pr. marked

### DSA (Digital Services Act)

- **Ikke relevant** — SKILTEX er ikke en marketplace med tredjepartssælgere

---

## 6. Næste skridt i produktion

Hvis siden skulle implementeres i den rigtige webshop:

1. **CMS-integration** — indlæg i DanDomain som CMS-side under `/shop/cms-baeredygtige-tiltag.html`
2. **Shop-chrome** — arve header/footer fra shop-template (ikke duplikere)
3. **Fonts** — `futura-pt` via Adobe Fonts som på shoppen
4. **Billeder** — rigtige produktbilleder med beskrivende `alt`-tekster
5. **og:image** — hero-billede til sociale medier
6. **Analytics** — Google Tag Manager med cookie consent
7. **A/B-test** — CTA-tekst og placering
8. **Løbende opdatering** — “Sidst opdateret”-dato ved ændringer

---

## 7. Præsentation til jobsamtalen

### Hvorfor layoutet?

- Shop-chrome skaber **genkendelighed** — kunden føler sig stadig i webshoppen
- **Cards** tillader parallel scanning — B2B-kunder finder hurtigt det relevante område
- **Processektion** forklarer “hvordan” — ikke kun “hvad”
- **FAQ** reducerer support-henvendelser og styrker SEO/GEO

### Brugeroplevelse (UX)

- Hero med klar H1 + CTA tilbage til shop — **ingen dead-end**
- Information hierarkisk: hvorfor → hvad → hvordan → troværdighed → FAQ → handling
- B2B-tone: fakta, dokumentation, ekskl. moms — ikke følelsesladet grøn marketing

### B2B-fit

- Ekskl. moms synlig fra start
- Miljøbidrag som eksisterende, gennemsigtig model
- EAN/faktura og CVR nævnt i CTA
- Links til ESG-dokumentation via kundeservice

### SEO / GEO / A11y / Compliance

- Meta, canonical, Open Graph, JSON-LD (WebPage, Organization, FAQPage)
- Faktuel tekst uden vildledende claims
- Semantisk HTML, landmarks, skip-link, focus states
- Compliance noteret — GDPR ved formular, green claims, multi-market

### Kort elevator-pitch (30 sek.)

> “Jeg har bygget en landingsside om SKILTEX’ bæredygtige tiltag som en ren HTML/CSS-løsning, der visuelt matcher webshoppen. Siden er struktureret til B2B-scanning med cards, proces og FAQ, bruger SKILTEX’ farver og typografi, og har SEO, structured data og accessibility indtænkt — uden vildledende miljøclaims.”

---

## 8. Projektstruktur

```
SKILTEX - Landingpage/
├── index.html    # Semantisk HTML + meta + JSON-LD
├── styles.css    # Design tokens + layout
└── notes.md      # Denne fil
```

Åbn `index.html` i browseren for at se resultatet.
