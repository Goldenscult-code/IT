# Specificatie: Projectenpagina

Status: ter goedkeuring — er is nog niets geimplementeerd
Datum: 2026-10-02
Project: ITweek2 portfolio (statische HTML/CSS/JS-site)

---

## 1. Doel

Bezoekers moeten op de portfoliowebsite kunnen zien **wat de laatste projecten van Jens waren**, met een duidelijke korte omschrijving, en daar **op kunnen klikken voor meer informatie**.

Wanneer dit af is moet een bezoeker:

1. Binnen enkele seconden zien welke projecten er zijn, welke het nieuwste zijn en waar ze over gingen.
2. Met één klik op een project alle details van dat ene project kunnen lezen.
3. Vanaf een detailpagina makkelijk terug kunnen naar het overzicht of naar het volgende project.

---

## 2. Vastgelegde besluiten

| Vraag | Besluit |
|---|---|
| Structuur detailpagina's | Eén eigen HTML-bestand per project |
| Homepage | `#projects` blijft staan als preview, met link naar de volledige overzichtspagina |
| Inhoud | Jens levert de teksten aan; ik bouw de structuur met invulvelden |

---

## 3. Wat er komt

Nieuwe bestanden:

```
ITweek2/
├── index.html              (bestaand, wordt aangepast)
├── projecten.html          nieuw — overzicht van alle projecten
├── project-google.html     nieuw — detailpagina project 1
├── project-microsoft.html  nieuw — detailpagina project 2
├── project-nvidia.html     nieuw — detailpagina project 3
├── css/styles.css          (bestaand, krijgt nieuwe secties)
└── js/main.js              (bestaand, krijgt uitbreidingen)
```

Bestaande bestanden die aangepast moeten worden:

| Bestand | Wijziging |
|---|---|
| `index.html` | CTA-link "Bekijk Mijn Werk" → `projecten.html`; kaart-links → detailpagina's; tekst in de preview-kaarten inkorten |
| `css/styles.css` | Nieuwe blokken voor projecten-pagina, detailpagina, tech-tags, breadcrumbs |
| `js/main.js` | Null-guards toevoegen, cross-pagina ankers, nieuwe elementen aan fade-animatie |
| `README.md` | Nieuwe bestanden en paginastructuur documenteren |

Er komt **geen** nieuwe map, geen build-step en geen dependency. Alles blijft open te openen in VS Code met Live Server.

---

## 4. Wat er op elke pagina staat

### 4.1 `projecten.html` — het overzicht

Per project één `.project-card`, **nieuwste bovenaan**:

- Afbeelding (`assets/images/`)
- Titel, bijv. "Google"
- Jaartal als badge, bijv. "2026" — hiermee is zichtbaar dat het om de laatste projecten gaat
- Korte omschrijving, maximaal 2 regels
- Tech-tags (HTML, Python, …)
- Knop **"Bekijk project"** → linkt naar de detailpagina van dat project
- De hele kaart is klikbaar, niet alleen de knop

### 4.2 `project-google.html` — detailpagina (één per project, identieke opbouw)

- **Breadcrumb**: `Home > Projecten > Google`
- Titel + jaartal
- Grote afbeelding
- **Over dit project** — 2 à 3 alinea's uitleg: wat was het, in welke context
- **Mijn rol** — wat Jens zelf deed, in 2 à 4 bullets
- **Technologieën** — dezelfde tags als op de overzichtspagina
- **Resultaat** — 1 alinea: wat heeft het opgeleverd
- **Links**: "Live demo bekijken" en "Bekijk code" (kunnen voorlopig `#` blijven, dan niet klikbaar)
- **Vorige / volgende** — navigatie langs alle projecten in volgorde
- "Terug naar alle projecten"

### 4.3 `index.html` — de preview

De bestaande `#projects`-sectie blijft, met drie aanpassingen:

- De teksten worden ingekort tot één regel, want de homepage is een samenvatting
- De "Bekijk details"-knop linkt naar de echte detailpagina i.p.v. `#`
- Onder het grid komt één knop: **"Alle projecten bekijken"** → `projecten.html`

---

## 5. Wat er in het contentmodel moet staan

Jens levert per project deze velden aan. Ik zet ze daarna in alle bestanden, zodat de tekst consistent hetzelfde is op de overzichtspagina, de detailpagina en de homepage.

