# Writing Style Card Creator

Multilingual step-by-step writing style profiler for LLMs (EN · ES · PL · DE · FR · IT).

## Status

Repository created from Grok. The full single-file app (`index.html`, ~97 KB) is in the Grok conversation artifacts as **karta-stylu-kreator.html**.

### Add the full app (recommended)

1. In the Grok chat, download **karta-stylu-kreator.html** from the artifacts panel.
2. Rename it to `index.html`.
3. Push from your machine:

```bash
git clone https://github.com/HiTom7/Writing-Style-Card-Creator.git
cd Writing-Style-Card-Creator
# copy downloaded file over index.html
git add index.html
git commit -m "Add full Writing Style Card Creator"
git push
```

Or in the GitHub web UI: **Add file → Upload files** and replace `index.html`.

### Why not fully auto-exported from Grok in one click?

Grok’s GitHub connector **can** create repositories and push files (this repo proves it). Very large single-file payloads (~100 KB self-contained HTML) can hit size limits on the integration path in one tool call. Creating the repo + README works reliably; the app file is simplest to attach once via **download from Grok → upload to GitHub** or local `git push`.

This is a transport/limit of the connector path, not a problem with your account permissions for normal repo use.

### Features

- 13-step wizard (identity → main rule → 9 style dimensions → examples → export)
- ~20 culturally adapted multi-select options per section, per language
- Free-text override on every step
- Exports Markdown ready as system prompt / styleguide for any LLM

### Languages

🇬🇧 English · 🇪🇸 Español · 🇵🇱 Polski · 🇩🇪 Deutsch · 🇫🇷 Français · 🇮🇹 Italiano

Open `index.html` in any browser — no build step.
