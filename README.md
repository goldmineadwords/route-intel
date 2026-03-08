# Route Intel — Bid Intelligence System

## Deploy to Netlify (no local setup needed)

### Step 1 — Push to GitHub
1. Create a new repo on github.com
2. Upload all these files to the repo
3. Commit

### Step 2 — Connect to Netlify
1. Go to app.netlify.com
2. Click "Add new site" → "Import an existing project"
3. Connect GitHub → select your repo
4. Build settings are auto-detected from netlify.toml:
   - Build command: `npm run build`
   - Publish directory: `dist`
5. Click "Deploy site"

### Step 3 — Add Environment Variables
In Netlify → Site settings → Environment variables, add:

```
AMADEUS_CLIENT_ID        = your amadeus key
AMADEUS_CLIENT_SECRET    = your amadeus secret
APIFY_TOKEN              = your apify token
VITE_CLAUDE_API_KEY      = your claude api key
```

### Step 4 — Redeploy
After adding env vars:
Netlify → Deploys → "Trigger deploy" → "Deploy site"

Your site is live.

---

## How It Works

```
Browser → Netlify Functions → Amadeus/Apify APIs
                           → OpenFlights (GitHub raw)

API keys are ONLY on Netlify server.
Never in browser. Never in code.
```

## Environment Variables

| Variable | Where to get |
|---|---|
| AMADEUS_CLIENT_ID | developers.amadeus.com → your app |
| AMADEUS_CLIENT_SECRET | same page, reveal secret |
| APIFY_TOKEN | apify.com → Settings → Integrations |
| VITE_CLAUDE_API_KEY | console.anthropic.com → API keys |

## OpenFlights Data
Routes are fetched live from:
https://github.com/jpatokal/openflights/blob/master/data/routes.dat
67,663 real operated routes. No hardcoding.
