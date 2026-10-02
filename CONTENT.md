# Content invullen voor de projectenpagina

Deel van fase 0. Vul dit bestand in, dan kan ik fasen 2 t/m 5 bouwen.
Alles tussen `[ ]` moet je vervangen. Wat er al staat is de huidige tekst van `index.html`.

---

## Stap 0.1 — Eerst dit beslissen

De site noemt nu drie **stages**. Daar is één vraag over:

- [ ] Zijn die stages je projecten? → Ga door naar stap 0.2
- [ ] Nee, ik heb echte code-/schoolprojecten → zet ze hieronder, stages vervallen

> Een stage is werkervaring, geen project dat je zelf bouwde. Als je docent of een
> werkgever dit leest is het eerlijker om een stage bij je cv te tonen en hier je
> eigen projecten te zetten. Maar als je stages je vakantiewerk waren en je ze
> bewust laat zien, is "stage" ook een prima projectomschrijving. Aan jou.

---

## Stap 0.2 — Project 1

**Titel:** `[Google]`
**Periode:** `[bv. februari 2026 - augustus 2026]`
**Afbeelding:** `[project1.jpg]`
**Status:** `[in behandeling / afgerond]`

**Korte omschrijving** (max 2 regels, dit komt op de kaart):
`Stage gelopen bij Google voor een half jaar.`

**Lange omschrijving** (2-3 alinea's, komt op de detailpagina):
```
[Schrijf hier wat het project was. Denk aan: om welk probleem ging het,
wie had er last van, wat moest er gebeuren?]

[Wat heb je concreet gedaan? Welke onderdelen heb je gebouwd of verbeterd?]

[Waarom was dit-project nuttig, en wat heb je ervan geleerd?]
```

**Mijn rol** (2-4 bullets):
```
- [bijv. Frontend gebouwd voor het interne dashboard]
- [bijv. Bestaande componenten omgezet naar herbruikbare modules]
- [bijv. Samen met team X het ontwerp uitgewerkt]
```

**Resultaat** (1 alinea):
```
[Wat leverde het op? Een snellere pagina, een gesloten bug, een opgelost probleem?]
```

**Technologieën:** `[bv. HTML, CSS, JavaScript]`
**Live-demo-link:** `[bv. https://... of leeg laten]`
**Link naar code:** `[bv. https://github.com/... of leeg laten]`

---

## Stap 0.3 — Project 2

**Titel:** `[Microsoft]`
**Periode:** `[bv. maart 2026 - september 2026]`
**Afbeelding:** `[project2.png]`
**Status:** `[in behandeling / afgerond]`

**Korte omschrijving:**
`Stage bij microsoft voor een half jaar.`

**Lange omschrijving:**
```
[Zelfde opbouw als project 1]
```

**Mijn rol:**
```
- [ ]
- [ ]
```

**Resultaat:**
```
[ ]
```

**Technologieën:** `[bv. HTML, CSS, JavaScript]`
**Live-demo-link:** `[ ]`
**Link naar code:** `[ ]`

---

## Stap 0.4 — Project 3

**Titel:** `[Nvidia]`
**Periode:** `[bv. april 2026 - juni 2026]`
**Afbeelding:** `[project3.jpg]`
**Status:** `[in behandeling / afgerond]`

**Korte omschrijving:**
`Een korte stage gelopen bij Nvidia.`

**Lange omschrijving:**
```
[Zelfde opbouw als project 1]
```

**Mijn rol:**
```
- [ ]
- [ ]
```

**Resultaat:**
```
[ ]
```

**Technologieën:** `[bv. HTML, CSS, JavaScript]`
**Live-demo-link:** `[ ]`
**Link naar code:** `[ ]`

---

## Stap 0.5 — Afbeeldingen controleren

**Klik hiervoor in VS Code met de muis op het bestand, of sleep het in een browser.**

| Bestand | Maat | Mijn bevinding | Jouw oordeel |
|---|---|---|---|
| `project1.jpg` | 447x447, 71% oranje `#F48B00` | Grote vlakke oranje achtergrond | [ ] klopt / [ ] vervangen |
| `project2.png` | 447x447, **13 unieke kleuren** | Platte illustratie, geen foto | [ ] klopt / [ ] vervangen |
| `project3.jpg` | 507x394, 49% donkergeel `#6E6000` | Grote vlakke achtergrond | [ ] klopt / [ ] vervangen |

> Ik kan afbeeldingen niet bekijken, alleenpixels tellen. De opvallende punten:
> `project2.png` heeft maar 13 kleuren op 447x447 pixels - dat is een platte
> illustratie of placeholder, geen foto. En de dominante kleuren zijn nergens het
> merklogo dat je zou verwachten: Microsoft is blauw/oranje, Nvidia is groen,
> Google is blauw. Kijk dus even zelf of de afbeeldingen bij de bedrijven passen.

---

## Stap 0.6 — Technologieën

De site noemt nu: **HTML, CSS, JavaScript, React, Node.js**

Ik heb je project gecontroleerd en daar staat het volgende over:

| Technologie | Klopt het? | Bewijs |
|---|---|---|
| HTML | ja | `index.html` |
| CSS | ja | `css/styles.css`, gebruikt Grid, Flexbox, CSS-variabelen en media queries |
| JavaScript | ja | `js/main.js` |
| **React** | **nee** | komt nergens voor in de code |
| **Node.js** | **nee** | geen `package.json`, geen `node_modules`, geen build-config |

`js/main.js` is 79 regels vanilla JavaScript met DOM-calls, geen enkel `import`
of `require`. Je `README.md` zelf schrijft ook "Vanilla JavaScript".

**Voorstel:** verander de tags naar `HTML`, `CSS`, `Vanilla JavaScript`.
Voor elk project kan ik er specifieke technologieën bij zetten, bijvoorbeeld
`Figma`, `Git`, of `Python` als je dat ergens voor hebt gebruikt.

**Te bevestigen:** [ ] tags aanpassen zoals voorgesteld  /  [ ] anders, namelijk: `[ ]`

---

## Stap 0.7 — Besluit over het Word-document

`Waarom gebruiken developers een vaste projectstructuur.docx` is een geldig
Word-bestand van 391 KB en duidelijk de opdrachtbeschrijving.

**Mijn besluit: ik commit het mee.** Het is een schooldocument en als je docent
in de repository kijkt moet het er staan. Het wordt niet gebruikt door de
website zelf, dus ik zet in de README één regel waarom het erin staat.

Wil je het eruit houden? Zeg het, dan haal ik het eruit en zet ik het in
`.gitignore`.

---

## Checklist voordat ik begin

- [ ] 0.1 - besloten wat de projecten zijn
- [ ] 0.2 - project 1 volledig ingevuld
- [ ] 0.3 - project 2 volledig ingevuld
- [ ] 0.4 - project 3 volledig ingevuld
- [ ] 0.5 - afbeeldingen gecontroleerd
- [ ] 0.6 - technologieën bevestigd
- [ ] 0.7 - besluit over het Word-bestand