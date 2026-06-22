# PrideNomad Foundation — Matt Handoff
**Prepared by:** Marco (PrideNomad)  
**Date:** 2026-06-21  
**Status:** Ready to deploy

---

## What's been built

The full foundation site is in this folder. All pages are self-contained HTML — no build step, no framework, no dependencies.

```
Foundation/
├── index.html          ← Home (updated — see changes below)
├── about/index.html    ← About the Foundation (NEW)
├── guides/index.html   ← Guides index (NEW)
├── research/index.html ← Research methodology (NEW)
├── privacy/index.html  ← Privacy policy (NEW)
├── contact/index.html  ← Contact page (NEW)
└── thank-you/index.html ← Post-subscribe confirmation (NEW)
```

---

## The one thing you need to do before deploying

**Wire the Beehiiv form.** Everything else is done.

### Steps:
1. Log into Beehiiv → go to **Settings → Newsletter → Embed**
2. Copy the embed code — it will look like this:
   ```html
   <iframe src="https://embeds.beehiiv.com/YOUR-PUBLICATION-ID"
     data-test-id="beehiiv-embed"
     height="52" frameborder="0" scrolling="no"
     style="width:100%; border:0; background:transparent;">
   </iframe>
   ```
3. Open `index.html` and find this comment block (line ~641):
   ```
   <!-- PASTE BEEHIIV EMBED IFRAME HERE — Matt, see instructions above -->
   ```
4. Replace the `<form class="subscribe-form-placeholder"...>` block with the Beehiiv iframe
5. **Optional but recommended:** In Beehiiv embed settings, set the redirect URL to `https://pridenomadFoundation.com/thank-you` so users stay on the foundation domain after subscribing

### Ad Grant compliance — why this matters:
The form must keep users on **pridenomadFoundation.com** after they subscribe. The Beehiiv embed iframe does this by default — the success message shows inside the iframe, the parent page doesn't navigate. If Beehiiv redirects the parent page after subscribe, set the redirect to `/thank-you` (same domain) in Beehiiv settings.

---

## What changed in index.html

Two compliance fixes:
- **Nav "Subscribe free"** — was linking to `pridenomad.beehiiv.com/subscribe` (external). Now links to `#subscribe` (scrolls to form on page).
- **Hero CTA button** — same fix. Was external, now `#subscribe`.

Newsletter section improvements (McGarry-optimized):
- Headline changed from generic "Free. Weekly. Real." → "Where can you actually build the life you want?" (answers the avatar's actual question)
- Subhead now tells them what's inside: "one destination analyzed across legal rights, safety, community, healthcare, and cost of living"
- Social proof line added: "7,500+ queer adults reading · Free, always · Nonprofit — we don't sell your data"
- Privacy copy updated to human tone: "your inbox is not a product"

---

## Deployment

Deploy the entire `Foundation/` folder to Cloudflare Pages (or wherever the pridenomadFoundation.com domain is pointed).

The folder structure maps directly to URL paths:
- `Foundation/index.html` → `pridenomadFoundation.com/`
- `Foundation/about/index.html` → `pridenomadFoundation.com/about`
- `Foundation/guides/index.html` → `pridenomadFoundation.com/guides`
- etc.

**Domain:** `pridenomadFoundation.com` (confirm canonical with Ken — the `<link rel="canonical">` tags are already set to this domain across all pages)

---

## Email addresses referenced in pages

The contact page references these addresses — confirm they exist or update before go-live:
- `hello@pridenomadFoundation.com` — general inquiries
- `partnerships@pridenomadFoundation.com` — partnership inquiries
- `research@pridenomadFoundation.com` — research corrections
- `privacy@pridenomadFoundation.com` — privacy/data requests

If these don't exist yet, simplest fix: forward them all to Ken's email via Cloudflare Email Routing.

---

## What's NOT in scope for this handoff

The guide cards in `guides/index.html` link to individual guide pages (e.g. `/lgbtq-travel/portugal`) — those pages don't exist yet. The links are correct for when they do. For Google Ads resubmission, the six guide URLs listed are placeholders until the actual content pages are built.

---

## Questions?

Route through North → Marco.
