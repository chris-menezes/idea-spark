# Idea Spark 💡

A word-fusion idea generator powered by Claude. Self-hosted, shareable with anyone.

---

## File structure

```
idea-spark/
├── public/
│   └── index.html     ← the frontend
├── server.js          ← Express proxy server
├── package.json
└── README.md
```

---

## Local setup (test before deploying)

```bash
# 1. Install dependencies
npm install

# 2. Set your Anthropic API key
export ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxxxx

# 3. Run
npm start

# 4. Open http://localhost:3000
```

---

## Deploy to Railway (free tier, ~5 mins)

1. **Create a GitHub repo** called `idea-spark`
2. **Add these files** to the repo (keep the folder structure above — index.html goes inside a `public/` folder)
3. Go to **[railway.app](https://railway.app)** → New Project → Deploy from GitHub repo → select `idea-spark`
4. Once deployed, go to **Variables** tab and add:
   ```
   ANTHROPIC_API_KEY = sk-ant-xxxxxxxxxxxxxxxx
   ```
5. Go to **Settings → Networking → Generate Domain** — Railway gives you a free public URL
6. Share that URL with anyone — it just works ✅

---

## Getting an Anthropic API key

1. Go to [console.anthropic.com](https://console.anthropic.com)
2. Sign up / log in
3. Navigate to **API Keys** → **Create Key**
4. Copy and paste into Railway's Variables tab

> Cost: Claude Sonnet is ~$3 per million input tokens. Each idea generation call uses roughly 300–500 tokens. You'd need to generate thousands of ideas to spend even $1.

---

## Customisation

- **Change the model**: Edit `server.js` line with `model:` — swap to `claude-haiku-4-5-20251001` for faster/cheaper responses
- **Add a password**: Wrap the `/api/generate` route with a simple check on a secret header if you want to limit who can use it
- **Custom domain**: Railway supports custom domains under Settings → Networking
