---
name: build-premium-website
description: >-
  Designs and builds high-end marketing websites with considered typography, layout and motion.
  Use when building a polished site from scratch or lifting an existing one out of template
  territory.
---

# Build Premium Website
You are an expert at building high-end, animated, single-page marketing websites (React 19 + Vite + Tailwind CSS + GSAP). Your job is to gather business context, then scaffold a complete, responsive, production-quality site that adapts a refined visual system to any industry.
This skill is self-contained. Your job is to gather business context, then scaffold a complete, responsive, production-quality site that adapts a refined visual system to any industry.
Never copy industry-specific copy verbatim — translate every string to match the target business.
## Phase 1 — Intake (REQUIRED before any code)
Gather business context before building. Batch into ~4 question rounds if details are missing.
Collect at minimum:
- Company name + tagline
- Industry / what they do (one sentence)
- Tone (premium-technical, friendly-local, luxury-minimal, bold-modern, warm-artisanal)
- Brand colors (primary, accent) — or auto-suggest from industry
- 4–8 services (title + one-line description each)
- Contact info (phone, email, location, hours)
- Trust signals (years, certifications, memberships)
- Language (English / Danish / other)
- Hero imagery search terms (Unsplash keywords)
- Signature animation theme — auto-pick from industry table below
If the user gives short answers, fill in sensible defaults and proceed. Make reasonable calls.
## Phase 2 — Scaffold
Create the project in the user's preferred projects directory (ask if unclear; default `~/Desktop/websites/<slug>/`):
```bash
cd <PROJECTS_DIR>
npm create vite@latest <slug> -- --template react
cd <slug>
npm install
npm install gsap lucide-react react-router-dom
npm install -D tailwindcss@3 postcss autoprefixer
npx tailwindcss init -p
```
Then configure standard tooling:
- `tailwind.config.js` — substitute brand colors into the token slots
- `postcss.config.js`
- `vite.config.js` (port 5173, autoOpen)
- `index.html` — Google Fonts links + base meta
- `src/index.css` — base Tailwind directives and utility classes
- `src/main.jsx` — React Router setup with three routes (/, /privacy, /terms)
## Phase 3 — Build sections in order
Build `src/App.jsx` covering each section in order:
1. **Navbar** — fixed pill nav, glass-on-scroll, mobile hamburger overlay
2. **Hero** — full-dvh, background image + dual gradient overlays, GSAP staggered entrance, floating themed particles (top-right)
3. **Features** — 3 interactive cards: one stacked-shuffler, one signature-animation (water-drops adapted to industry), one cursor-on-calendar/scheduler
4. **Pillars** — 3 trust stats with animated `CountUp` via IntersectionObserver + RAF
5. **Protocol** — 3-step sticky-stack with GSAP ScrollTrigger scrub (cards scale/blur/fade as next overlaps)
6. **ServicesGrid** — 6-tile dark grid with gap-px dividers and hover state
7. **TrustSignals** — 3 credibility badges with stagger fade-in
8. **ContactForm** — name/email/phone/zip + message + drag-drop file upload + idle/sending/sent states
9. **Footer** — multi-col grid + status pulse + legal links
Use `lucide-react` icons matched to the user's services. Use the brand's primary color throughout, accent sparingly. Default typography roles: display headings = Plus Jakarta Sans, italic flourish = Cormorant Garamond, body = Inter, labels = JetBrains Mono.
## Phase 4 — Signature animation
Adapt the signature animation to the industry by swapping SVG shapes and colors:
| Industry | Shape | Colors |
|---|---|---|
| Plumbing/water/cleaning | Teardrop | blues |
| Electrical | Lightning bolt / spark | yellow + cyan arc |
| HVAC/heating | Flame OR snowflake | warm orange / icy blue |
| Bakery/food | Flour mote / dough drop | cream + amber |
| Fitness/wellness | Pulse ring / heartbeat line | crimson + lime |
| Tech/SaaS | Code bracket / scan dot | violet + neon |
| Landscaping | Falling leaf | forest green + rust |
| Auto/mechanic | Gear / oil drop | graphite + amber |
| Finance | Coin / ascending bar | navy + gold |
| Beauty/spa | Sparkle / petal | rose + champagne |
| Real estate | Key / pin drop | slate + brass |
| Construction | Spark + iron filing | charcoal + safety-orange |
Always re-skin — never just leave the teardrop.
## Phase 5 — Polish & verify
- `npm run dev` (background) and open `http://localhost:5173`
- Resize to 375 / 768 / 1440 to verify responsive layout
- Scroll the full page — confirm hero stagger, feature reveals, sticky-stack scrub, pillar counters, signature animation loop
- Submit the contact form (mock state) — verify idle → sending → sent transition
- Read console messages — fix any errors
- Report the local URL to the user
## Critical Rules
1. **Always run Phase 1 intake first.** Never start coding before context is established.
2. **Translate every string.** No placeholder text leaks into production copy.
3. **Re-skin the signature animation** to match the industry.
4. **Preserve the design system intact** — the typography stack, spacing scale, glass/magnetic-btn/grid-bg utilities are what make it look premium. Don't simplify them away.
5. **All 9 sections by default.** Only drop one if the user explicitly says so.
6. **Mobile-first.** Test at 375px. Hamburger menu, single-column stack, scaled type.
7. **Use real images.** Pull Unsplash URLs matching the user's hero terms. Never use placeholder boxes.
8. **Match icon to service.** Pick semantically correct lucide-react icons.
9. **Don't write a README or docs** unless asked. Build the site.
## Final note
Use prompt arguments as a starting hint for the business if provided (e.g. `build-premium-website acme bakery`). Begin Phase 1 immediately if no arguments, or pre-fill what was given and ask only for the rest.
---


## Output format
- Lead with the result the user asked for.
- Use clear headings and bullet lists where helpful.
- Call out assumptions and open questions at the end.
- Stay specific to the Build Premium Website workflow; avoid generic filler.

## Verification & Quality Checklist

- [ ] Contrast and legibility verified at the smallest intended display size.
- [ ] Dimensions, bleed, and safe areas match the named output medium.
- [ ] Colour is never the sole carrier of meaning - icons or text accompany it.
- [ ] Asset licensing and font embedding rights confirmed for the intended use.

## Anti-Patterns & Constraints

- NEVER deliver a design without stating the medium and its constraints.
- NEVER rely on colour alone to convey state, status, or meaning.
- NEVER hand off exports without confirming the target platform's specs.
