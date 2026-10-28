# Writing Style Card Creator

Multilingual step-by-step writing style profiler for LLMs (EN · ES · PL · DE · FR · IT).

Open `index.html` in any browser — no build step.

---

## 1. Create your style card

1. Open `index.html`
2. Pick language (flags at the top)
3. Go through the steps: name, main rule, 9 style dimensions (multi-select + own text), good/bad examples
4. Click **Download .md for LLM**

You get a Markdown file, e.g. `style-card-yourname.md`.

---

## 2. How to use the .md file with an LLM

The exported file is a **styleguide / system prompt**. The model should follow it when writing as you/your brand.

### ChatGPT (OpenAI)

**Custom GPT / Project instructions**
1. Create a GPT or open a Project
2. Paste the full content of the `.md` into **Instructions** / **System prompt**
3. Save

**Single chat**
1. Start a new chat
2. First message: paste the whole `.md` and write e.g.  
   `From now on, write all answers in this style. Confirm with one short sentence.`
3. Next messages: give the task (post, thread, email, script…)

### Claude (Anthropic)

1. **Projects** → create project → **Project instructions** → paste the `.md`
2. Or in a chat: paste the card first, then:  
   `Apply this style guide to everything you write in this conversation.`

### Grok (xAI)

1. Paste the `.md` at the start of the chat, or put it in **Custom instructions** if available
2. Add: `Always follow this writing style card.`

### Gemini

1. **Gems** / system instructions → paste the card  
2. Or first message in the chat with the same instruction as above

### Local models (Ollama, LM Studio, etc.)

Put the `.md` content in the **system prompt** field of the chat UI or in the model’s system template.

---

## 3. How to use it effectively

| Do | Don’t |
|----|--------|
| Paste the **entire** card once at the start (or in system/instructions) | Paste only 1–2 lines — the model needs the full rules |
| Give a **clear task** after the card: topic, length, channel (X / LinkedIn / email) | Assume the model “remembers” the style from last week |
| Ask for 2–3 variants if you want choice | Mix this style with another style card in the same system prompt |
| After a long chat, **re-paste** the card or start a new chat with it | Rely only on “write like me” without the card |
| Keep good/bad example sentences in the card — they steer the model a lot | Leave the examples empty if you care about tone |

**Example prompt after loading the card:**

```text
Using the style card above, write a short X (Twitter) post about testing the new model X vs Y on the same prompts. Include one concrete number. End with a question to the audience.
```

**For Instagram / Reels script:**

```text
Using the style card, write a 30-second Reel script: hook in the first line, 3 steps, show result first then how. CTA: comment KEYWORD for the prompt.
```

---

## 4. Deploy on home.pl (or any classic hosting)

Yes — you can put the app on home.pl. GitHub does not push directly to home.pl; you **download from GitHub (or from this chat) and upload** to the server.

### Option A – File manager in home.pl panel (easiest)

1. Download `index.html` (from GitHub: raw file, or from Grok artifacts as `karta-stylu-kreator.html` renamed to `index.html`)
2. Log in to **Panel home.pl** → **Hosting** → **Menedżer plików** (or FTP)
3. Go to `public_html` (or the folder for your domain/subdomain)
4. Upload `index.html`
5. Open `https://twoja-domena.pl/` (or `/index.html`)

### Option B – FTP (FileZilla, WinSCP, Cyberduck)

1. In home.pl panel: create/get FTP login (host often `ftp.twoja-domena.pl`)
2. Connect with FTP client
3. Upload `index.html` into `public_html`
4. Set permissions if needed (usually 644 for the file)

### Option C – Git on the server (if SSH / git is available)

On many shared home.pl plans there is **no** full git deploy. If you have SSH and git:

```bash
cd public_html
git clone https://github.com/HiTom7/Writing-Style-Card-Creator.git .
# ensure index.html is the full app file
```

Otherwise stick to A or B.

### Notes for home.pl

- No Node/build required — pure static HTML
- Works on HTTP and HTTPS once the domain has SSL in the panel
- For a subdomain: point subdomain to the same or another folder and put `index.html` there
- Optional: add a short `README` or link from your main site: “Kreator karty stylu”

---

## 5. Features

- 13-step wizard (identity → main rule → 9 style dimensions → examples → export)
- ~20 culturally adapted multi-select options per section, per language
- Free-text on every step
- Exports Markdown ready as system prompt for any LLM

### Languages

🇬🇧 English · 🇪🇸 Español · 🇵🇱 Polski · 🇩🇪 Deutsch · 🇫🇷 Français · 🇮🇹 Italiano
