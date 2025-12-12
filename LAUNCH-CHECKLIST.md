# $5 Vault — Launch Checklist (End-to-End)

## 0) What’s already done

- **GitHub repo**: `https://github.com/Dongetabag/five-dollar-vault`
- **Vercel production URL**: `https://five-dollar-vault-d54b81c4c-dongetabags-projects.vercel.app`

## 1) Update the website with your Discord invite

- Create a permanent Discord invite link (Never Expire)
- Update `five-dollar-vault/index.html`:
  - Replace `https://discord.gg/YOUR_INVITE_CODE`

Then:

```bash
cd "/Users/simeonreid/AiSim Virtual Workspace/five-dollar-vault"
git add index.html
git commit -m "Add Discord invite link"
git push origin main
```

Vercel will auto-deploy.

## 2) Discord server + bot setup (manual steps)

### Server
- **Server name**: `$5 Vault Community`
- Create categories + channels (copy/paste from `CURSOR-INSTRUCTIONS.html`)
- Create roles:
  - `@Customer` (Green `#10B981`)
  - `@Bundle Owner` (Blue `#3B82F6`)
  - `@Member` (Purple `#8B5CF6`)
  - `@VIP` (Gold `#F59E0B`)

### Bot (for automation)
- Create app in Discord Developer Portal
- Add bot
- Enable intents:
  - Server Members Intent
  - Message Content Intent
- Keep token secure

## 3) Payments + delivery decision

This site currently links to **Stripe Payment Links**. That means you must choose how delivery works:

- **Option A (Fastest)**: Keep Stripe links + build **n8n delivery workflow** triggered by Stripe webhooks
- **Option B (Simplest delivery)**: Move products to Gumroad and replace links with Gumroad product URLs

## 4) Email automation (ConvertKit)

- Create ConvertKit account
- Create sequences:
  - Post-purchase welcome (any $5)
  - Bundle buyer ($25)
  - Membership onboarding ($47/mo)

## 5) Stripe webhooks

- Create Stripe webhook endpoint (recommended events):
  - `checkout.session.completed`
  - `customer.subscription.created`
  - `customer.subscription.deleted`
- Point the webhook to your n8n endpoint (e.g. `/webhook/stripe-purchase`)

## 6) Final test

- Do a $5 test purchase
- Confirm:
  - Buyer gets delivery email
  - Buyer gets Discord invite
  - Tags/segments are correct in ConvertKit


