<div align="center">

# 🌍 Globaid

### Citizen coordination for disasters — and everyday neighbourhood mutual aid

**Bottom-up · Transparent · Offline-first · Free for people**

[🌐 globaid.org](https://globaid.org) · [📖 Help](https://globaid.org/) · [🔓 Open data (API)](https://globaid.org/api/public) · [💬 Contact](mailto:hola@globaid.org)

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
13. [Getting started (technical)](#-getting-started-technical)
14. [License and contact](#-license-and-contact)

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

From the analysis of the DANA (see [`docs/`](docs/)), these are the *jobs-to-be-done* Globaid tackles head-on:

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
- **Live map** of needs by urgency, with disaster **phase** intelligence.
- **Ask for help** in natural language: **Claude AI** detects category, urgency, whether it's for someone else and whether a vulnerable person is affected. You can **attach a photo**.
- **Offer help**: volunteer, resource or donation; suggests who to help nearby.
- **"I'm safe"**: everyone marks themselves safe or asks for help; coordinators instantly see who needs help.
- **Anti-hoax board**: verified updates; coordinators mark information as **CONFIRMED / DEBUNKED** with its source.
- **Push alerts**: reach the phone **even with the app closed** (evacuations, water points, debunks).
- **Help / logistics points**: water, food, charging, **WiFi/connectivity**, shelter, drop-off point, medical care.
- **Missing people**: report and search.
- **Emergency phone numbers + AI tips** per disaster type.
- **Offline tool kit**: flashlight, SOS light, siren, compass, my location, CPR metronome, first-aid guide, SOS message.

### Everyday (peace mode)
- **Neighbourhood communities** for mutual aid and preparedness.
- **Join by link or QR** (drives the network effect).
- **Peace → emergency bridge**: when disaster hits, the community **switches to emergency mode in one tap**, keeping its neighbours, trust and resources.

### Cross-cutting
- **Transparency**: traced donation ledger + shareable **public page** per area + **open API** (B2G/press).
- **Trust and reputation** from real actions (corroborations, vouches, badges).
- **Progressive identity**: viewing requires nothing; acting requires sign-in (email magic link).
- **Aggregate analytics** in the admin panel (no individual tracking).
- **Bilingual ES/EN** with autodetection; **installable** (PWA); **accessibility** (text-size control, high contrast).

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
│  PWA (app/) — HTML + CSS + JS (ES modules), no build       │
│  • IndexedDB  → everything works offline (db.js)          │
│  • Service Worker → cached app shell + push (sw.js)        │
│  • MapLibre + OpenStreetMap (map) · offline QR            │
└───────────────┬───────────────────────────────────────────┘
                │ progressive enhancement (if online)
┌───────────────▼───────────────────────────────────────────┐
│  Supabase — Postgres + RLS + Realtime + Auth (magic link) │
│  Sync with a persistent offline queue                     │
└───────────────┬───────────────────────────────────────────┘
                │ serverless functions (Vercel)
┌───────────────▼───────────────────────────────────────────┐
│  /api/ai      → secure proxy to Claude (triage, matching,  │
│                 translation, social draft, tips)           │
│  /api/push    → Web Push (VAPID) to subscribers           │
│  /api/public  → open JSON data (transparency / B2G)       │
│  /api/share   → per-area Open Graph cards (SEO / social)  │
└───────────────────────────────────────────────────────────┘
```

**Stack:**
- **Frontend:** vanilla PWA (ES modules), IndexedDB, Service Worker, MapLibre GL, [qrcode-generator](https://github.com/kazuhikoarase/qrcode-generator) (offline QR), Tabler icons.
- **Backend:** [Supabase](https://supabase.com) (Postgres, RLS, Realtime, Auth) — the client only ships the *publishable key*; secret keys live only in environment variables.
- **Serverless:** Node functions on Vercel for AI, push, open data and OG.
- **AI:** Claude API (Anthropic) — default model `claude-opus-4-8`; `claude-haiku-4-5` recommended for triage.
- **Offline-first:** instant local read/write; background sync with a persistent queue ("connectivity islands").

**Design principles:**
- *Local-first*: the UI never waits on the network.
- *Progressive enhancement*: with no backend, the app is still useful (demo/local).
- *One engine, many profiles*: flood, earthquake and community share primitives (needs, offers, trust), at different intensities.

---

## 🚧 How it was built

Globaid was built **incrementally and verified**, in sprints, starting from prior research (the DANA and the landscape of existing tools, in [`docs/`](docs/)).

**MVP + foundations:** ES/EN i18n, guided help, event/community model, real map, real Claude AI, Supabase multi-user backend, magic-link identity, traced donations + partner organization, automatic event detection (USGS) and admin mode, resilience and polish.

**Product phase (Sprints 7–14):**

| Sprint | Delivered |
|---|---|
| 7 | Event trust (anti-fake) |
| 8 | "I'm safe" + anti-hoax board |
| 9 | Push alerts (Web Push / PWA) |
| 10 | Living communities (join by QR + peace→emergency bridge) |
| 11 | Field robustness (photos, logistics points, offline status) |
| 12 | Public transparency + open API (B2G) |
| 13 | Analytics in the admin panel |
| 14 | SEO + share cards (Open Graph) |

Every sprint was **verified in a demo environment** (without polluting real data) and shipped to production with auto-deploy.

---

## 🧗 Challenges and decisions

- **Real offline, not a brochure.** Instead of promising Bluetooth *mesh* (unrealistic), we bet on **offline-first + connectivity islands** (each antenna with internet is a sync point). Robust and honest.
- **Transparency without holding money.** Globaid never touches the funds: it routes to an NGO that issues the tax receipt, and the ledger traces every step. This avoids the biggest reputational and legal risk.
- **Anti-hoax without censorship.** Information is not deleted: coordinators **label** it (confirmed/debunked) with its source, so the truth stands out over the noise.
- **Privacy of sensitive data.** The vulnerable-people registry and check-ins are never publicly exposed (strict RLS; the open API includes no personal data).
- **Zero friction.** A PWA with no mandatory install, progressive identity, and a build-free architecture anyone can deploy.
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
- **RLS** on Supabase; push subscriptions and check-ins are **not publicly readable**.
- The **public API** exposes only aggregates and non-personal data.
- **No third-party cookies or individual tracking** in the analytics.
- Privacy policy available in the app.

---

## 🗺️ Current status and roadmap

**Today:** a complete app deployed at [globaid.org](https://globaid.org), with a real backend (Supabase), real AI (Claude), push, communities, public transparency and analytics. Ready for a **pilot with real users**.

**Next steps:**
- Safe social sharing (aggregate text with no personal data) + explainer **video** on the landing page.
- Configurable social auto-posting (optional).
- Real OTP/SMS as a data-free fallback.
- Field pilot in Valencia with neighbourhood associations.
- Setting up the **partner NGO/entity** for donations.
- Legal review (privacy, data protection).

---

## 🤝 How to collaborate

Globaid is looking for allies. If you're an **NGO, city council, neighbourhood association, civil protection body, foundation or volunteer** (technical or not), you can help by:

- **Piloting** the app in your community or municipality.
- Being the **partner organization** that channels donations (with tax receipts).
- Contributing **field knowledge** (emergency management, volunteering).
- **Contributing** code, translations or documentation.
- **Spreading the word.**

📬 Write to us at **[hola@globaid.org](mailto:hola@globaid.org)**.

---

## ⚙️ Getting started (technical)

> Internal / legacy code name: **ResQ**. Domain and brand: **Globaid**.

### Run locally

No dependencies, no build. Just Node.js:

```bash
node server.mjs      # or: npm start
```

Open **http://localhost:5173**. With no backend configured, it runs in local/demo mode.

### Deploy (Vercel)

1. Import the repository at [vercel.com/new](https://vercel.com/new).
2. **Root Directory** = `app` · **Framework Preset** = `Other` · no *build command*.
3. Deploy. Every `push` to `main` deploys automatically.

### Environment variables (Vercel → Settings → Environment Variables)

| Variable | Purpose |
|---|---|
| `ANTHROPIC_API_KEY` | Claude AI (triage, matching, translation). **Required** for real AI. |
| `ANTHROPIC_MODEL` | Optional. Defaults to `claude-opus-4-8`; `claude-haiku-4-5` recommended. |
| `VAPID_PRIVATE_KEY` | Push alerts (the public key is in `config.js`). |
| `VAPID_SUBJECT` | Push contact, e.g. `mailto:privacy@globaid.org`. |
| `SUPABASE_SECRET_KEY` | Supabase *secret key* (reads/cleans push subscriptions; bypasses RLS). |

> Secret keys **never** go in the repository. The Supabase *publishable key* is public by design (security is enforced by RLS policies).

### Database (Supabase → SQL Editor)

Run the scripts in [`supabase/`](supabase/): `schema.sql` (base tables) and the per-feature ones: `orgs.sql`, `settings.sql`, `checkins.sql`, `push.sql`, `points.sql`, `allow-delete.sql`.

### Repo structure

```
app/            # the PWA (deploy root on Vercel)
  index.html    # shell + meta/SEO
  js/           # app.js, store.js, db.js, data.js, supabase.js, auth.js, i18n.js…
  api/          # serverless functions: ai, push, public, share
  css/ · vendor/ · icons/ · sw.js · manifest.webmanifest · og.svg
supabase/       # SQL schema and policies
docs/           # research, vision, MVP, roadmap, visibility plan
server.mjs      # static server for local development only
```

---

## 📄 License and contact

- **License:** MIT (see [`LICENSE`](LICENSE)).
- **Web:** [globaid.org](https://globaid.org)
- **Contact:** [hola@globaid.org](mailto:hola@globaid.org)
- **Documentation:** [`docs/`](docs/)

<div align="center">

---

*Built from Valencia, in memory of the 2024 DANA flood.* 🦇

**Globaid — to help those who help.**

</div>
