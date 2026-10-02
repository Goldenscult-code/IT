# Portfolio Website

Een persoonlijke portfolio website gebouwd met HTML, CSS en JavaScript.

## Functies

- Responsive design (werkt op mobiel, tablet en desktop)
- Moderne UI met hover effecten
- Navigatie met smooth scrolling
- Contact formulier
- Project overzicht op `projecten.html`
- Detailpagina per project, bereikbaar door op een projectkaart te klikken
- Kruimelpad en vorige/volgende-navigatie op de detailpagina's
- Mobile hamburger menu

## Pagina's

| Bestand | Pagina |
|---|---|
| `index.html` | Homepage: intro, over mij, projectpreview, contact |
| `projecten.html` | Overzicht van alle projecten |
| `project-google.html` | Detailpagina project 1 |
| `project-microsoft.html` | Detailpagina project 2 |
| `project-nvidia.html` | Detailpagina project 3 |

Het contactformulier staat alleen op `index.html`. De andere pagina's linken
ernaar met `index.html#contact`.

## Project Structuur

```
ITweek2/
├── index.html              # Homepage
├── projecten.html          # Projectoverzicht
├── project-google.html     # Detailpagina project 1
├── project-microsoft.html  # Detailpagina project 2
├── project-nvidia.html     # Detailpagina project 3
├── css/
│   └── styles.css          # Stijlen
├── js/
│   └── main.js             # JavaScript functionaliteit
└── assets/
    └── images/             # Afbeeldingen
        ├── profile.jpeg
        ├── project1.jpg
        ├── project2.png
        └── project3.jpg
```

De detailpagina's zijn kopieen van dezelfde sjabloon. Wil je een project
toevoegen: kopieer een bestaande detailpagina, verander de titel, het
afbeeldingsbestand, de tekst en de vorige/volgende-links, en voeg daarna een
kaart toe aan `projecten.html`.

In `SPECIFICATIE.md` staat de volledige opdrachtspecificatie.
In `CONTENT.md` staat welke tekens nog ingevuld moeten worden.

## Gebruik

1. Open `index.html` in je browser (of start de Live Server vanuit VS Code)
2. Pas de inhoud aan in de HTML-bestanden
3. Voeg je eigen afbeeldingen toe aan `assets/images/`
4. Personaliseer de kleuren in `css/styles.css` (variabelen bovenaan)

## Aanpassingen

### Kleuren wijzigen
Bewerk de CSS variabelen in `css/styles.css`:
```css
:root {
    --primary-color: #2563eb;
    --secondary-color: #1e40af;
    --text-color: #1f2937;
    --bg-color: #ffffff;
    --bg-secondary: #f3f4f6;
}
```

### Afbeeldingen vervangen
Vervang de bestanden in `assets/images/` met je eigen afbeeldingen.

## Technologieën

- HTML5
- CSS3 (Flexbox, Grid, CSS Variables)
- Vanilla JavaScript (geen frameworks, geen build-step)

## Browser Ondersteuning

- Chrome (laatste versie)
- Firefox (laatste versie)
- Safari (laatste versie)
- Edge (laatste versie)

## Licentie

Vrij te gebruiken voor persoonlijke projecten.



## leerdoelen

- leren hoe ik vibe code
- leren hoe ik websites naar git push

##  over mij

- Ik ben Jens van Ekris ik ben 16 jaar oud en mijn favotriete code is python, omdat het makkelijk en snel gaat.


