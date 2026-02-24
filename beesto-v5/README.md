# 🐝 Beesto AI — v5.0

A premium, fully client-side AI chatbot with smart file routing, vision analysis, PDF reading, and audio transcription.

## ✅ What's fixed in v5.0

| Issue | Fix |
|-------|-----|
| Vision broken on Groq | Removed `detail` param — Groq doesn't support it |
| PDF not analysed | Improved extraction (40pp, 150k chars) with structured context injection |
| Token limits causing 400 errors | Exact per-model limits via `GROQ_MODEL_MAX_TOKENS` map |
| Conflicting animations | Single CSS keyframe source, smooth transitions |
| Image detail on OpenAI | `detail:'high'` applied only to OpenAI/OpenRouter |

## 🚀 Quick Start

Just open `index.html` in a browser. No build step, no server needed.

```bash
# Or serve locally:
npx serve .
# or
python3 -m http.server 8080
```

## 📁 Structure

```
beesto-ai/
├── index.html        # Main app (Alpine.js, Tailwind CDN)
├── js/
│   └── app.js        # All logic — routing, API calls, state
├── css/
│   └── styles.css    # Animations, prose, code blocks
├── .env.local        # API key reference (gitignored)
└── .gitignore
```

## 🔑 API Keys

- **Groq** — Built-in key, works out of the box. Vision (LLaMA 4 Scout) + Whisper + text.
- **OpenRouter / Gemini / OpenAI / xAI** — Add in ⚙️ Settings.

## 🖼️ Vision Details

| Provider | Image detail sent |
|----------|------------------|
| Groq (LLaMA 4) | No `detail` param (Groq doesn't support it) |
| OpenAI / OpenRouter | `detail: 'high'` for maximum quality |
| Gemini | Native format via OpenAI-compat endpoint |

## 📄 PDF Analysis

1. PDF.js extracts text client-side (up to 40 pages, 150k chars)
2. Text is wrapped with page markers and injected as structured context
3. Your selected text model (default: LLaMA 3.3 70B) reads and analyses it
