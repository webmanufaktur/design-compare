# Design Briefing — Plakatradar Landing Page

**Version 1.0 · 2026-08-31 · Deliverable: one responsive landing page (light mode)**

---

## 1. About this briefing

This document governs a design comparison: several models receive exactly this briefing, and each delivers one landing page. To keep the comparison fair, a simple contract applies:

**Fixed (MUST):** tech stack — semantic HTML, Tailwind CSS via CDN, JS only via Alpine.js and/or htmx (both via CDN); no build step, no other frameworks — plus brand (§3), color system (§6), design tokens (§7), component specification (§8), and section structure plus content requirements (§4–§5). Values are adopted verbatim, down to the exact hex code.

**Free (MAY):** inner layout, illustration style, microcopy beyond the fixed strings in §3, subtle animations, and the choice between Alpine.js and htmx per interaction.

**Deliverable:** one responsive landing page for desktop and mobile (360 px to 1440 px), light mode only, as a single self-contained `index.html` (Tailwind via CDN `<script>`, Alpine/htmx via CDN — no build step). The tokens from §7 are applied unchanged (px values as px or rem, hex values 1:1).

**Content rules:** all content is fictional. No real parties, people, places, brands, or map services — the fiction framework is defined in §2 and §5. Before delivery, run through the self-check list in §10. All page copy is written in German at delivery time (the product's language); this briefing specifies it in English, with every fixed German string quoted. Numbers use German formatting at delivery (12.480, not 12,480).

---

## 2. Product

### What Plakatradar is

Plakatradar is a map app for managing campaign posters. Teams drop a pin for every poster they hang — with GPS position, address, and up to 5 photos — and keep the state up to date across the whole lifecycle: hanging, damaged, stolen, removed. The app is deliberately multi-party: it serves campaign teams of all parties equally and takes no political position.

### Problem & audience

Posters are usually coordinated today through lists, spreadsheets, and messenger groups. Oversight gets lost: which poster hangs where? What has been reported, what was replaced? And when posters are damaged or stolen, there is no documented basis for filing a police report. The audience is campaign teams and local chapters — from small volunteer teams to district organizations — distributing hundreds of posters across a region.

### Platform & positioning

- Mobile-first progressive web app (PWA), offline-capable in the field.
- Access behind login; registration is free.
- This briefing covers the landing page, not the app — the landing page promotes the app; the app itself is not part of the deliverable.

### Core workflows

1. **Pin a poster:** capture GPS on site, add the address, attach up to 5 photos. Every team member has their own pin color, so the map shows at a glance who was active where.
2. **Maintain status:** every pin carries a status — „Aktiv“, „Gestohlen“, or „Beschädigt“ (active / stolen / damaged) — plus two independent flags: „Anzeige erstattet“ (reported to police) and „Entfernt“ (removed). Details in §5.6.
3. **Map & nearby:** all team pins on one map; a "nearby" view shows which posters hang in the immediate area while canvassing.
4. **Numbers:** per-team evaluation: how many posters are up, what the status distribution looks like, how many incidents are documented.

> Note for implementation: the landing page explains these workflows as a process (§5.4), as features (§5.5), and as the status model (§5.6) — it does not imitate app screens.

---

## 3. Brand

### Name & claim (fixed)

| Element | Value |
| --- | --- |
| Name | `Plakatradar` |
| Claim | „Jedes Plakat. Ein Pin. Eine Karte.“ |
| Rejected alternative | `Plakatwache` — „Deine Plakate im Blick — bei jeder Witterung.“ (deliberately rejected: reads like surveillance and weather-proofing instead of a tool) |

Name and claim are used verbatim — the claim in the hero and in the final CTA block. The rejected name appears nowhere on the page.

### Tone of voice

Matter-of-fact and pragmatic, told from field experience, civic-neutral. German copy, informal du-form. Short main clauses, active voice, concrete numbers instead of adjectives. Plakatradar is politically neutral: the landing page addresses all teams equally and judges no party, no side, no "right way" to run a campaign. The example copy below stays in German as quoted, with the problem glossed in English.

| Do | Don't |
| --- | --- |
| „Pin setze ich in 20 Sekunden.“ (gloss: "I set a pin in 20 seconds.") | „Blitzschnell pinnen — die schnellste Plakat-App aller Zeiten!“ (superlative: "the fastest poster app of all time!") |
| „Für Wahlkampfteams aller Parteien.“ (gloss: "For campaign teams of all parties.") | „Damit dein Wahlkampf gewinnt.“ (political siding / outcome promise: "so your campaign wins") |
| „340 Plakate im Blick, jede Meldung dokumentiert.“ (gloss: "340 posters in view, every report documented.") | „Nie wieder Plakatchaos!!!“ (vague, exclamation overload: "never again poster chaos!!!") |
| „Meldung dokumentiert — Grundlage für eine Anzeige.“ (gloss: "Report documented — basis for a police report.") | „Empörender Vandalismus im großen Stil!“ (dramatization: "outrageous vandalism on a grand scale!") |
| du-form, short main clauses, concrete verbs | formal Sie-form, noun-heavy style, buzzwords ("seamless", "revolutionary") |

### Glossary: fixed UI strings (EN → DE)

These strings are written exactly as shown — no translation variants, no rephrasing:

| EN | DE (fixed) | Usage |
| --- | --- | --- |
| Poster entry | „Plakat-Eintrag“ | term for a pin/record in copy |
| Active | „Aktiv“ | status label |
| Stolen | „Gestohlen“ | status label |
| Damaged | „Beschädigt“ | status label |
| Reported to police | „Anzeige erstattet“ | flag |
| Removed | „Entfernt“ | flag |
| Start for free | „Kostenlos starten“ | primary CTA |
| How it works | „So funktioniert's“ | secondary CTA / process anchor |
| Features · Process · Voices | „Funktionen · Ablauf · Stimmen“ | navigation (fixed order) |
| Imprint · Privacy | „Impressum · Datenschutz“ | footer |
| Pin | „Pin“ | noun, der Pin (not "marker", not "drop") |
| Map | „Karte“ | die Karte (not "map", not "radar view") |

---

## 4. Landing page strategy

**Primary conversion goal:** „Kostenlos starten“ (start for free) — registration for the app. Exactly one filled primary CTA per view (usage rules §6.6); every other button uses the secondary style (§8.3).

**Secondary goal:** „So funktioniert's“ (how it works) — jump to the process section so prospects understand the product in 3 steps.

**Argument line:** time saved and documentation certainty for teams coordinating posters across a region — with evidentiary value when incidents occur. Neutral in tone, concrete in numbers, no superlatives (§3).

**Page map (9 sections, fixed order):**

| # | Section | Goal |
| --- | --- | --- |
| 1 | Header | orientation + permanent access to registration |
| 2 | Hero incl. map teaser | understand in seconds: what, for whom, first CTA |
| 3 | Testimonial strip | trust from field practice, civic-neutral |
| 4 | How it works | 3 steps to your own pin |
| 5 | Features grid | full scope at a glance |
| 6 | Status lifecycle | differentiator: status and flag model |
| 7 | Stats strip | show scale (fictional placeholders) |
| 8 | Final CTA | close with claim + primary CTA |
| 9 | Footer | navigation, legal, brand close |

---

## 5. UX: section by section

For each of the 9 page-map sections: position, headline intent (message, **not final copy** — headlines are written by the implementing model in the §3 tone), content requirements, components used (§8), and communication goal.

### 5.1 Header

- **Position:** page-map section 1; sticky on top, above all other sections.
- **Headline intent:** none — the header carries the wordmark, anchor navigation, and the CTA slot.
- **Content:** wordmark „Plakatradar“ (§8.1), the 3 nav anchors „Funktionen · Ablauf · Stimmen“ (fixed order), button „Kostenlos starten“ in the secondary style (so the filled primary CTA stays unique per view, §6.6). Mobile: hamburger with panel (§8.1).
- **Components:** header/nav (§8.1), secondary button (§8.3).
- **Communication goal:** orientation and permanent, unobtrusive access to registration.

### 5.2 Hero incl. map teaser

- **Position:** page-map section 2; first full-viewport impression below the header.
- **Headline intent:** anchor in one sentence what Plakatradar does and for whom — posters managed as pins on a map.
- **Content:** eyebrow (audience context line, civic-neutral), H1 close to the claim, 1–2 subline sentences (benefit: oversight + documentation), button pair „Kostenlos starten“ (primary, filled) + „So funktioniert’s“ (secondary, scroll anchor to §5.4). Next to or below it, the map teaser (§8.6) with approx. 8 pins in the pin colors + 2 status pins and a Musterstadt reference.
- **Fiction rules:** the map shows an abstracted „Musterstadt und Region“ — no real places, no real tiles.
- **Components:** hero (§8.2), map teaser (§8.6), buttons (§8.3), eyebrow (§7.1).
- **Communication goal:** understand in under 5 seconds: what is it, who is it for, what is the first step.

### 5.3 Testimonial strip

- **Position:** page-map section 3, directly after the hero; anchor target of „Stimmen“ (voices).
- **Headline intent:** briefly signal that teams in the field already use the tool.
- **Content:** 2–3 short quotes (1–2 sentences each) from everyday team work. Civic-neutral, fictional attributions in the format “First name, team context”, e.g. „Katharina, Wahlkampfteam Nordstadt“ or „Jonas, Kreisverband Musterstadt-Land“. No party names, no real people, no political attributes inside the quote.
- **Components:** testimonial card (§8.8) in a 2–3-column strip.
- **Communication goal:** trust through field voices — without political coloring.

### 5.4 How it works (process)

- **Position:** page-map section 4; scroll target of the secondary CTA; anchor target of „Ablauf“ (process).
- **Headline intent:** defuse the “how much effort is this?” objection with 3 numbered steps.
- **Content:** step 1 “Pin a poster” (location + photos in seconds), step 2 “Maintain status” („Aktiv“ / „Gestohlen“ / „Beschädigt“ + flags), step 3 “Keep the overview” (map, nearby, numbers). Per step: icon or mini illustration, title, 1–2 sentences. Optional cross-reference to the status model (§5.6).
- **Components:** step layout based on the feature card (§8.4) or a dedicated process layout with the same tokens.
- **Communication goal:** prove simplicity — 3 steps, start immediately.

### 5.5 Features grid

- **Position:** page-map section 5, after the process; anchor target of „Funktionen“ (features).
- **Headline intent:** show the full scope compactly — everything necessary covered, nothing superfluous.
- **Content:** 6 feature cards from the core workflows (§2): map & pins (GPS + address + photos), status & flags, pin colors per team member, nearby view, offline PWA (works in the field without reception), numbers & reporting. Per card: icon, title, 1–2 sentences.
- **Components:** feature card (§8.4) in a grid: 3 columns (desktop), 2 (tablet), 1 (mobile).
- **Communication goal:** completeness and field capability — a tool, not a toy.

### 5.6 Status lifecycle (differentiator)

- **Position:** page-map section 6; the content core of the page.
- **Headline intent:** show that Plakatradar documents incidents cleanly — this is what sets the product apart from plain map tools.
- **Content (mandatory, complete):**
  - All **3 statuses** visible as status badges: „Aktiv“, „Gestohlen“, „Beschädigt“ (§8.5).
  - Both **flags** visible: „Anzeige erstattet“, „Entfernt“.
  - At least **one combination** shown, e.g. „Gestohlen“ + „Anzeige erstattet“.
  - A short explanation of the model: the status describes the poster’s condition; the flags are independent additional information. „Entfernt“ documents the takedown, „Anzeige erstattet“ the documented evidence for the authorities.
  - Presentation form is free (timeline, sample „Plakat-Eintrag“ records, etc.) — but with real badges per §8.5.
- **Components:** status badge incl. flag combinations (§8.5), optionally card/list layouts with the same tokens.
- **Communication goal:** documentation certainty — every incident leaves traces, numbers, and evidence.

### 5.7 Stats strip

- **Position:** page-map section 7; compact band between lifecycle and final CTA.
- **Headline intent:** prove scale and activity — soberly, without superlatives.
- **Content:** 3–4 metrics with **realistic placeholder magnitudes**, fixed as: “12.480 posters pinned”, “1.270 reports documented”, “38 cities and regions”, “4 minutes from sign-up to the first pin”. German number formatting at delivery (12.480, not 12,480). The values are fictional placeholders and are adopted as given — no “× times more” claims, no comparisons with other products.
- **Components:** stats strip (§8.7).
- **Communication goal:** the product is in the field — concrete scale, matter-of-fact.

### 5.8 Final CTA

- **Position:** page-map section 8; last action block before the footer.
- **Headline intent:** close with the claim and frame registration as the final simple step.
- **Content:** claim „Jedes Plakat. Ein Pin. Eine Karte.“, 1 support sentence (free, du-form), „Kostenlos starten“ as the filled primary CTA. Optional „So funktioniert’s“ as a secondary link (unfilled).
- **Components:** CTA block (§8.9), buttons (§8.3).
- **Communication goal:** complete the conversion — without pressure, with one clear next step.

### 5.9 Footer

- **Position:** page-map section 9; page close.
- **Headline intent:** none — close and legal.
- **Content:** wordmark, nav anchors „Funktionen · Ablauf · Stimmen“, „Impressum · Datenschutz“ (placeholder links `#`), copyright line “© 2026 Plakatradar”.
- **Components:** footer (§8.10).
- **Communication goal:** serious, clear close; all links are anchors or marked placeholders.

---

## 6. Color system (light mode only)

All hex values are adopted **1:1**. The page base background is white `#FFFFFF`; sections can set themselves apart with the surface roles from §6.5.

### 6.1 Brand (violet)

| Role | Hex | Usage |
| --- | --- | --- |
| Brand / primary | `#6D28D9` | primary CTA fill, links, eyebrow text, icon accents, `focus-visible` ring |
| Brand dark | `#5B21B6` | primary CTA hover, strong accents |
| Brand tint | `#F5F3FF` | soft backgrounds (CTA panel, icon tiles), avatar circles |

### 6.2 Neutrals (zinc, 10 steps)

| Hex | Equivalent | Usage |
| --- | --- | --- |
| `#FAFAFA` | zinc-50 | set-off section surfaces, map teaser base, footer |
| `#F4F4F5` | zinc-100 | card surfaces, city blocks in the teaser, „Entfernt“ background |
| `#E4E4E7` | zinc-200 | borders, dividers, minor streets in the teaser |
| `#D4D4D8` | zinc-300 | stronger borders, major streets in the teaser, placeholders, secondary border |
| `#A1A1AA` | zinc-400 | disabled text, hover border (never body text) |
| `#71717A` | zinc-500 | secondary text on white (short text, labels, copyright) |
| `#52525B` | zinc-600 | secondary body text, „Entfernt“ foreground |
| `#3F3F46` | zinc-700 | secondary icons, meta text |
| `#27272A` | zinc-800 | dark heading variant |
| `#18181B` | zinc-900 | primary text, H1–H3, stat values |

### 6.3 Semantic pairs (status & flags)

Foreground = text (and optional border) color, background = tint surface. These colors are reserved **exclusively** for status badges and status pins (usage rules §6.6).

| Meaning | Foreground | Background |
| --- | --- | --- |
| Active | `#059669` | `#ECFDF5` |
| Stolen | `#DC2626` | `#FEF2F2` |
| Damaged | `#D97706` | `#FFFBEB` |
| Reported to police | `#2563EB` | `#EFF6FF` |
| Removed | `#52525B` | `#F4F4F5` |

### 6.4 Pin swatches (8, map/teaser only)

| Pin | Hex | Pin | Hex |
| --- | --- | --- | --- |
| Pin 1 | `#DC2626` | Pin 5 | `#0D9488` |
| Pin 2 | `#EA580C` | Pin 6 | `#2563EB` |
| Pin 3 | `#CA8A04` | Pin 7 | `#7C3AED` |
| Pin 4 | `#16A34A` | Pin 8 | `#DB2777` |

Pin colors appear **only** as pins on the map / in the map teaser — never as text, button, border, or decorative color.

### 6.5 Surface roles

| Role | Hex | Example |
| --- | --- | --- |
| Page background | `#FFFFFF` | main surface of all sections |
| Set-off section | `#FAFAFA` | stats strip, testimonial band, footer |
| Brand tint surface | `#F5F3FF` | final CTA block, icon tiles |
| Map teaser | `#FAFAFA` + `#E4E4E7` / `#D4D4D8` | base surface + streets |

### 6.6 Usage rules

1. **Contrast (WCAG AA, 4.5:1):** body text only in `#18181B`, `#3F3F46`, or `#52525B` on `#FFFFFF` / `#FAFAFA` / `#F4F4F5` / `#F5F3FF`. `#71717A` and lighter only for short secondary text with checked contrast, never for body text. White type only on `#6D28D9` (primary CTA, > 4.5:1).
2. **Exactly one primary CTA per view:** the filled violet button (`#6D28D9`) appears exactly once per visible viewport (hero or final CTA block). The header CTA is therefore always in the secondary style (§8.1, §8.3).
3. **Semantics never as decoration:** `#059669`, `#DC2626`, `#D97706`, `#2563EB` appear only in status badges and as status pins — never as borders, illustration colors, section accents, or hover colors.
4. **Pin swatches only on the map** (§6.4).
5. **No dark mode**, no `prefers-color-scheme` branch, no scheme switching.

---

## 7. Design tokens

All values are fixed in px; rem is based on a 16 px root. Everything maps directly to Tailwind utilities (e.g. spacing 16 → `p-4`, radius 12 → `rounded-xl`).

### 7.1 Typography — Inter, weights 400 / 500 / 600

| Token | px / rem | Weight | Usage |
| --- | --- | --- | --- |
| `text-60` | 60 / 3.75 | 600 | H1 desktop |
| `text-40` | 40 / 2.5 | 600 | H1 mobile, H2 desktop |
| `text-32` | 32 / 2 | 600 | H2 mobile |
| `text-24` | 24 / 1.5 | 600 | H3 |
| `text-18` | 18 / 1.125 | 400/500/600 | lead, hero subline, wordmark, card titles |
| `text-16` | 16 / 1 | 400 | body text (base) |
| `text-14` | 14 / 0.875 | 400/500 | secondary text, labels, testimonial attribution |
| `text-12` | 12 / 0.75 | 500/600 | eyebrow, badge text, micro labels |

Headings in `#18181B`, body text `#3F3F46`/`#52525B`. Line heights: headings approx. 1.1–1.2, body text approx. 1.6. Headings may use `text-balance`, paragraphs `text-pretty`. Eyebrow as the heading-group opener: 12 px, weight 600, letter-spacing approx. 0.08 em, color `#6D28D9`, uppercase optional — one style page-wide.

### 7.2 Spacing (4-px grid)

| Token | px | rem | Typical usage |
| --- | --- | --- | --- |
| `space-1` | 4 | 0.25 | icon gaps, badge padding (vertical) |
| `space-2` | 8 | 0.5 | inline gaps, badge gap, dot offset |
| `space-3` | 12 | 0.75 | label gaps, compact padding |
| `space-4` | 16 | 1 | small button padding, base block gap |
| `space-6` | 24 | 1.5 | card padding, page-wide grid gap |
| `space-8` | 32 | 2 | group gaps, desktop container horizontal padding |
| `space-12` | 48 | 3 | mobile section padding, compact panel padding |
| `space-16` | 64 | 4 | desktop section padding (compact) |
| `space-24` | 96 | 6 | desktop section padding (standard) |

**Two-element section pattern (all sections):** the outer element carries the background and vertical padding; the inner element carries the container max-width (1152 px), centering, and horizontal padding — so content edges align while scrolling.

### 7.3 Radii

| Token | Value | Usage |
| --- | --- | --- |
| `radius-sm` | 6 px | inputs, small surfaces |
| `radius-md` | 12 px | buttons, icon tiles |
| `radius-lg` | 20 px | cards, panels, map teaser |
| `radius-pill` | 9999 px | badges, chips, stats chip |

### 7.4 Shadows (zinc-tinted)

| Token | Definition | Usage |
| --- | --- | --- |
| `shadow-sm` | `0 1px 2px rgba(24, 24, 27, 0.06)` | header (scrolled), cards, stats chip |
| `shadow-md` | `0 4px 12px rgba(24, 24, 27, 0.08)` | map teaser |
| `shadow-lg` | `0 12px 32px rgba(24, 24, 27, 0.12)` | mobile menu panel |

### 7.5 Layout & breakpoints

| Token | Value | Usage |
| --- | --- | --- |
| Breakpoint `sm` | 640 px | 1 → 2 columns |
| Breakpoint `md` | 768 px | mobile menu → navigation, hero two-column |
| Breakpoint `lg` | 1024 px | feature grid 2 → 3 columns |
| Breakpoint `xl` | 1280 px | full container width |
| Container | max 1152 px, centered | horizontal padding 24 px (mobile) / 32 px (desktop) |
| Grid gap | 24 px | one gap value for all multi-column sections |

### 7.6 Optional CSS custom properties

Optional for the implementation — the values are binding, the mechanism is free:

```css
:root {
  --color-brand: #6D28D9;
  --color-brand-strong: #5B21B6;
  --color-brand-tint: #F5F3FF;
  --color-zinc-50: #FAFAFA;  --color-zinc-100: #F4F4F5;
  --color-zinc-200: #E4E4E7; --color-zinc-300: #D4D4D8;
  --color-zinc-400: #A1A1AA; --color-zinc-500: #71717A;
  --color-zinc-600: #52525B; --color-zinc-700: #3F3F46;
  --color-zinc-800: #27272A; --color-zinc-900: #18181B;
  --color-status-active: #059669;   --color-status-active-bg: #ECFDF5;
  --color-status-stolen: #DC2626;   --color-status-stolen-bg: #FEF2F2;
  --color-status-damaged: #D97706;  --color-status-damaged-bg: #FFFBEB;
  --color-status-reported: #2563EB; --color-status-reported-bg: #EFF6FF;
  --color-status-removed: #52525B;  --color-status-removed-bg: #F4F4F5;
  --pin-1: #DC2626; --pin-2: #EA580C; --pin-3: #CA8A04; --pin-4: #16A34A;
  --pin-5: #0D9488; --pin-6: #2563EB; --pin-7: #7C3AED; --pin-8: #DB2777;
  --radius-sm: 6px; --radius-md: 12px; --radius-lg: 20px; --radius-pill: 9999px;
  --shadow-sm: 0 1px 2px rgba(24, 24, 27, 0.06);
  --shadow-md: 0 4px 12px rgba(24, 24, 27, 0.08);
  --shadow-lg: 0 12px 32px rgba(24, 24, 27, 0.12);
  --container-max: 1152px;
  --font-sans: "Inter", system-ui, sans-serif;
}
```

---

## 8. Components

Per component: anatomy (parts), variants, states. All dimensions and colors from §6–§7.

### 8.1 Header / nav

- **Anatomy:** wordmark left (pin glyph in `#6D28D9` + text “Plakatradar”, 18/600), nav center („Funktionen · Ablauf · Stimmen“, 14/500, `#52525B`, hover `#18181B` consistent with footer links; active section optionally `#6D28D9`), CTA slot right with „Kostenlos starten“.
- **Variants:** desktop (nav visible) / mobile (hamburger, touch target ≥ 44 × 44 px).
- **States:**
  - **Top:** background `#FFFFFF`, no border.
  - **Scrolled (sticky):** background `#FFFFFF` (optionally translucent + blur), bottom border `#E4E4E7`, `shadow-sm`.
  - **Mobile menu:** the hamburger opens a simple panel (dropdown/overlay, `radius-lg`, `shadow-lg`) with the 3 nav links stacked + CTA; closes on link tap, outside tap, or X. No mega menu, no submenus.

### 8.2 Hero

- **Anatomy:** eyebrow, H1 (60/600 desktop, 40/600 mobile), subline (18, max 2 lines), button pair (primary + secondary, 16 px gap), map teaser.
- **Variants:** desktop two-column (text left, teaser right, vertically centered) / mobile stacked (text, then teaser).
- **States:** static; subtle entrance animation optional (MAY).

### 8.3 Buttons

- **Anatomy:** label (16/600 at md, 14/600 at sm), optional icon, radius `radius-md` (12 px). Sizes: md = 12 px vertical / 24 px horizontal (height ≈ 48 px), sm = 8 px / 16 px (height ≈ 36 px). Max 2 sizes page-wide.
- **Variants:**
  - **Primary:** background `#6D28D9`, text `#FFFFFF`. Exactly one per view (§6.6).
  - **Secondary (outline):** background `#FFFFFF`, 1 px border `#D4D4D8`, text `#18181B`. For the header CTA and all further actions.
- **States:**

| State | Primary | Secondary |
| --- | --- | --- |
| Default | bg `#6D28D9`, text `#FFFFFF` | bg `#FFFFFF`, border `#D4D4D8` |
| Hover | bg `#5B21B6` | border `#A1A1AA`, bg `#FAFAFA` |
| Focus-visible | 2 px outline `#6D28D9`, offset 2 px | identical |
| Active | bg `#5B21B6` (same as hover) | border `#71717A` |
| Disabled | 50% opacity, no hover, `cursor: not-allowed` | identical |

### 8.4 Feature card

- **Anatomy:** icon tile (48 × 48 px, bg `#F5F3FF`, `radius-md`, 24 px stroke icon in `#6D28D9`), title (18/600, `#18181B`), text (16/400, `#52525B`, 2–3 lines). Padding 24 px.
- **Variants:** grid 3/2/1 columns, gap 24 px; surface `#FFFFFF`, 1 px border `#E4E4E7`, `radius-lg` (20 px).
- **States:** default / hover: border `#D4D4D8` + `shadow-sm` (transition ≤ 200 ms, no lift required).

### 8.5 Status badge

- **Anatomy:** optional status dot (6 px circle in the foreground color) + label (12/600), padding 4 px vertical / 12 px horizontal, `radius-pill`, background = tint, text = foreground color (§6.3).
- **Variants (all mandatory in the lifecycle section, §5.6):**

| Variant | Background | Foreground |
| --- | --- | --- |
| „Aktiv“ | `#ECFDF5` | `#059669` |
| „Gestohlen“ | `#FEF2F2` | `#DC2626` |
| „Beschädigt“ | `#FFFBEB` | `#D97706` |
| „Anzeige erstattet“ (flag) | `#EFF6FF` | `#2563EB` |
| „Entfernt“ (flag) | `#F4F4F5` | `#52525B` |

- **Flag combinations:** status + flags sit in a badge row with 8 px gap, wrapping allowed. Mandatory example: „Gestohlen“ + „Anzeige erstattet“; additionally sensible: „Beschädigt“ + „Entfernt“. Flags stay visually separate badges — do not merge them into one chip.
- **States:** purely presentational, no interaction.

### 8.6 Map teaser

- **Anatomy:** container `radius-lg` (20 px), border `#E4E4E7`, `shadow-md`; inside it an **abstracted, stylized street map**: base surface `#FAFAFA`, minor streets as 2-px lines `#E4E4E7`, major streets 4–6 px `#D4D4D8`, optional city blocks `#F4F4F5`. On top approx. **8 user pins** — one per pin swatch (`#DC2626`, `#EA580C`, `#CA8A04`, `#16A34A`, `#0D9488`, `#2563EB`, `#7C3AED`, `#DB2777`), each a 10–12 px dot with a 2-px white ring — plus **2 status pins** in `#DC2626` („Gestohlen“) and `#D97706` („Beschädigt“) in a distinguishable teardrop/marker shape. Optional stats chip (bg `#FFFFFF`, `radius-pill`, `shadow-sm`, 12–14 px, e.g. “248 pins in Musterstadt”).
- **Hard rules:** no real map services, no tiles, no attribution, no hint of login-gated UI, no imitation of real map-provider elements (compass, scale, layer switcher). The map is pure illustration (SVG/CSS), fictional, with a Musterstadt reference in the chip text.
- **Variants:** hero size (desktop approx. 560 × 420 px) / mobile full width, height ≥ 300 px.
- **States:** static; subtle pin pulsing optional (MAY).

### 8.7 Stats strip

- **Anatomy:** 3–4 stat items, each value (32/600 desktop, `#18181B`) + label (14/500, `#52525B`).
- **Variants:** band with bg `#FAFAFA`, vertical padding 48–64 px; 2 columns below `md` (768 px), 4 columns from `md`; optional dividers `#E4E4E7`.
- **States:** static; count-up animation optional (MAY, never layout shift).

### 8.8 Testimonial card

- **Anatomy:** quote (16/400, `#3F3F46`, `text-pretty`), attribution (14/500, `#18181B`) in the format “First name, team context”; optional avatar initial (40 px circle, bg `#F5F3FF`, text 14/600 `#6D28D9`) — **no photos** (fictional people).
- **Variants:** card (bg `#FFFFFF`, border `#E4E4E7`, `radius-lg`, `shadow-sm`), 2–3 cards in a strip with gap 24 px.
- **States:** static.

### 8.9 CTA block

- **Anatomy:** panel (bg `#F5F3FF`, `radius-lg`, padding 48–64 px) with H2 (32–40/600), 1 support line (16, `#52525B`), „Kostenlos starten“ (primary). Optional „So funktioniert’s“ as a text link (secondary, unfilled).
- **Variants:** panel inside the container (standard) or full-bleed band — both allowed (MAY).
- **States:** as buttons (§8.3). Exactly one filled CTA per view.

### 8.10 Footer

- **Anatomy:** wordmark + 1 sentence (14, `#52525B`), nav anchors „Funktionen · Ablauf · Stimmen“, legal „Impressum · Datenschutz“ (placeholder links `#`, 14/500). Copyright line “© 2026 Plakatradar” (12, `#71717A`).
- **Variants:** bg `#FAFAFA`, top border `#E4E4E7`, padding 48–64 px.
- **States:** links hover to `#18181B` + `focus-visible` ring; otherwise static.

---

## 9. Fixed vs. free

| MUST (fixed) | MAY (free) |
| --- | --- |
| Name, claim, and all fixed strings from §3 verbatim | all other microcopy in the §3 tone |
| All hex values from §6 1:1; the only additional color is `#FFFFFF` | illustration style of the street map (line work, block shapes) |
| Type scale, weights (400/500/600), spacing grid, radii, shadows (§7) | line heights within the defined range, icon library |
| 9 sections in page-map order (§4) | inner layout per section (columns, arrangement, hero teaser right or below) |
| Status lifecycle with all 3 statuses + both flags + at least 1 combination (§5.6) | presentation form of the lifecycle (timeline, sample „Plakat-Eintrag“ records) |
| Musterstadt reference, civic-neutral attributions, realistic placeholder numbers | concrete fictional names/contexts of the voices (format §5.3) |
| Exactly one filled primary CTA per view; header CTA secondary | position of the CTA panel (container or band, §8.9) |
| Light mode only | subtle animations (transitions ≤ 200 ms, never required) |
| `focus-visible` on all interactive elements | `text-balance` / `text-pretty` recommended, not checked |
| Two-element section pattern for all sections (§7.2) | section backgrounds from the surface roles (§6.5) |
| Stack: HTML + Tailwind CSS via CDN, JS only via Alpine.js/htmx — no build step, no other frameworks | which interactions use Alpine.js vs. htmx |
| Map teaser: abstract, approx. 8 pin colors + 2 status pins, no real tiles (§8.6) | pulsing animation, exact stats-chip text (format §8.6) |

Not allowed (NEVER): real parties, people, places, or brands; real map tiles or map services; dark mode; pricing sections; superlatives or political siding; deviation from the hex values.

---

## 10. Self-check (before delivery)

The implementing model runs this list before delivery; every item must be answerable with “met”:

1. [ ] All **9 sections** of the page map present, in the fixed order (§4).
2. [ ] All **fixed strings** set verbatim (§3): claim, CTAs, status labels, flags, nav, footer.
3. [ ] All **hex values** from §6 adopted unchanged; no additional colors except `#FFFFFF`.
4. [ ] **Exactly one** filled primary CTA per visible view; header CTA is secondary.
5. [ ] **Status lifecycle** shows „Aktiv“, „Gestohlen“, „Beschädigt“, „Anzeige erstattet“, „Entfernt“ — plus at least one combination (e.g. „Gestohlen“ + „Anzeige erstattet“).
6. [ ] Fiction held: Musterstadt reference, no real parties, people, places, brands; testimonial attributions in the “First name, team context” format.
7. [ ] Stats strip uses realistic placeholder magnitudes without comparison or competitive claims.
8. [ ] **Light mode only** — no dark-mode path, no scheme switching.
9. [ ] Inter with **400/500/600**; type scale (§7.1) and the 4-px spacing grid (§7.2) respected.
10. [ ] **`focus-visible`** on all links and buttons; keyboard focus order is sensible.
11. [ ] **Pin swatches** appear only on the map/teaser; **semantic status colors** not used as decoration.
12. [ ] Map teaser is abstract-stylized: no tiles, no attribution, no login UI.
13. [ ] Responsive from **360 px to 1440 px** without overflow, no horizontal scrollbar.
14. [ ] Headings carry `text-balance`, paragraphs `text-pretty` (recommended); eyebrow style consistent across all sections.
15. [ ] All sections follow the **two-element section pattern** (§7.2); container 1152 px, one grid gap page-wide.
16. [ ] **Stack respected:** single `index.html`, Tailwind CSS via CDN, JS only via Alpine.js/htmx (CDN) — no build step, no other frameworks.
