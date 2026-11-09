# Clay Email Checker

A local dashboard for scoring and revising Clay prospecting emails. Paste an email (rough drafts are fine), pick the persona and vertical, and the checker:

- Scores it 0–100 using the archetype rubric in [prompt.md](prompt.md) (8 categories, archetype weights and hard caps)
- Lists the top fixes, flags and line edits
- Writes a revised, send-ready draft that's coached toward the 100/100 gold-standard email
- Saves every result to your history so you can reopen it and track your progress

## Setup

Requires Node 20.12 or later.

```bash
npm install
cp .env.example .env   # then paste your Anthropic API key into .env
npm start
```

Open http://localhost:3000.

## Files

| File | What it is |
|---|---|
| `prompt.md` | The checker's system prompt. Edit approved claims, personas, verticals or the gold-standard email here. Changes apply on the next check, with no restart. |
| `server.js` | Serves the page and sends each email to Claude (`claude-opus-5-5`, override with `CLAUDE_MODEL`). |
| `index.html` | The dashboard. |
| `lib.js` | Prompt loading, request building and JSON parsing. Tested in `test/`. |
| `history.json` | Your scored emails. Created on first use and kept out of git. |

## Tests

```bash
npm test
```
