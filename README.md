Ontwerp en maak een data driven online concept voor een opdrachtgever

De instructies voor deze opdracht staan in: [docs/INSTRUCTIONS.md](https://github.com/fdnd-task/proof-of-concept/blob/main/docs/INSTRUCTIONS.md)

# Titel
<!-- Geef je project een titel en schrijf in één zin wat het is -->

## Inhoudsopgave

- [Titel](#titel)
  - [Inhoudsopgave](#inhoudsopgave)
  - [Beschrijving](#beschrijving)
  - [Gebruik](#gebruik)
  - [Kenmerken](#kenmerken)
    - [`prefers-color-scheme` — Dark en light mode](#prefers-color-scheme--dark-en-light-mode)
  - [Installatie](#installatie)

## Beschrijving
<!-- Bij Beschrijving staat kort beschreven wat voor project het is en wat je hebt gemaakt -->
<!-- Voeg een mooie poster visual toe 📸 -->
<!-- Voeg een link toe naar Github Pages 🌐-->

## Gebruik
<!-- Bij Gebruik staat de user story, hoe het werkt en wat je er mee kan. -->

## Kenmerken
<!-- Bij Kenmerken staat welke technieken zijn gebruikt en hoe. Wat is de HTML structuur? Wat zijn de belangrijkste dingen in CSS? Wat is er met JS gedaan en hoe? Misschien heb je iets met NodeJS gedaan, of heb je een framwork of library gebruikt? -->

### `prefers-color-scheme` — Dark en light mode

De interface ondersteunt automatisch het systeem-thema van de gebruiker via de CSS media query `prefers-color-scheme`.

**Hoe het werkt**

Alle kleuren zijn gedefinieerd als CSS-variabelen in `:root`. De dark mode is de standaard (het originele ontwerp van Q42), de light mode is een enhancement die de variabelen overschrijft:

```css
:root {
  --primaire-kleur: hsl(194, 37%, 16%);   /* donker teal → achtergrond */
  --secundiary-kleur: hsl(37, 53%, 92%);  /* crème → tekst en kaart */
  --action-kleur: hsl(48, 100%, 50%);     /* geel → accentkleur */
}

@media (prefers-color-scheme: light) {
  :root {
    --primaire-kleur: hsl(37, 53%, 94%);  /* crème → achtergrond */
    --secundiary-kleur: hsl(194, 37%, 16%); /* donker teal → tekst en kaart */
    --action-kleur: hsl(48, 100%, 40%);   /* iets donkerder geel voor contrast */
  }
}
```

**Designkeuzes**

- De twee hoofdkleuren (donker teal en crème) zijn bewust omgewisseld in plaats van nieuwe kleuren te introduceren. Zo blijft de huisstijl van Q42 herkenbaar in beide modi.
- De gele accentkleur (`--action-kleur`) wordt in light mode iets donkerder gezet (`50%` → `40%` lightness) zodat de knoptekst voldoende contrast heeft op een lichte achtergrond.
- De quiz-kaart heeft in dark mode een lichte achtergrond (crème op donker), en in light mode een donkere achtergrond (teal op licht). Dat contrast werkt in beide richtingen dankzij dezelfde variabelen.
- De stippellijn van de tijdlijn en de jaar-punten zijn ook via variabelen (`--tijdlijn-lijn`, `--tijdlijn-punt`) aan het thema gekoppeld. De JS leest de huidige variabelewaarde via `getComputedStyle` en herrendert de SVG-elementen bij een themawissel.

**Fallback**

Browsers die `prefers-color-scheme` niet ondersteunen negeren de media query en krijgen gewoon de dark mode — het oorspronkelijke ontwerp. Er is geen zichtbaar verschil voor die gebruikers.

## Installatie
<!-- Bij Instalatie staat hoe een andere developer aan jouw repo kan werken -->

