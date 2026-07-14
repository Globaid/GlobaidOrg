<div align="center">

# 🌍 Globaid

### Citizen coordination for disasters — and everyday neighbourhood mutual aid

**Bottom-up · Transparent · Offline-first · Free for people**

[🌐 Open the app — globaid.org](https://globaid.org) · [🔓 Open data (API)](https://globaid.org/api/public) · [💬 Contact](mailto:hola@globaid.org)

> *Globaid is the app we want **everyone** to install, but that we hope **no one** will **ever** have to use.*

</div>

---

## 📑 Table of contents

1. [Why Globaid exists](#-why-globaid-exists)
2. [The idea and the intention](#-the-idea-and-the-intention)
3. [The real problems it solves](#-the-real-problems-it-solves)
4. [What Globaid does (features)](#-what-globaid-does-features)
5. [What makes it different](#-what-makes-it-different)
6. [Technical architecture](#-technical-architecture)
7. [How it was built](#-how-it-was-built)
8. [Challenges and decisions](#-challenges-and-decisions)
9. [Sustainability model](#-sustainability-model)
10. [Privacy and ethics](#-privacy-and-ethics)
11. [Current status and roadmap](#-current-status-and-roadmap)
12. [How to collaborate](#-how-to-collaborate)
13. [Contact](#-contact)

---

## 🌊 Why Globaid exists

In **October 2024**, a flash flood (*DANA*) devastated the **l'Horta Sud** region, in **Valencia, Spain**. There were hundreds of victims, entire towns buried in mud (Paiporta, Catarroja, Aldaia…) and, in the first hours, a tragic **lack of coordination**: warnings came too late and the institutional response was overwhelmed.

But something extraordinary happened: **communities saved themselves**. Thousands of volunteers arrived on foot with shovels and boots, neighbours opened their homes, food and water were shared, garages were pumped out house by house. An immense wave of solidarity.

That solidarity collided with chaos:

- **No one knew what was really needed** on each street, at each moment.
- **Donations piled up** in warehouses without reaching families; clothes and food expired.
- **Hoaxes** (bodies in garages, fake WhatsApp chains) mixed with useful information.
- People went **missing** for days, and elderly people were left alone and isolated.

**Globaid was born from this.** To coordinate, organize and inform that people-power from the very first minute. To **help those who help**.

---

## 💡 The idea and the intention

A **citizen-led, bottom-up layer** that fills the gap left by both institutional tools (top-down, slow) and WhatsApp groups (chaotic, unstructured).

Three non-negotiable commitments:

- **Free for people, always.** Help is never charged for.
- **Radical transparency.** Globaid **never holds money**: it routes each donation to a trusted organization and lets you trace every euro.
- **Works offline.** Truly offline-first, because in a disaster the network is the first thing to fail.

And a discipline of scope: **it is not a social network**. We don't compete with Nextdoor or an infinite feed. The focus is **community resilience**, not socializing.

---

## 🧩 The real problems it solves

These are the *jobs-to-be-done* Globaid tackles head-on, drawn from the analysis of the DANA:

| Real problem in the DANA | Globaid's answer |
|---|---|
| Nobody knew what was needed on each street | **Live needs map** with AI triage (category, urgency, phase) |
| Uncoordinated volunteers | **Offers and matching**: who can help, where and with what |
| Donations that never arrived | **Transparency ledger**: donor → NGO → purchase → delivery → confirmed receipt |
| Hoaxes mixed with useful info | **Anti-hoax board**: coordinators mark info as CONFIRMED or DEBUNKED, with its source |
| No one knew who was safe | **"I'm safe"**: one-tap safety check-in |
| Isolated vulnerable people | **Vulnerable-people registry** (opt-in, with consent), ready *before* disaster strikes |
| Missing people | **Report and search for missing people** |
| Communications down | **Offline-first** + **connectivity points** (WiFi/Starlink islands) on the map |
| The app is forgotten between disasters | **Peace mode**: everyday neighbourhood mutual aid keeps the trust network alive |

---

## 🛠️ What Globaid does (features)

### In an emergency
- **Live needs map** by urgency, with disaster **phase** intelligence.
- **Ask for help** in natural language: **Claude AI** detects category, urgency, whether it's for someone else and whether a vulnerable person is affected. You can **attach a photo**.
- **Offer help** (volunteer, resource or donation) with **AI matching** that suggests who to help nearby.
- **Full request lifecycle**: claim → *on the way* → *delivered* → **confirmed by the recipient** ("I'll take it").
- **Task-linked chat**: private messaging tied to each need to coordinate the delivery.
- **"I'm safe"**: everyone marks themselves safe or asks for help; coordinators instantly see who needs help.
- **Anti-hoax board**: verified updates; coordinators mark information as **CONFIRMED / DEBUNKED** with its source.
- **Push alerts**: reach the phone **even with the app closed** (evacuations, water points, debunks).
- **Help / logistics points**: water, food, charging, **WiFi/connectivity**, shelter, drop-off point, medical care.
- **Missing people**: report and search.
- **Emergency phone numbers + AI safety tips** per disaster type.
- **Offline tool kit**: flashlight, SOS light, siren, compass, my location, CPR metronome, first-aid guide, SOS message.
- **Directions** to any need or point (opens maps).

### Everyday (peace mode)
- **Neighbourhood communities** for mutual aid and preparedness.
- **Join by link or QR** (drives the network effect).
- **Peace → emergency bridge**: when disaster hits, the community **switches to emergency mode in one tap**, keeping its neighbours, trust and resources.
- **Vulnerable-people registry** (opt-in, with consent) — visible only to coordinators; built *before* disaster strikes.

### Trust & transparency
- **Transparency ledger**: every donation traced in 5 steps — donor → partner NGO (tax receipt) → purchase → house-by-house delivery → **confirmed receipt**. Globaid **never holds the money**.
- **Public transparency page** per area (shareable, no login) + **open JSON API** (B2G / press).
- **Needs corroboration**: cross-verification ("N confirmations") raises trust and curbs hoaxes.
- **Trust & reputation** from real, verifiable actions — vouches, levels and badges (Participant → Verified → Trusted neighbour → Verified coordinator) + **report/flag**.

### Coordination & AI
- **AI**: triage, matching and translation (real-time, both languages) via a secure server-side proxy.
- **Automatic event detection** (e.g. earthquakes via public feeds) → **one-tap activation** of a zone.
- **Coordinator panel**: zone situation, needs by type, phase anticipation, donation management.
- **AI social-post draft** to mobilize help on social media.
- **Admin panel**: manage the catalog of trusted NGOs and assign which one receives each event's or region's donations.
- **Aggregate analytics** for coordinators — zones, needs, coverage, donations — with **no individual tracking**.

### Everywhere
- **Bilingual ES/EN** with device autodetection.
- **Installable PWA**, **offline-first** (works with no connection), and **accessibility** (text-size control, high contrast).
- **Progressive identity**: viewing requires nothing; acting requires a passwordless email **magic link**.
- **Safe demo mode**: a sandbox with example data (two disasters, two communities) to try everything without touching anything real.

---

## ⭐ What makes it different

| | Institutional tools (ArcGIS, D4H…) | WhatsApp/Telegram groups | **Globaid** |
|---|---|---|---|
| Approach | Top-down | Chaotic | **Structured bottom-up** |
| Installation | Complex | None | **None (PWA)** |
| Offline | No | No | **Yes, offline-first** |
| Donation transparency | Opaque | None | **Traced, public, verifiable** |
| Anti-hoax | — | The problem | **Verification with source** |
| Between disasters | Goes dark | Goes dark | **Peace mode keeps the network** |

---

## 🏗️ Technical architecture

A deliberately **simple and resilient** design: no framework, no build step, no client dependencies. Everything runs on an old phone, offline.

```
┌───────────────────────────────────────────────────────────┐
│  PWA — HTML + CSS + JS (ES modules), no build              │
│  • IndexedDB  → everything works offline                  │
│  • Service Worker → cached app shell + push               │
│  • MapLibre + OpenStreetMap (map) · offline QR            │
└───────────────┬───────────────────────────────────────────┘
                │ progressive enhancement (if online)
┌───────────────▼───────────────────────────────────────────┐
│  Supabase — Postgres + RLS + Realtime + Auth (magic link) │
│  Sync with a persistent offline queue                     │
└───────────────┬───────────────────────────────────────────┘
                │ serverless functions
┌───────────────▼───────────────────────────────────────────┐
│  AI (Claude): triage · matching · translation             │
│  Web Push (VAPID) · Open data API · Open Graph cards      │
└───────────────────────────────────────────────────────────┘
```

**Stack:** vanilla PWA (ES modules, IndexedDB, Service Worker), [MapLibre GL](https://maplibre.org), offline QR, [Supabase](https://supabase.com) (Postgres + RLS + Realtime + Auth), serverless functions on [Vercel](https://vercel.com), and the [Claude API](https://www.anthropic.com) (Anthropic) for triage, matching and translation.

**Design principles:**
- *Local-first*: the UI never waits on the network.
- *Progressive enhancement*: with no backend, the app is still useful.
- *One engine, many profiles*: flood, earthquake and community share primitives (needs, offers, trust), at different intensities.
- *Security*: only a public *publishable key* ships in the client; secret keys live only in server environment variables; access is enforced by database Row-Level Security.

---

## 🚧 How it was built

Globaid grew **incrementally and verified at every step** — from prior research (the DANA and the landscape of existing tools) to a complete product. This is the real journey:

**1 · Foundations (MVP)** — the universal engine and the core screens.
- Bilingual ES/EN with device autodetection.
- Guided user guide.
- Multi-context model: events (each disaster) + communities.
- Real map (OpenStreetMap / MapLibre) with peace mode.
- Opt-in vulnerable-people registry.
- Real Claude AI for triage.

**2 · Core platform (Sprints 1–6).**
- AI to 100%: matching + translation on the same secure proxy.
- Real multi-user backend (Supabase) with offline sync and a persistent queue.
- Real identity & communication (passwordless email magic link).
- Real donations + partner fiscal entity, fully traced end-to-end.
- Automatic event detection + admin mode.
- Resilience and polish (local-first boot, robustness).

**3 · UX depth (interaction improvements).**
- Need detail screen with full status timeline.
- Share a specific request.
- View-on-map + pin → detail.
- Two-tab map (needs / help).
- Emergency-phone board + AI tips.
- Visible trust & badges + content reporting.
- Improved footer; offer help with location.

**4 · Identity & coordination.**
- Magic-link sign-in (Supabase Auth).
- Needs corroboration (cross-verification).
- Missing-person reporting and search.
- Manual assignment ("I'll take it").

**5 · Detection & outreach.**
- Automatic event detection (USGS) with one-tap activation.
- AI-generated social-media draft.

**6 · Product phase (Sprints 7–14).**

| # | Delivered |
|---|---|
| 7 | Event trust (anti-fake) |
| 8 | "I'm safe" + anti-hoax board |
| 9 | Push alerts (Web Push / PWA) |
| 10 | Living communities (join by QR + peace→emergency bridge) |
| 11 | Field robustness (photos, logistics points, offline status) |
| 12 | Public transparency + open API (B2G) |
| 13 | Analytics for coordinators |
| 14 | SEO + share cards (Open Graph) |

Every step was **verified in a demo environment** (without polluting real data) and shipped to production with automatic deployment.

---

## 🧗 Challenges and decisions

- **Real offline, not a brochure.** Instead of promising Bluetooth *mesh* (unrealistic), we bet on **offline-first + connectivity islands** (each antenna with internet is a sync point). Robust and honest.
- **Transparency without holding money.** Globaid never touches the funds: it routes to an NGO that issues the tax receipt, and the ledger traces every step. This avoids the biggest reputational and legal risk.
- **Anti-hoax without censorship.** Information is not deleted: coordinators **label** it (confirmed/debunked) with its source, so the truth stands out over the noise.
- **Privacy of sensitive data.** The vulnerable-people registry and check-ins are never publicly exposed (strict RLS; the open API includes no personal data).
- **Zero friction.** A PWA with no mandatory install and progressive identity.
- **The "valley" between disasters.** **Peace mode** solves the app dying when there's no emergency: it builds, in calm, the three assets a disaster makes impossible to create in time — **trust, a capabilities map, and a vulnerable-people registry**.

---

## 💶 Sustainability model

**Free for people. Always.** Sustainability comes from those who can afford it:

- **B2G** (government): live situational awareness, analytics and open data for emergency management.
- **B2B / foundations**: coordination tools for NGOs and large donors.
- **Public / EU funding**: resilience, civil protection, social innovation.
- **Voluntary micro-support** (never the donations to victims, which go entirely to the NGO).

The **open API** and radical transparency aren't just ethics: they're the product institutions need and can pay for.

---

## 🔒 Privacy and ethics

- **Minimal personal data**, gathered with consent (vulnerable registry is opt-in).
- Sensitive data (vulnerable registry, safety check-ins) is **never publicly readable**.
- The **public API** exposes only aggregates and non-personal data.
- **No third-party cookies or individual tracking** in the analytics.

---

## 🗺️ Current status and roadmap

**Today:** a complete app deployed at [globaid.org](https://globaid.org), with a real backend, real AI, push, communities, public transparency and analytics. Ready for a **pilot with real users**.

**Next steps:** explainer video, safe social sharing, real OTP/SMS fallback, a field pilot in Valencia with neighbourhood associations, setting up the partner NGO for donations, and a legal review.

---

## 🤝 How to collaborate

Globaid is looking for allies. If you're an **NGO, city council, neighbourhood association, civil protection body, foundation or volunteer**, you can help by:

- **Piloting** the app in your community or municipality.
- Being the **partner organization** that channels donations (with tax receipts).
- Contributing **field knowledge** (emergency management, volunteering).
- **Spreading the word.**

---

## 📬 Contact

- **Web:** [globaid.org](https://globaid.org)
- **Email:** [hola@globaid.org](mailto:hola@globaid.org)
- **Open data / API:** [globaid.org/api/public](https://globaid.org/api/public)

<div align="center">

---

*Built from Valencia, in memory of the 2024 DANA flood.* 🦇

**Globaid — to help those who help.**

</div>


*Built from Valencia, in memory of the 2024 DANA flood.* 🦇

**Globaid — to help those who help.**

</div>
