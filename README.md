# Bresolin SRL – Website Project

E-commerce website for **BRESOLIN SRL** (Italy), a used & reconditioned auto parts dealer based in Bassano del Grappa.

## Status: Work in Progress 🚧

**Last worked on:** June 2026  
**Stack:** Single-file HTML/CSS/JS — no framework, no build step, runs directly in browser.

---

## What's done

- Full dark-themed e-commerce layout (similar to the Wix reference at `project4532.wixsite.com/libreson`)
- Hero section with animated stat counters (40+ years, 50k+ parts, 98% satisfaction, 30+ countries)
- Product catalog with 12 items across 5 categories + live filter tabs
- Each product card: stock Pexels image, price, "BUY NOW" button (Stripe placeholders), "HAVE A QUESTION?" WhatsApp link
- "How to Buy" 4-step section
- Contact form section (UI only — not wired to backend yet)
- Footer with real company legal data
- WhatsApp floating button → `https://wa.me/390424566666`
- Scroll-reveal animations (IntersectionObserver)
- Lazy image loading
- Fully responsive (mobile/tablet/desktop)

## What's PENDING

### 1. Stripe Payment Links (PRIORITY)
All "BUY NOW" buttons currently have placeholder links (`#stripe-XXX`).  
Once you have a Stripe account, create Payment Links for each product and replace in `index.html` around **line 678–800** in the `products` array:

```js
{ id:1, ..., stripeLink:"https://buy.stripe.com/XXXXXXXX" },
{ id:2, ..., stripeLink:"https://buy.stripe.com/XXXXXXXX" },
// etc.
```

**Stripe registration:** Go to stripe.com → use company info (BRESOLIN SRL, P.IVA 00870960242). No domain needed to sign up — use `www.bresolin.com` as website field. You are NOT affiliated with that domain personally; you're building for the company.

### 2. Product Images (IN PROGRESS — stopped here)
Some Pexels stock photos don't match the product. Need to replace with accurate car-parts photos.  
Specifically `id:2` (Axle Parts, Pexels ID 3807568) was showing a fruit bowl — wrong image.

**To fix:** Edit the `img:` fields in the products array (lines ~680–800). Use Pexels URLs in format:  
`https://images.pexels.com/photos/{ID}/pexels-photo-{ID}.jpeg?auto=compress&cs=tinysrgb&w=700`

Search pexels.com for: "car axle", "driveshaft", "suspension strut", "turbocharger", "wing mirror", etc.

### 3. Hosting
The site currently runs locally only. To publish:
- **Free option:** [Netlify](https://netlify.com) → drag & drop the `bresolin-ricambi` folder → get a free `.netlify.app` URL
- **Custom domain:** Buy `brresolinricambi.com` or similar (~€12/yr) and point it to Netlify
- WHOIS privacy (~€2/yr) keeps personal info hidden from public WHOIS

### 4. Contact Form Backend (optional)
The form sends nothing currently. Options:
- [Formspree](https://formspree.io) — free, add `action="https://formspree.io/f/XXXXX"` to `<form>`
- Or wire to a Node.js/Express backend

---

## Company Info (real data from Visura Ordinaria)

| Field | Value |
|-------|-------|
| Name | BRESOLIN SRL |
| P.IVA | 00870960242 |
| REA | VI-180154 |
| Address | Via Luigi Di Gallo 17, 36061 Bassano del Grappa (VI), Italy |
| Phone | +39 0424 566666 |
| Founded | 1980 (website shows "Since 2016" — that's the online presence date) |

---

## Run locally

Just open `index.html` in your browser (double-click it in Windows Explorer).  
All images are external (Pexels CDN) so you need internet access for them to load.

Or run the Node static server (if you have the `web test` Claude Code project):
```
# Port 4500 — configured in web test/.claude/launch.json
```

---

## Product categories

| Category key | Display name |
|---|---|
| `engine` | Engine & Drivetrain |
| `body` | Body & Exterior |
| `interior` | Interior |
| `suspension` | Suspension |
| `lighting` | Lighting |

---

## Fonts & colors

- **Fonts:** Barlow Condensed (headings), Barlow (body), DM Mono (prices/codes) — Google Fonts
- **Colors:** `--black:#06060a`, `--charcoal:#0d0d1c`, `--red:#c0392b`, `--white:#ededf8`
