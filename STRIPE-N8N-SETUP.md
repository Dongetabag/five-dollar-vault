# $5 Vault — Stripe → n8n Delivery Setup

## Goal
When someone purchases a Stripe Payment Link, Stripe sends a webhook to n8n, and n8n:
- identifies the product (by amount or price_id)
- emails the download link(s)
- optionally generates a single-use Discord invite
- tags the buyer in ConvertKit

## 1) Stripe webhook endpoint

In Stripe Dashboard → Developers → Webhooks:

- Add endpoint URL: `https://YOUR_N8N_DOMAIN/webhook/stripe-purchase`
- Select events:
  - `checkout.session.completed`
  - `customer.subscription.created`
  - `customer.subscription.deleted`

Copy:
- **Signing secret** (starts with `whsec_...`)

## 2) Minimal n8n workflow logic (outline)

### Webhook trigger (POST `/stripe-purchase`)
- Verify signature (recommended)
- Parse the payload

### Identify product
Use one of:
- `price_id` (best) from the event line items
- `amount_total` in cents (fallback)

### Route
- `$5 product` → send 1 product file
- `$25 bundle` → send bundle pack
- `$47/mo membership` → send onboarding + role assignment instructions

## 3) Mapping (from your `index.html`)

Your site uses these Stripe payment links (source of truth: `five-dollar-vault/index.html`):

- $5 products:
  - Business Essentials: `https://buy.stripe.com/00w9ASfz91kqgMFbgvcZa03`
  - Lead Generator: `https://buy.stripe.com/eVq6oGcmXe7c3ZTacrcZa04`
  - Content Creator: `https://buy.stripe.com/dRm3cucmXbZ4eEx58ncZa05`
  - Social Media Poster: `https://buy.stripe.com/fZu6oGcmX5AG53X84jcZa06`
  - Starter Bundle ($5): `https://buy.stripe.com/5kQdR81Ij4wC2VP1FVcZa07`
- Ultimate Bundle ($25):
  - `https://buy.stripe.com/fZu7sKfz99QWeEx4S7cZa08`
- Membership ($47/mo):
  - `https://buy.stripe.com/fZubJ0cmXaV0cwp70fcZa09`

## 4) What I need from you to fully automate delivery

- **Where are the downloadable files hosted?**
  - S3? Gumroad? Google Drive? A private URL? (Right now the repo has product *source* files, not a delivery mechanism.)
- **Email sending method**
  - ConvertKit, SendGrid, Gmail SMTP, etc.
- **Discord bot token** (if generating one-time invites)


