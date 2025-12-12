# $5 Vault - Starter Bundle 🚀

> **5 Premium Prompts + 1 Automation = $5** (Normally $10+ value)

---

## What's Included

### 🎯 5 Hand-Picked Prompts

#### 1. The Universal Business Email Writer
```
You are an expert business communicator. Write a professional email for the following situation:

Context: [DESCRIBE THE SITUATION]
Recipient: [WHO ARE YOU WRITING TO]
Desired Outcome: [WHAT DO YOU WANT TO HAPPEN]
Tone: [formal/friendly/urgent/apologetic]

Requirements:
- Clear subject line that gets opened
- Hook in the first sentence
- Concise body (under 150 words)
- Specific call-to-action
- Professional sign-off

Output the email ready to copy-paste.
```

#### 2. The 60-Second Content Idea Generator
```
Generate 10 content ideas for [YOUR BUSINESS/NICHE] that I can create in under 60 seconds each.

Target audience: [DESCRIBE YOUR AUDIENCE]
Platforms: [TikTok/Instagram Reels/YouTube Shorts/Twitter]
Content goal: [awareness/engagement/sales/education]

For each idea provide:
1. Hook (first 3 seconds)
2. Main point (10-15 seconds)
3. Call-to-action
4. Hashtags (5 relevant ones)

Focus on ideas that feel authentic, not salesy.
```

#### 3. The Customer Objection Crusher
```
I sell [YOUR PRODUCT/SERVICE] to [TARGET AUDIENCE].

Common objection I hear: "[THE OBJECTION]"

Create 5 different responses to overcome this objection:

1. The Empathy Response - Acknowledge and redirect
2. The Logic Response - Facts and data
3. The Story Response - Customer success example
4. The Question Response - Turn it back on them
5. The Reframe Response - Change their perspective

Each response should be natural, not pushy, and under 50 words.
```

#### 4. The Meeting Notes Transformer
```
Transform these meeting notes into actionable outputs:

[PASTE YOUR MESSY MEETING NOTES]

Create:
1. Executive Summary (3 bullet points max)
2. Action Items (who does what by when)
3. Decisions Made (with rationale)
4. Open Questions (need follow-up)
5. Follow-up Email Draft (to send to attendees)

Format everything for easy copy-paste into project management tools.
```

#### 5. The Social Proof Generator
```
Help me create compelling social proof content for [YOUR BUSINESS].

I have this customer result/testimonial:
[PASTE THE RAW TESTIMONIAL OR RESULT]

Transform it into:
1. LinkedIn post format (professional, story-driven)
2. Twitter thread (5 tweets, hook-heavy)
3. Instagram caption (engaging, with CTA)
4. Case study headline options (5 variations)
5. Email subject line options (5 variations)

Make each version feel authentic, not braggy.
```

---

### ⚡ 1 Bonus Automation

#### Quick Lead Qualifier Bot

A simplified version of our Lead Generator that you can run manually:

