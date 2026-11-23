# Writing Style Card Creator

A browser-based, multilingual writing-style profile and prompt-card builder. The complete application is in `index.html`; there is no build step or server-side data processing required. Open the file directly in a modern browser.

## Create and export a card

1. Open `index.html` and choose a language from the language picker.
2. Work through the guided sections. Select suggested options and add your own notes where needed; the app includes role/audience, channel and tone, style dimensions, truth/boundary guidance, reusable templates and examples.
3. Review the generated card and download it as Markdown for use as an LLM instruction/style guide.

The interface includes a simplified mode, theme and text-size controls, a progress indicator, and a preview/export area. The card is generated in the browser. Avoid entering sensitive information if you do not want it retained in your browser session/storage.

## Language support

The interface contains language data for English, Polish, German, Spanish, French, Italian, Portuguese, Russian, Ukrainian, Indonesian, Korean, Turkish, Chinese, Japanese, Hindi, Arabic, Swedish, Norwegian, Danish, Finnish, Thai, Swahili, Vietnamese, Malay, Dutch, Czech and Romanian. Translation coverage varies by section: some content uses shared English fallback strings, so this list should not be read as a promise that every label and option has a complete native-language translation.

## Using the exported Markdown

Treat the downloaded file as a reusable style guide. Add it to the model's system/project instructions when supported, or paste it at the start of a conversation and then provide a concrete writing task. Model interfaces and instruction limits change; check the current product UI if a named setting is unavailable. The card guides style but cannot guarantee exact imitation or override a model's policies.

## Privacy and external resources

The profile and export are handled client-side by this single-page app. The language flags are loaded from FlagCDN when a network connection is available. The page also contains links to internetsafer.com. Review these external dependencies and links before deploying a modified copy under another domain.

## Project files

- `index.html` — application markup, styles, translations and JavaScript.
- `AUDYT_PL.md` — implementation and localization review, known issues and recommended follow-up.
