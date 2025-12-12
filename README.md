# $5 Vault

Static (single-page) marketplace site for selling $5 AI prompts + n8n automations.

## Deploy (Vercel)

This repo is **static HTML** (no build step). Vercel will serve `index.html` automatically.

### Option A: Vercel CLI

```bash
cd "/Users/simeonreid/AiSim Virtual Workspace/five-dollar-vault"
vercel --prod
```

### Option B: Vercel Dashboard

- Import this repo
- Framework preset: **Other**
- Build command: **none**
- Output directory: **.**

## Update links

- Stripe Payment Links are hardcoded in `index.html`.
- Membership link is also hardcoded in `index.html`.
- Discord invite link is currently a placeholder; update it after you create the server.


