# Export-localisatie — dekking en verificatie

## Dekking

De Markdown-export heeft een complete set van 72 sleutelteksten voor alle 26 niet-Engelse UI-lokalisaties: `pl`, `de`, `es`, `fr`, `it`, `pt`, `zh`, `ja`, `hi`, `ar`, `ru`, `id`, `ko`, `tr`, `uk`, `sv`, `no`, `da`, `fi`, `th`, `sw`, `vi`, `ms`, `nl`, `cs` en `ro`. Engels blijft de expliciete standaard-/fallbacktaal.

De titel en toelichting van de stap met lengte, bronnen en toon zijn bovendien voor alle 27 ondersteunde taalcodes ingevuld.

## Controles

- Alle taalpakketten bevatten dezelfde 72 exportvelden als het Poolse referentiepakket.
- `node --check` voor de ingesloten JavaScript slaagde.
- `git diff --check` slaagde.
- HTML-parsercontrole: geen dubbele ID's en geen onopgeloste label-/ARIA-verwijzingen.

De volledige visuele en interactieve werking is niet handmatig in een browser doorlopen.
