# 🎙️ Vocallabs.ai — Product Teardown
**Product Intern Assignment · Aryan Patel · May 2026**

> A hands-on, two-day product teardown of [Vocallabs.ai](https://vocallabs.ai) — covering GTM gaps, competitor benchmarking, UX failures, feature invisibility, and partnership opportunities. Every finding is backed by a timestamped screenshot taken during live exploration.

📄 **[Read the Full Teardown PDF →](./Product_Teardown_Vocallabs_Aryan_Patel.pdf)**

> **Note for reviewers:** All screenshots mentioned below are embedded directly inside the PDF above, with visible system clock timestamps verifying when each observation was made. No separate screenshot folder — everything is in the PDF.

---

## 🔍 What I Explored (Over 2 Days)

I explored Vocallabs.ai across **five sessions** treating myself as two personas simultaneously:
- **Ops Manager** at a small Indian business evaluating AI calling software
- **Developer** trying to integrate the SDK and build a workflow

| Day | Sessions | What I Did |
|-----|----------|------------|
| Day 1 (29 May) | 3 sessions | Homepage deep-dive, URL probing, Retell signup comparison, GitHub repo audit, pricing check |
| Day 2 (30–31 May) | 2 sessions | Blog source inspection, n8n README analysis, docs audit, WhatsApp/Freshworks research, mobile UX testing |

---

## 📋 Finding Summary

All observations, screenshots, problems, and ship-instead solutions are documented in the **[Teardown PDF](./Product_Teardown_Vocallabs_Aryan_Patel.pdf)**. Quick overview:

---

### 🔴 F1 — No Self-Serve Access (No Signup, No Pricing)
*PDF pages 7–8*

Tested every button on vocallabs.ai — all lead to a booking form. Typed `/signup`, `/login`, `/register`, `/app`, `/pricing` directly — all returned 404. Signed up for Retell as a benchmark: working agent in under 8 minutes, no sales call.

**Screenshots in PDF:** `vocallabs.ai/signup` 404 · `vocallabs.ai/pricing` 404 · `retellai.com/pricing` showing transparent per-minute pricing

---

### 🔴 F2 — Site Navigation Breaks Completely on Mobile and Tablet
*PDF pages 9–11*

Opened vocallabs.ai on mobile — homepage renders as a popup overlay with a single "Talk to an Expert" button. No navigation visible. Closing the popup returns a blank screen. Tested in Chrome DevTools at 768px — hamburger menu (≡) renders but clicking it opens nothing. Solutions, Docs, Blogs, Careers — all unreachable on tablet.

**Screenshots in PDF:** Mobile popup view · Tablet 768px hamburger non-functional

---

### 🟡 F3 — Call Flow Builder Has No Public Demo
*PDF pages 11–13*

Tested `/templates`, `/flows`, `/demo`, `/use-cases` — all 404. YouTube search for "vocallabs call flow builder" — zero results. Checked the vocalflow GitHub repo: 12 forks, 1 star, 3 open PRs with no maintainer response.

**Screenshots in PDF:** vocalflow GitHub (12 forks, 1 star, 3 open PRs) · Retell free dashboard showing templates immediately after signup

---

### 🟡 F4 — AI-to-Human Handoff Is Listed but Has No Public Documentation
*PDF pages 13–15*

Checked `/docs`, `/documentation`, `/api-reference`, `/handoff` — all 404 or login-gated. The n8n README has 100+ operations but no mention of a handoff payload, escalation trigger, or transfer event schema. docs.vocallabs.ai exists but requires login — a buyer cannot evaluate the handoff API before a demo.

**Screenshots in PDF:** `docs.vocallabs.ai` requiring login · `docs.retellai.com` fully public with Build, Test, Deploy, Monitor sections

---

### 🟡 F5 — Emotion Analytics Exist but Cannot Trigger Anything Automatically
*PDF pages 15–17*

Read the full n8n README. Analytics operations exist — Get Call Summary, Get Call Data, Get Call Conversation — but all are pull-only. No `on_call_end` trigger exists. Nothing fires automatically when a call ends with bad sentiment.

**Screenshots in PDF:** n8n Analytics section showing pull-only operations · Homepage claiming emotion + intent + tone analytics

---

### 🟢 Potential Collaborations
*PDF pages 17–19*

Checked WhatsApp Business API docs, Freshworks Marketplace, and n8n community nodes directory. Retell is listed on Freshworks Marketplace. Vocallabs is not. The n8n node has 100+ operations but is not submitted to the official n8n directory.

**Screenshots in PDF:** WhatsApp Business API docs · Freshworks Marketplace showing Retell listed, Vocallabs absent

---

## 🏆 Competitor Snapshot

| Feature | Vocallabs | Retell AI | Bolna AI |
|---------|-----------|-----------|----------|
| Self-serve signup | ❌ Booking form only | ✅ Free tier, API key on signup | ✅ ₹500 pilot, instant access |
| Public pricing | ❌ /pricing returns 404 | ✅ Pay per minute, starts $0 | ✅ INR per outcome, published |
| Homepage CTA | Talk to an Expert | Try For Free + Live Demo | Get Started |
| India language | Claimed (multilingual) | Partial | 50+ Indian accents, Hindi native |
| Template library | ❌ /templates returns 404 | ✅ Visible after free signup | ✅ Industry-specific flows |
| API docs | ❌ Login-gated | ✅ docs.retellai.com | ✅ Published API reference |
| Analytics depth | Emotion + intent + tone (claimed) | Call summary + transcript | Transcript + basic stats |
| n8n integration | ✅ 100+ operations | Zapier + webhooks | Webhooks + API |
| Mobile navigation | ❌ Hamburger broken at 768px | ✅ Functional | ✅ Functional |
| Trust signals | ❌ None visible | G2 rating, named customers | YC logo, named customers |

---

## 📊 Prioritization

`Priority = Impact × (6 − Effort)` · Impact and Effort scored 1–5

| What | Impact | Effort | Priority | When |
|------|--------|--------|----------|------|
| Publish INR pricing page — 3 tiers | 5 | 1 | **25** | This week |
| Fix mobile hamburger + popup rendering | 5 | 1 | **25** | This week |
| Fix blog canonical tags → vocallabs.ai | 4 | 1 | **20** | This week |
| Submit n8n node to community directory | 4 | 1 | **20** | This week |
| Homepage hero in plain HTML | 4 | 2 | 16 | Week 2 |
| /templates page + 2-min screen recording | 5 | 2 | 20 | Week 2–3 |
| Publish "How Handoff Works" page | 4 | 1 | 20 | Week 2–3 |
| Self-serve signup + API key + free tier | 5 | 3 | 15 | Month 1 |
| n8n on_call_end trigger + WhatsApp alert | 4 | 3 | 12 | Month 1–2 |
| Freshworks Marketplace listing | 4 | 2 | 16 | Month 1–2 |

---

## 🔗 Sources Verified

| Source | What I Checked |
|--------|---------------|
| vocallabs.ai | Every button, URL probe (/signup /login /register /app /dashboard /pricing /templates /flows /demo), page source |
| github.com/Vocallabsai | 4 repos — vocalflow (forks/PRs), n8n-nodes-vocallabs (README, operations), vocal-sdk |
| blogs.vocallabs.ai | Canonical tags via Ctrl+U on multiple posts |
| retellai.com | Signed up, full dashboard access, pricing page, docs |
| bolna.ai | Homepage, pricing, feature comparison |
| docs.retellai.com | Transfer call API, full public documentation |
| n8n.io | Community nodes directory search for "voice" |
| freshworks.com/apps | Marketplace search for voice AI tools |
| developers.facebook.com | WhatsApp Business API trigger documentation |

---

## 🗂️ Repository Structure

```
vocallabs-ai-product-analysis/
├── README.md                                   ← This file
└── Product_Teardown_Vocallabs_Aryan_Patel.pdf  ← Full teardown report with all screenshots embedded
```

---

*Prepared by: Aryan Patel · Product Intern Assignment · Vocallabs.ai · May 2026*
