# $5 Vault — ConvertKit Email Sequences (Copy/Paste)

## Sequence 1: Post‑Purchase Welcome (Trigger: any $5 purchase)

### Email 1 (Immediate)
**Subject:** Your $5 Vault download is ready! 🎉

**Body:**
Hi {{ subscriber.first_name | default: "there" }},

Thanks for grabbing **{{ purchase.product_name }}**.

Your download:
- {{ purchase.download_link }}

Need help using it? Join the community:
- {{ discord_invite_link }}

Want the best value? The Ultimate Bundle is **10 tools for $25**:
- {{ bundle_link }}

— $5 Vault

### Email 2 (24 hours later)
**Subject:** Quick tip to get results faster

**Body:**
Here’s the fastest way to get value from **{{ purchase.product_name }}**:

1) {{ quickstart_step_1 }}
2) {{ quickstart_step_2 }}
3) {{ quickstart_step_3 }}

If you get stuck, reply to this email or ask in Discord:
- {{ discord_invite_link }}

### Email 3 (48 hours later)
**Subject:** Last chance: 10 tools for $25

**Body:**
Quick reminder: the **Ultimate Bundle** offer ends soon.

If you’re planning to grab more than a couple items, it’s the cheapest way in:
- {{ bundle_link }}

— $5 Vault

---

## Sequence 2: Bundle Buyer (Trigger: $25 bundle purchase)

### Email 1 (Immediate)
**Subject:** Your Ultimate Bundle is ready ✅

**Body:**
Here’s your bundle access:
- {{ bundle_download_link }}

Start here (recommended order):
1) Business Essentials Prompts
2) Lead Generator Automation
3) Content Creator Prompts

Join Discord for support + updates:
- {{ discord_invite_link }}

### Email 2 (3 days later)
**Subject:** Getting the most from your bundle

**Body:**
Two quick wins:
- Win #1: {{ win_1 }}
- Win #2: {{ win_2 }}

If you want everything + new drops monthly, membership is here:
- {{ membership_link }}

### Email 3 (7 days later)
**Subject:** Ready for unlimited access?

**Body:**
Membership includes:
- Unlimited downloads
- New releases
- Member-only Discord channels

Join here:
- {{ membership_link }}

---

## Sequence 3: Membership Onboarding (Trigger: $47/mo subscription)

### Email 1 (Immediate)
**Subject:** Welcome to $5 Vault Membership 🎓

**Body:**
You’re in ✅

Start here:
- Vault access: {{ vault_url }}
- Member guide: {{ member_guide_url }}

Join Discord (member channels unlock after role assignment):
- {{ discord_invite_link }}

### Email 2 (Weekly, ongoing)
**Subject:** This week’s new releases in the Vault

**Body:**
New this week:
- {{ release_1 }}
- {{ release_2 }}
- {{ release_3 }}

Discuss in Discord:
- {{ discord_invite_link }}


