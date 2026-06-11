# NOVA — Tactical AI Core `v0.1`

Personal AI coaching interface inspired by Cortana / Halo. Powered by Claude Sonnet via the Anthropic API. Fully static — deploys to Netlify with zero configuration.

---

## Quick deploy (< 5 min)

### 1. Push to GitHub

```bash
git init
git add .
git commit -m "Nova v0.1"
git remote add origin https://github.com/YOUR_USERNAME/nova.git
git push -u origin main
```

### 2. Deploy on Netlify

1. Go to [netlify.com](https://netlify.com) → **Add new site** → **Import from Git**
2. Pick your repo
3. Leave all build settings blank — `netlify.toml` handles everything
4. Click **Deploy site**
5. Your live URL is ready in ~30 seconds

### 3. First launch

Open your Netlify URL → enter your Anthropic API key → Nova initializes.

Get a key at [console.anthropic.com](https://console.anthropic.com)

---

## Run locally

No server, no install. Just open the file:

```bash
# Direct open
open index.html

# Or serve locally to avoid any CORS edge cases
python3 -m http.server 8000
# → http://localhost:8000
```

---

## API Key security

- Stored in `localStorage` in your browser only
- Transmitted directly to `api.anthropic.com` — never touches any intermediate server
- Use the **Re-Auth** button in the header to clear and replace it
- Do not share your deployed URL with people you don't trust — they could use their own key but your profile context would be visible

---

## Customize Nova

Edit the `PROFILE` object inside `index.html` (look for `/* PROFILE */`):

```js
const PROFILE = {
  name: "Chief",
  age: 35,
  location: "Connecticut, USA",
  active_projects: [...],
  tech_milestones: {...},
  constraints: {...},
  preferences: {...}
};
```

This object gets injected into Nova's system prompt on every message.

---

## File structure

```
nova/
├── index.html       ← entire app — HTML, CSS, JS, all self-contained
├── netlify.toml     ← deploy config + security headers
├── README.md
└── .gitignore
```

The `app.py` / `requirements.txt` files are the optional local Python backend — not needed for Netlify.

---

## Roadmap

- `v0.1` — Core chat, key auth, memory matrix, boot sequence, particle UI
- `v0.2` — Voice input (Web Speech API), persistent chat history
- `v0.3` — Editable profile via UI, milestone tracker panel
