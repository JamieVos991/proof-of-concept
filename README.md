

# De grote Elektriseermachine met Leidse Flessen 

## Inhoudsopgave

- [De grote Elektriseermachine met Leidse Flessen](#de-grote-elektriseermachine-met-leidse-flessen)
  - [Inhoudsopgave](#inhoudsopgave)
  - [Beschrijving](#beschrijving)
    - [`prefers-color-scheme` — Dark en light mode](#prefers-color-scheme--dark-en-light-mode)

## Beschrijving
Design challenge voor Q42, met Teylers Museum als opdrachtgever. Ik ontwerpte en bouwde een nieuwe, uitgebreide detailpagina voor het topstuk “Grote Elektriseermachine met Leidse flessen”


### `prefers-color-scheme` — Dark en light mode

De UI ondersteunt automatisch het systeem thema van de gebruiker via de CSS media query `prefers-color-scheme`.

**Hoe het werkt**

Alle kleuren zijn gedefinieerd als CSS variabelen in `:root`. De dark mode is de standaard (het originele ontwerp van Q42), de light mode is een enhancement die de variabelen overschrijft:

```css
:root {
  --primaire-kleur: hsl(194, 37%, 16%); 
  --secundiary-kleur: hsl(37, 53%, 92%);  
  --action-kleur: hsl(48, 100%, 50%);   
}

@media (prefers-color-scheme: light) {
  :root {
    --primaire-kleur: hsl(37, 53%, 94%); 
    --secundiary-kleur: hsl(194, 37%, 16%);
    --action-kleur: hsl(48, 100%, 40%);  
  }
}
```

**Designkeuzes**

- De twee hoofdkleuren (donker teal en crème) zijn bewust omgewisseld in plaats van nieuwe kleuren te introduceren. Zo blijft de huisstijl van Q42 herkenbaar.
- De gele accentkleur (`--action-kleur`) wordt in light mode iets donkerder gezet (`50%` → `40%` lightness) zodat de knoptekst voldoende contrast heeft op een lichte achtergrond.
- De quiz kaart heeft in dark mode een lichte achtergrond (crème op donker), en in light mode een donkere achtergrond (teal op licht). Dat contrast werkt in beide richtingen dankzij dezelfde variabelen.
- De stippellijn van de tijdlijn en de jaar-punten zijn ook via variabelen (`--tijdlijn-lijn`, `--tijdlijn-punt`) aan het thema gekoppeld. De JS leest de huidige variabelewaarde via `getComputedStyle` en herrendert de SVG elementen bij een thema wissel.

**Fallback**

Browsers die `prefers-color-scheme` niet ondersteunen negeren de media query en krijgen gewoon de dark mode — het oorspronkelijke ontwerp. Er is geen zichtbaar verschil voor die gebruikers.