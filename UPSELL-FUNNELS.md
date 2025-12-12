# $5 Vault - Upsell Funnels & Community Strategy

## The $5 Entry Point Flywheel

```
                    ┌─────────────────┐
                    │   FREE CONTENT  │
                    │  (TikTok/YT/X)  │
                    └────────┬────────┘
                             │
                             ▼
                    ┌─────────────────┐
                    │   $5 PURCHASE   │◄────┐
                    │  (First Trust)  │     │
                    └────────┬────────┘     │
                             │              │
                             ▼              │
                    ┌─────────────────┐     │
                    │  DISCORD JOIN   │     │
                    │  (Community)    │     │
                    └────────┬────────┘     │
                             │              │
              ┌──────────────┼──────────────┤
              │              │              │
              ▼              ▼              ▼
        ┌───────────┐ ┌───────────┐ ┌───────────┐
        │  BUNDLE   │ │ MEMBERSHIP│ │  COURSE   │
        │   $25     │ │  $47/mo   │ │   $97+    │
        └─────┬─────┘ └─────┬─────┘ └─────┬─────┘
              │             │             │
              └──────────┬──┴─────────────┘
                         │
                         ▼
                ┌─────────────────┐
                │  DONE-FOR-YOU   │
                │    $297-997     │
                └─────────────────┘
```

---

## Funnel #1: The Taste Test

**Trigger:** First $5 purchase

### Immediate Post-Purchase Email
```
Subject: Your $5 Vault download is ready! 🎉 (+ a surprise inside)

Hey [NAME],

Your [PRODUCT NAME] is attached below.

But before you dive in, I want to share something...

That $5 product you just bought? It's ONE item from a collection
of 10+ premium tools I use daily in my automation business.

Right now, I'm offering the **complete collection** for just $25.

That's 10+ products for the price of 5.

→ [GRAB THE ULTIMATE BUNDLE - $25]

This offer expires in 48 hours.

To your success,
The $5 Vault Team

P.S. - Join our Discord community for free support: [DISCORD LINK]
```

### 48-Hour Follow-Up (Non-Purchasers)
```
Subject: Last chance: 10 tools for $25 (expires tonight)

Hey [NAME],

Quick reminder - the Ultimate Bundle deal expires at midnight.

After that, each product goes back to $5 individually.

10 products × $5 = $50
Ultimate Bundle = $25 (50% off)

Math doesn't lie. 🤷

→ [GET THE BUNDLE BEFORE MIDNIGHT]

- The $5 Vault Team
```

---

## Funnel #2: The Power User Path

**Trigger:** 3+ purchases within 30 days

### Membership Offer Email
```
Subject: You're spending more than a member... let me fix that

Hey [NAME],

I noticed you've grabbed [X] products this month. Love it!

Quick math: [X] × $5 = $[TOTAL]

Here's the thing - our $47/month membership gives you:
✓ Unlimited access to EVERYTHING in the vault
✓ New products dropped monthly
✓ Private Discord channel
✓ Monthly live Q&A with me
✓ Custom prompt requests

If you're buying 10+ products/month, membership literally
saves you money while giving you MORE.

→ [BECOME A MEMBER - $47/MONTH]

First month comes with a 30-day money-back guarantee.

- The $5 Vault Team
```

---

## Funnel #3: The Results Accelerator

**Trigger:** Member for 2+ months OR purchased $100+ total

### Course Upsell Email
```
Subject: Ready to build your own $5 products?

Hey [NAME],

You've been crushing it with $5 Vault tools.

But what if you could CREATE tools like these?

I'm opening enrollment for my course:
**"The $5 Product Machine"**

You'll learn:
• How I create prompts that sell (my exact framework)
• Building n8n automations from scratch
• Pricing psychology that converts
• Distribution strategies that scale

Price: $97 (one-time)

This is the same system that built The $5 Vault.

→ [ENROLL IN THE COURSE - $97]

Limited to 50 students this round.

- The $5 Vault Team
```

---