| Veld | Verplicht | Toelichting |
|---|---|---|
| Titel | ja | Korte naam, bv. "Google" |
| Jaartal / periode | ja | bv. "2026" of "feb 2026 – aug 2026" |
| Afbeelding | ja | Naam van het bestand in `assets/images/` |
| Korte omschrijving | ja | 1–2 regels, voor de kaart |
| Lange omschrijving | ja | 2–3 alinea's, voor de detailpagina |
| Mijn rol | ja | 2–4 bullets |
| Resultaat | ja | 1 alinea |
| Technologieën | ja | Lijst, bv. HTML, CSS, Python, Figma |
| Live-demo-link | nee | Laat leeg als er geen is |
| Link naar code | nee | Laat leeg als er geen is |

---

## 6. Technische randvoorwaarden

Deze punten zijn geen extra's, maar dingen die de huidige code kapotmaken zodra er meerdere pagina's zijn.

### 6.1 `main.js` crasht zonder contactformulier

`js/main.js:31` doet `const contactForm = document.getElementById('contact-form')` en daarna meteen `.addEventListener`. Op een pagina zonder formulier is dat `null` en volgt een **TypeError**, waarna ook de hamburger en smooth-scroll niet meer werken.

**Oplossing:** overal een `if (contactForm) { ... }` omheen.

### 6.2 Navigatie-ankers werken niet op subpagina's

De nav-links zijn nu `href="#about"` en `href="#projects"`. Op `projecten.html` bestaan die ids niet, dus klikken doet niets. Bovendien gooit `document.querySelector('index.html#about')` niets op.

**Oplossing:** op `index.html` blijven het ankers zijn, op alle andere pagina's wordt het `index.html#about` enz. De smooth-scroll-handler wordt uitgebreid zodat cross-pagina-ankers niet meer door `querySelector` hoeven.

### 6.3 Contactformulier alleen op de homepage

Het formulier blijft alleen in `index.html`. Voorkomt dubbele `id="contact-form"` en lost 6.1 op. De nav-link "Contact" wijst daarom overal naar `index.html#contact`.

### 6.4 De fade-in-animatie

`js/main.js:72` selecteert `.project-card, .about-content`. De nieuwe pagina's hebben andere klassen, die moeten worden meegenomen anders blijven ze onzichtbaar (`opacity: 0`). Let op: elk element met een meegenomen klasse start op `opacity: 0`, dus de klasse moet kloppen of de content blijft weg.

### 6.5 Responsive

