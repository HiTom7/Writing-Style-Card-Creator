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

## 4. Features

- 13-step wizard (identity → main rule → 9 style dimensions → examples → export)
- ~20 culturally adapted multi-select options per section, per language
- Free-text on every step
- Exports Markdown ready as system prompt for any LLM

### Languages

🇬🇧 English · 🇪🇸 Español · 🇵🇱 Polski · 🇩🇪 Deutsch · 🇫🇷 Français · 🇮🇹 Italiano