## Funnel #4: The VIP Treatment

**Trigger:** Course graduate OR spent $200+ total

### Done-For-You Offer
```
Subject: Let us build it for you

Hey [NAME],

You're clearly serious about automation.

What if we built your custom system... for you?

Our Done-For-You service includes:
• Strategy call (60 min) to map your needs
• Custom n8n workflows built to your specs
• Prompt libraries tailored to your business
• 30 days of support & refinement
• Training video for your team

Investment: $297-$997 (based on complexity)

We only take 5 DFY clients per month.

Want to see if you're a fit?

→ [BOOK A STRATEGY CALL]

- The $5 Vault Team
```

---

## Discord Community Structure

### Channel Setup

```
📢 ANNOUNCEMENTS
├── #welcome
├── #rules
├── #new-releases
└── #community-wins

💬 GENERAL
├── #introductions
├── #general-chat
├── #show-your-work
└── #questions

📦 PRODUCTS
├── #prompt-support
├── #automation-support
├── #feature-requests
└── #bug-reports

🎓 LEARNING
├── #tips-and-tricks
├── #tutorials
├── #resources
└── #book-club

💎 MEMBERS ONLY (Role-gated)
├── #vip-lounge
├── #early-access
├── #monthly-qa
└── #custom-requests

🛠️ SUPPORT
├── #tech-help
├── #billing
└── #feedback
```

### Role Structure

| Role | Access | How to Get |
|------|--------|------------|
| @Everyone | Public channels | Join server |
| @Customer | Product channels | Any $5 purchase |
| @Bundle Owner | Extended support | $25 bundle |
| @Member | VIP channels | $47/mo subscription |
| @Course Graduate | Exclusive resources | Complete course |
| @VIP | Everything + DMs | $500+ spent |

### Engagement Tactics

1. **Weekly Prompt Challenge**
   - Post a problem on Monday
   - Community submits prompt solutions
   - Best prompt wins free product

2. **Automation Showcase**
   - Members share their workflows
   - Upvotes determine "Automation of the Week"
   - Winner gets featured on socials

3. **AMA Sessions**
   - Monthly live Q&A for members
   - Record and clip for content
   - Non-members see highlights → FOMO

4. **Referral Program**
   - Share unique link
   - 20% commission on sales
   - Tracked via Stripe + affiliate link

---

## Automation: Post-Purchase Discord Invite

```json
{
  "trigger": "Stripe webhook (checkout.session.completed)",
  "steps": [
    {
      "action": "Generate unique Discord invite",
      "tool": "Discord API"
    },
    {
      "action": "Send welcome email with invite",
      "tool": "Email (ConvertKit/Mailchimp)"
    },
    {
      "action": "Tag customer in CRM",
      "tool": "Airtable/Notion"
    },
    {
      "action": "Schedule follow-up sequence",
      "tool": "Email automation"
    }
  ]
}
```

---

## Metrics to Track

### Funnel Health
- **$5 → $25 Bundle**: Target 15% conversion
- **$25 → $47 Membership**: Target 10% conversion
- **Membership → $97 Course**: Target 5% conversion
- **Course → DFY**: Target 3% conversion

### Community Health
- Discord DAU (Daily Active Users)
- Messages per day
- Support ticket resolution time
- Feature request volume
- Referral rate

### Revenue Mix Target (Month 6+)
- 30% from $5 products
- 25% from $25 bundles
- 30% from $47 memberships
- 10% from courses
- 5% from DFY services

---

## Quick Start Checklist

- [ ] Set up Discord server with channel structure
- [ ] Create roles and permissions
- [ ] Configure Stripe webhooks for purchase tracking
- [ ] Build email sequences in ConvertKit/Mailchimp
- [ ] Set up affiliate/referral tracking
- [ ] Create upsell landing pages
- [ ] Schedule first community event
- [ ] Document support FAQs
- [ ] Train on Discord moderation
- [ ] Launch! 🚀

---

*The $5 Vault - Where $5 is just the beginning.*