Dezelfde breakpoint als nu: `768px` (mobiel) en `1200px` (voor detailpagina's, waar de tekstkolom te breed wordt). Detailpagina's krijgen een leeslijn van maximaal ±70ch.

### 6.6 Dode links

De huidige `href="#"` links (6 knoppen + 3 socials) doen na de vorige bugfix niets meer, maar ze zijn nog steeds misleidend. Ze worden vervangen door echte links of, als er nog geen URL is, verwijderd uit de `<a>`-semantiek.

---

## 7. Volgorde van werk

Tien fasen (0 t/m 9), 68 stappen. Elke stap is één focusscheiding, zodat je na elke stap iets zichtbaars hebt en een commit kunt maken. De stap-ID's (`1.3`) zijn referentienummers voor als we het samen doorlopen.

**Regel per fase:** ga pas door als de test van de vorige stap slaagt. Elke fase eindigt met een werkende pagina.

---

### Fase 0 — Content ophalen (blokkert alles hierna)

| Stap | Actie | Resultaat |
|---|---|---|
| 0.1 | Beslissen: zijn de stages bij Google/Microsoft/Nvidia je projecten, of heb je echte codeprojecten? | Vastgelegd welke 3 projecten er komen |
| 0.2 | Contentformulier (§5) invullen voor project 1 | Tekst klaar |
| 0.3 | Contentformulier invullen voor project 2 | Tekst klaar |
| 0.4 | Contentformulier invullen voor project 3 | Tekst klaar |
| 0.5 | `project2.png` (1210 bytes) openen; klopt het beeld? Zo niet: vervangen | Afbeeldingen klaar |
| 0.6 | Tech-tags per project vaststellen — klopt React/Node.js, of is het HTML/CSS/Python? | Tags klaar |
| 0.7 | Besluiten: `.docx` wel of niet in Git | Duidelijk |

### Fase 1 — `main.js` op orde maken (moet vóór elke nieuwe pagina)

Zonder deze stap werkt de hamburger op elke nieuwe pagina niet. Zie §6.1.

| Stap | Actie | Bestand |
|---|---|---|
| 1.1 | `if (hamburger && navLinks)` om de click-handler | `js/main.js` |
| 1.2 | `if (contactForm)` om de submit-handler | `js/main.js` |
| 1.3 | Fade-animatie-selector voorbereiden (lijst uitbreidbaar maken) | `js/main.js` |
| 1.4 | Testen: hamburger, smooth-scroll en formulier werken nog op `index.html` | — |

### Fase 2 — `projecten.html` bouwen

| Stap | Actie |
|---|---|
| 2.1 | Nieuw bestand aanmaken met lege `<head>`, `<meta>` en titel |
| 2.2 | Nav toevoegen; links wijzigen naar `index.html#home` / `index.html#about` / `index.html#contact` |
| 2.3 | `<section id="projects">` met `<h2>` en korte intro |
| 2.4 | `.project-grid` openen |
| 2.5 | Project-kaart 1: afbeelding, titel, jaartal-badge, korte tekst, tech-tags, "Bekijk project" |
| 2.6 | Project-kaart 2 |
| 2.7 | Project-kaart 3 |
| 2.8 | Hele kaart klikbaar maken (`<a>` om de kaart heen, geen losse knop ernaast) |
| 2.9 | `<footer>` toevoegen |
| 2.10 | `js/main.js` koppelen in `<body>` |
| 2.11 | CSS: bestaande `.project-grid` en `.project-card` hergebruiken; `.year-badge` en `.tag-list` toevoegen |
| 2.12 | Testen: pagina laadt, 3 kaarten zichtbaar, geen JS-errors |

### Fase 3 — Detailpagina-sjabloon (`project-google.html`)

Eén pagina helemaal uitschrijven als sjabloon; fasen 4 en 5 zijn daarna kopiëren met andere tekst.

| Stap | Actie |
|---|---|
| 3.1 | Nieuw bestand: `<head>`, titel "Google — Jens van Ekris", CSS-link |
| 3.2 | Nav met links naar `index.html#…` en `projecten.html` |
| 3.3 | Breadcrumb `Home > Projecten > Google` |
| 3.4 | Project-titel + jaartal |
| 3.5 | Grote projectafbeelding |
| 3.6 | Sectie "Over dit project" — 2 à 3 alinea's |
| 3.7 | Sectie "Mijn rol" — 2 à 4 bullets |
| 3.8 | Sectie "Resultaat" — 1 alinea |
| 3.9 | Sectie "Technologieën" — tags |
| 3.10 | Sectie "Links" — live demo + code |
| 3.11 | Vorige / volgende project |
| 3.12 | Knop "Terug naar alle projecten" |
| 3.13 | `<footer>` + `js/main.js` |
| 3.14 | CSS: `.detail-*` blokken, leeslijn van ±70ch |
| 3.15 | Testen: pagina haalt 200, tekst leesbaar, geen JS-errors |

### Fase 4 — Detailpagina 2 (`project-microsoft.html`)

| Stap | Actie |
|---|---|
| 4.1 | Sjabloon kopiëren |
| 4.2 | Teksten, afbeelding, titel en jaartal vervangen |
| 4.3 | Vorige/volgende-links aanpassen (nu Google ↔ Nvidia) |
| 4.4 | Breadcrumb en `<title>` aanpassen |
| 4.5 | Testen |

### Fase 5 — Detailpagina 3 (`project-nvidia.html`)

| Stap | Actie |
|---|---|
| 5.1 | Sjabloon kopiëren |
| 5.2 | Teksten, afbeelding, titel en jaartal vervangen |
| 5.3 | Vorige/volgende-links aanpassen (nu Microsoft → terug naar overzicht) |
| 5.4 | Breadcrumb en `<title>` aanpassen |
| 5.5 | Testen |

### Fase 6 — `index.html` aanpassen

| Stap | Actie |
|---|---|
| 6.1 | "Bekijk Mijn Werk"-knop wijzigen naar `projecten.html` |
| 6.2 | Kaart 1: "Bekijk details" → `project-google.html` |
| 6.3 | Kaart 2: "Bekijk details" → `project-microsoft.html` |
| 6.4 | Kaart 3: "Bekijk details" → `project-nvidia.html` |
| 6.5 | Teksten inkorten tot één regel |
| 6.6 | Knop "Alle projecten bekijken" → `projecten.html` onder het grid |
| 6.7 | Testen: alle 4 links vanaf de homepage werken |

### Fase 7 — Cross-pagina navigatie afmaken

| Stap | Actie |
|---|---|
| 7.1 | Smooth-scroll: ankers met `index.html#…` herkennen en niet door `querySelector` sturen |
| 7.2 | Fade-animatie: nieuwe klassen (`.detail-section`, `.detail-media`) toevoegen aan de selector |
| 7.3 | Actieve nav-link markeren met `aria-current` (lastig voor screenreaders, maar correct) |
| 7.4 | Testen: van elke pagina naar elke andere pagina navigeren, console leeg |

### Fase 8 — Responsive

| Stap | Actie |
|---|---|
| 8.1 | 375px: `projecten.html` — grid 1 kolom, kaarten leesbaar |
| 8.2 | 375px: detailpagina — afbeelding en tekst stapelen |
| 8.3 | 768px: hamburger en grid |
| 8.4 | 1200px: leeslijn detailpagina, kaartinhoud niet te uitgerekt |
| 8.5 | Testen op alle 5 pagina's in beide schermrichtingen |

### Fase 9 — Opruimen en documentatie

| Stap | Actie |
|---|---|
| 9.1 | Alle resterende `href="#"` vervangen of verwijderen |
| 9.2 | `README.md`: nieuwe bestanden, paginastructuur en gebruik bijwerken |
| 9.3 | Acceptatiecriteria (§8) afvinken |
| 9.4 | Laatste commit |

---

## 7a. Samenvatting per fase

| Fase | Stappen | Commit |
|---|---|---|
| 0 — Content | 7 | — (geen code) |
| 1 — `main.js` fundament | 4 | `main.js` null-guards toevoegen |
| 2 — Overzichtspagina | 12 | `projecten.html` toevoegen` |
| 3 — Detailpagina 1 | 15 | `project-google.html` toevoegen` |
| 4 — Detailpagina 2 | 5 | `project-microsoft.html` toevoegen` |
| 5 — Detailpagina 3 | 5 | `project-nvidia.html` toevoegen` |
| 6 — Homepage | 7 | `index.html` projectlinks omzetten` |
| 7 — Navigatie | 4 | `main.js` cross-pagina ankers` |
| 8 — Responsive | 5 | `styles.css` responsive afronden` |
| 9 — Afronden | 4 | `README` bijwerken |

**Totaal: 68 stappen, 9 commits.**

---

## 8. Acceptatiecriteria

De opdracht is af als dit allemaal klopt:

- [ ] Elke projectkaart op `index.html` en `projecten.html` linkt naar een werkende detailpagina
- [ ] Er staan geen `href="#"` meer in de codebase
- [ ] Het nieuwste project staat bovenaan, met zichtbaar jaartal
- [ ] Detailpagina's tonen omschrijving, rol, technologieën en resultaat
- [ ] Vorige/volgende werkt over alle detailpagina's heen
- [ ] De hamburger werkt op élke pagina
- [ ] Smooth-scroll werkt op `index.html`, en de nav-links werken vanaf elke pagina
- [ ] Het contactformulier werkt nog steeds op `index.html`
- [ ] Geen JS-errors in de browserconsole, op geen enkele pagina
- [ ] Layout is goed op 375px (mobiel), 768px (tablet) en 1440px (desktop)
- [ ] Alle afbeeldingen laden (geen 404)
- [ ] Werk gecommit in logische stappen

---

## 9. Buiten scope

Bewust niet in deze opdracht:

- Backend, database of een echt formulier dat mails verstuurt
- Een JSON- of JS-bestand als databron (alle projecten staan als HTML in de bestanden)
- Een CMS of admin-paneel om projecten te beheren
- De bestaande `href="#"`-socials echt invullen — daarvoor zijn URL's nodig
- De `.docx` in de repository opnemen
- Het vervangen van `project2.png` (1210 bytes, vermoedelijk een lege placeholder)

---

## 10. Openstaande punten voor Jens

1. **Hoeveel projecten?** Ik ga uit van 3, gelijk aan nu. Bij meer worden er meer detailbestanden.
2. **Zijn de stages je projecten?** De huidige tekst noemt stages bij Google, Microsoft en Nvidia. Klopt dat, of zijn dat stages naast echte projecten die hier getoond moeten worden?
3. **Zijn `project1.jpg` / `project2.png` / `project3.jpg` de juiste afbeeldingen?** `project2.png` is 1210 bytes en lijkt leeg.
4. **Zijn de tech-tags kloppen?** Op de homepage staan nu React en Node.js, terwijl `js/main.js` vanilla JavaScript is.
5. **Is `Waarom gebruiken developers een vaste projectstructuur.docx` een schoolopdracht die mee moet?** Nu staat hij buiten Git.