```json
{
  "name": "$5 Vault - Quick Lead Qualifier",
  "nodes": [
    {
      "parameters": {
        "httpMethod": "POST",
        "path": "quick-qualify",
        "responseMode": "responseNode",
        "options": {}
      },
      "id": "webhook",
      "name": "Start",
      "type": "n8n-nodes-base.webhook",
      "typeVersion": 2,
      "position": [0, 0],
      "webhookId": "quick-qualify-5vault"
    },
    {
      "parameters": {
        "assignments": {
          "assignments": [
            {
              "id": "business",
              "name": "businessName",
              "value": "={{ $json.body?.businessName || $json.businessName }}",
              "type": "string"
            },
            {
              "id": "industry",
              "name": "industry",
              "value": "={{ $json.body?.industry || $json.industry }}",
              "type": "string"
            },
            {
              "id": "website",
              "name": "hasWebsite",
              "value": "={{ $json.body?.hasWebsite || $json.hasWebsite || false }}",
              "type": "boolean"
            },
            {
              "id": "employees",
              "name": "employeeCount",
              "value": "={{ $json.body?.employeeCount || $json.employeeCount || '1-10' }}",
              "type": "string"
            }
          ]
        }
      },
      "id": "config",
      "name": "Set Lead Info",
      "type": "n8n-nodes-base.set",
      "typeVersion": 3.4,
      "position": [220, 0]
    },
    {
      "parameters": {
        "method": "POST",
        "url": "=https://generativelanguage.googleapis.com/v1beta/models/gemini-2.0-flash:generateContent?key={{ $env.GEMINI_API_KEY }}",
        "sendBody": true,
        "specifyBody": "json",
        "jsonBody": "={\n  \"contents\": [{\n    \"parts\": [{\n      \"text\": \"Score this business lead 1-10 on likelihood to need AI/automation services.\\n\\nBusiness: {{ $json.businessName }}\\nIndustry: {{ $json.industry }}\\nHas Website: {{ $json.hasWebsite }}\\nEmployee Count: {{ $json.employeeCount }}\\n\\nConsider:\\n- Industry automation potential\\n- Business size (sweet spot: 5-50 employees)\\n- Digital presence maturity\\n- Likely pain points\\n\\nRespond with ONLY JSON: {\\\"score\\\": <1-10>, \\\"reason\\\": \\\"<2 sentences>\\\", \\\"suggestedApproach\\\": \\\"<how to pitch them>\\\"}\"\n    }]\n  }],\n  \"generationConfig\": {\"temperature\": 0.3, \"maxOutputTokens\": 200}\n}",
        "options": {"timeout": 30000}
      },
      "id": "qualify",
      "name": "AI Qualifier (FREE)",
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.2,
      "position": [440, 0]
    },
    {
      "parameters": {
        "mode": "runOnceForEachItem",
        "jsCode": "const lead = $('Set Lead Info').item.json;\nconst aiResponse = $input.item.json;\n\nlet result = { score: 5, reason: 'Default', suggestedApproach: 'Standard outreach' };\n\ntry {\n  const text = aiResponse.candidates?.[0]?.content?.parts?.[0]?.text || '{}';\n  const match = text.match(/\\{[\\s\\S]*?\\}/);\n  if (match) result = JSON.parse(match[0]);\n} catch(e) {}\n\nreturn {\n  ...lead,\n  leadScore: result.score,\n  scoreReason: result.reason,\n  suggestedApproach: result.suggestedApproach,\n  priority: result.score >= 7 ? 'HIGH' : result.score >= 5 ? 'MEDIUM' : 'LOW',\n  qualifiedAt: new Date().toISOString()\n};"
      },
      "id": "parse",
      "name": "Parse Result",
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [660, 0]
    },
    {
      "parameters": {
        "respondWith": "json",
        "responseBody": "={\n  \"success\": true,\n  \"lead\": {\n    \"businessName\": \"{{ $json.businessName }}\",\n    \"industry\": \"{{ $json.industry }}\",\n    \"score\": {{ $json.leadScore }},\n    \"priority\": \"{{ $json.priority }}\",\n    \"reason\": \"{{ $json.scoreReason }}\",\n    \"approach\": \"{{ $json.suggestedApproach }}\"\n  }\n}",
        "options": {}
      },
      "id": "response",
      "name": "Return",
      "type": "n8n-nodes-base.respondToWebhook",
      "typeVersion": 1.1,
      "position": [880, 0]
    }
  ],
  "connections": {
    "Start": {
      "main": [[{"node": "Set Lead Info", "type": "main", "index": 0}]]
    },
    "Set Lead Info": {
      "main": [[{"node": "AI Qualifier (FREE)", "type": "main", "index": 0}]]
    },
    "AI Qualifier (FREE)": {
      "main": [[{"node": "Parse Result", "type": "main", "index": 0}]]
    },
    "Parse Result": {
      "main": [[{"node": "Return", "type": "main", "index": 0}]]
    }
  },
  "settings": {"executionOrder": "v1"},
  "versionId": "5vault-quick-qualify-v1",
  "active": false,
  "tags": [{"name": "$5 Vault"}, {"name": "Starter Bundle"}]
}
```

---

## 🛠️ Setup Instructions

### For the Prompts
1. Copy any prompt above
2. Replace the [BRACKETED] sections with your info
3. Paste into ChatGPT, Claude, or Gemini
4. Get instant results!

### For the Automation
1. Import the JSON into your n8n instance
2. Set your `GEMINI_API_KEY` environment variable (free at ai.google.dev)
3. Activate the workflow
4. Send POST requests to test

**Example API Call:**
```bash
curl -X POST https://your-n8n.com/webhook/quick-qualify \
  -H "Content-Type: application/json" \
  -d '{
    "businessName": "Atlanta Dental Group",
    "industry": "Healthcare",
    "hasWebsite": true,
    "employeeCount": "10-25"
  }'
```

---

## 💡 Pro Tips

1. **Stack the prompts** - Use the Email Writer output as input for Social Proof Generator
2. **Batch process** - Qualify multiple leads by calling the automation in a loop
3. **Customize** - Add your industry-specific context to prompts for better results
4. **Track results** - Keep a spreadsheet of which prompts perform best for you

---

## 🎁 Upgrade Path

Love the Starter Bundle? Get more:

- **Individual Packs** - $5 each for specialized prompt collections
- **Full Automations** - $5 each for production-ready n8n workflows
- **Ultimate Bundle** - $25 for everything (10x the value!)
- **Membership** - $47/month for unlimited access + monthly drops

---

*Questions? Join our Discord community for support!*

**The $5 Vault** - Big automation. Small price.
