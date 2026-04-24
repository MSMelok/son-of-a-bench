# Son of a Bench — Coach Ammar Shaban

A modern, single-page Arabic landing site for online fitness coach **Ammar Shaban** and the SON OF A BENCH coaching team. Built with hand-written HTML, CSS, and a sprinkle of vanilla JavaScript — no framework, no build step, no dependencies.

> _"بسعى دايماً إن تجربة التدريب الأونلاين تكون متميزة و ممتعة و مليانة بالفايدة اللي يقدر يستخدمها المشترك بنفسه في باقي حياته، مش مجرد نتيجة في فترة من حياته."_
>
> — Coach Ammar's manifesto

---

## Live preview

> _Add your deployment URL here once published (GitHub Pages, Netlify, or Vercel — see [Deployment](#deployment) below)._

## About

This site presents the coaching offering in Egyptian Arabic with full right-to-left support, anchored in IBM Plex Sans Arabic typography. Every section funnels toward a single conversion goal: starting a WhatsApp conversation with Ammar. The visual identity is light editorial — warm cream backgrounds, crimson accents pulled from the brand logo, and bold display typography for the wordmark.

The site is intentionally **lead-generation focused**, not e-commerce. Visitors don't checkout — they tap "كلّمنى على واتساب" and start a real conversation.

## Screenshots

> _Add screenshots here once you've captured them (`/docs/screenshot-desktop.png`, `/docs/screenshot-mobile.png`)._

## Features

- **Single-page design** — Nine sections, one scroll, one conversion path
- **Right-to-left Arabic** — Native RTL layout using CSS logical properties; no separate stylesheet needed for direction
- **Mobile-first responsive** — Breakpoints at 980px and 640px with a hamburger nav, stacked layouts, and a thumb-friendly floating WhatsApp button
- **Pricing comparison** — Tabbed interface across three plan types (Full / Diet Only / Workout Only) and three durations (2 / 3 / 6 months) for both Golden and Silver tiers
- **Direct WhatsApp integration** — Sticky floating button plus six in-flow CTAs, all deep-linking to `wa.me/201009013820`
- **Accessible accordion FAQ** — Native `<details>` / `<summary>` elements; full keyboard support with zero JavaScript
- **Scroll-reveal animations** — IntersectionObserver-driven fade-ins with a `prefers-reduced-motion` fallback for accessibility
- **Lucide-style inline SVG icons** — No icon font, no extra HTTP requests, fully themeable via `currentColor`
- **Brand-anchored color system** — Eight CSS custom properties drive every accent, hover state, and gradient on the page

## Page sections

In display order (right-to-left scroll):

| # | Section | Purpose |
|---|---|---|
| 1 | Sticky navbar | Persistent navigation with primary WhatsApp CTA |
| 2 | Hero | Brand wordmark, manifesto quote, coach photo, primary CTAs |
| 3 | About the captain | Coaching philosophy and credentials |
| 4 | How it works | Four-step onboarding flow (DM → questionnaire → trial week → start) |
| 5 | Programs | Golden vs Silver comparison cards, highlighting the daily-vs-weekly difference |
| 6 | Pricing | Tabbed pricing tables for all 12 plan combinations |
| 7 | What's included | Eight feature cards covering custom programs, video tutorials, photo follow-up, and more |
| 8 | FAQ | Eight collapsible answers to common objections |
| 9 | Final CTA | Closing pitch, contact email, and social links |

## Tech stack

| Layer | Choice | Rationale |
|---|---|---|
| Markup | Hand-written semantic HTML5 | SEO-friendly, accessible by default |
| Styling | Vanilla CSS with custom properties | Whole design system retheme-able from a single `:root` block |
| Scripting | Vanilla JavaScript (~50 lines) | No framework needed for a brochure site |
| Typography | Google Fonts: IBM Plex Sans Arabic + Anton | Strong Arabic glyph coverage paired with an athletic Latin display face |
| Icons | Inline [Lucide](https://lucide.dev/)-style SVG | Zero external requests, scales infinitely, themeable |

## Project structure

```text
Coach-Ammar/
├── index.html                  # Single-page site (Arabic, RTL)
├── styles/
│   └── main.css                # Full design system (~700 lines)
├── scripts/
│   └── main.js                 # Mobile nav, pricing tabs, scroll reveal
├── assets/
│   ├── logo.png                # SON OF A BENCH brand mark
│   └── ammar.jpg               # Coach photo
├── Golden Price List.pdf-1.pdf # Source pricing reference (Golden tier)
├── Silver Price List.pdf       # Source pricing reference (Silver tier)
└── README.md                   # You are here
```

## Getting started

### Clone the repo

```bash
git clone https://github.com/YOUR-USERNAME/coach-ammar.git
cd coach-ammar
```

### Run locally

The simplest way is to double-click `index.html` and open it in your browser.

For the cleanest experience (correct relative paths, font loading, scroll behavior), serve it over a local HTTP server:

```bash
# Python 3
python -m http.server 8000

# Node.js (no install needed)
npx serve

# PHP
php -S localhost:8000
```

Then visit `http://localhost:8000`.

## Customization

### Brand colors

The entire color system lives in eight custom properties at the top of `styles/main.css`:

```css
:root {
  --red:       #E11D2A;   /* Primary brand color (CTAs, accents) */
  --red-deep:  #B8141F;   /* Hover and pressed state */
  --gold:      #C8941F;   /* Golden tier accent */
  --silver:    #8B95A1;   /* Silver tier accent */
  --cream:     #FAF7F2;   /* Page background */
  --cream-2:   #F3EFE6;   /* Alternate section background */
  --ink:       #0E0E0E;   /* Primary text */
  --muted:     #5B5B58;   /* Secondary text */
}
```

Change one value, the whole site retones. No find-and-replace needed.

### Coach photo

Replace `assets/ammar.jpg` with a new file of the same name. The hero frame uses a 4:5 aspect ratio with `object-position: center top` — anchor the subject's face near the top of the frame for best results.

### Pricing

Prices live inline in `index.html` inside the `#pricing` section. Each tier has three duration rows. To update, edit the `<span class="price">` values directly.

### WhatsApp number

The number `+201009013820` appears in seven places (six CTAs + the FAQ link). Find-and-replace `wa.me/201009013820` globally to update.

### Social links

The four social URLs and email link are in the `.socials` block of the final CTA section. Replace the `href` values directly.

### Add or remove sections

Each section is a self-contained `<section>` with its own `id`. To remove one, delete the section element and its corresponding entry in the navbar (`#navLinks`) and footer (`.footer__links`).

## Deployment

This is a static site — host it anywhere that serves files.

### GitHub Pages

1. Push the repo to GitHub
2. Go to **Settings → Pages**
3. Under **Source**, choose `Deploy from a branch`, then select `main` and `/ (root)`
4. Save — your site goes live at `https://YOUR-USERNAME.github.io/REPO-NAME` within a minute

### Netlify

The fastest path: drag-and-drop the project folder onto [app.netlify.com/drop](https://app.netlify.com/drop). Netlify gives you a public URL instantly and a custom-domain option in one click.

### Vercel

```bash
npm i -g vercel
vercel
```

Follow the CLI prompts. Vercel detects it as a static site automatically.

## Browser support

Tested and working in:

- Chrome / Edge (Chromium) — current and one previous version
- Firefox — current and one previous version
- Safari — current and one previous version
- Mobile Safari (iOS) and Chrome (Android) — current

Uses modern CSS (custom properties, logical properties, `aspect-ratio`, `backdrop-filter`) — no support for Internet Explorer or pre-2020 browsers, by design.

## About the coach

**Ammar Shaban** — Online fitness and nutrition coach based in Egypt.

| Channel | Link |
|---|---|
| WhatsApp | [+20 100 901 3820](https://wa.me/201009013820) |
| Email | [ammarshaban543211@gmail.com](mailto:ammarshaban543211@gmail.com) |
| Facebook | [Son of a Bench](https://www.facebook.com/p/Son-of-a-bench-100082108987872) |
| Instagram | [@son_ofabench](https://www.instagram.com/son_ofabench) |
| TikTok | [@sonofaaabench](https://www.tiktok.com/@sonofaaabench) |
| YouTube | [@Son-of-a-bench](https://www.youtube.com/@Son-of-a-bench) |

## Credits

- **Brand identity** — SON OF A BENCH Coaching Team
- **Typography** — [IBM Plex Sans Arabic](https://fonts.google.com/specimen/IBM+Plex+Sans+Arabic) and [Anton](https://fonts.google.com/specimen/Anton), both via Google Fonts
- **Icon style** — [Lucide](https://lucide.dev/), MIT-licensed line icons

## License

The HTML, CSS, and JavaScript scaffolding in this repository are freely reusable as a reference for building Arabic RTL coaching landing pages.

The brand assets — logo, photo of Ammar, copy, and pricing — belong to SON OF A BENCH and are **not** redistributable.

---

Built with care for someone who actually changes lives in the gym.
