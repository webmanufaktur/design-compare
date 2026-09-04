> Todoist: DES: Plakatradar-Landingpage als index.html umsetzen (muse) — see .plans/plakatradar-landingpage-muse.md

*Plan-only note: this file describes the work; the deliverable is `index.html` in the repo root, not this file.*

## Goal

One self-contained `index.html` in the repo root implementing the Plakatradar landing page per design-briefing.md v1.0 (§4–§10), fixed stack HTML + Tailwind CDN + Alpine.js + Inter 400/500/600, German copy, light mode, 360–1440 px.

## Current state

Repo contains only `design-briefing.md`, `prompt.md`, `README.md`, `.plans/` — no `index.html` yet. Everything is built from scratch; the briefing is the sole normative source.

## Plan — phased outline (single file: `index.html`)

**(a) Skeleton, head, CDN includes** — grounding: §1, §6, §7.6, §9

- `<!doctype html>` `lang="de"`, viewport meta, `<title>`, meta description in German.
- Head: Google Fonts Inter `wght@400;500;600` + preconnect; Tailwind via `<script src="https://cdn.tailwindcss.com"></script>`; Alpine.js CDN (`defer`); htmx omitted (only interactions: hamburger + scrolled header, Alpine covers both — MAY per §9).
- Inline `tailwind.config` registering exact hexes from §6/§7 (brand `#6D28D9`/`#5B21B6`/`#F5F3FF`, zinc x10, status pairs x5, pin swatches x8, shadows sm/md/lg, font Inter). No `:root` CSS custom-properties block.
- Global `<style>`: `html { scroll-behavior: smooth }`, `scroll-margin-top` on anchor sections, `focus-visible` ring (`outline: 2px solid #6D28D9; outline-offset: 2px`) page-wide.
- Empty two-element section shells for all 9 sections in page-map order (§4): outer = background + vertical padding, inner = `max-w-[1152px] mx-auto px-6 md:px-8`.

**(b) Header + hero + map teaser** — grounding: §5.1, §5.2, §8.1, §8.2, §8.3, §8.6, §3

- Header sticky; wordmark = inline SVG pin glyph `#6D28D9` + „Plakatradar" (18/600); nav „Funktionen · Ablauf · Stimmen" fixed order (14/500, `#52525B`, hover `#18181B`); CTA „Kostenlos starten" in secondary style (§6.6 rule 2); Alpine `x-data` for hamburger panel (radius-lg, shadow-lg, ≥44px targets, closes on link/outside/X) + `@scroll.window` scrolled state (border `#E4E4E7` + shadow-sm).
- Hero: eyebrow (12/600, `#6D28D9`, tracking 0.08em, one style page-wide), H1 60/600 → 40 mobile, subline 18 max 2 lines, button pair „Kostenlos starten" (filled primary) + „So funktioniert's" (secondary, `href="#ablauf"`). Two-column ≥768px, stacked below.
- Map teaser: single inline SVG ~560x420 desktop / ≥300px mobile; base `#FAFAFA`, minor streets 2px `#E4E4E7`, major 4–6px `#D4D4D8`, blocks `#F4F4F5`; 8 dots one per pin swatch (10–12px, 2px white ring); 2 teardrop status pins `#DC2626`/`#D97706`; stats chip pill (white, shadow-sm, German Musterstadt text). No tiles/attribution/compass/scale. Pin pulse cut unless trivial.

**(c) Testimonial strip + 3-step process** — grounding: §5.3, §5.4, §8.8, §2

- Band bg `#FAFAFA`, `id="stimmen"`; 3 cards (quote 16 `#3F3F46` text-pretty, attribution 14/500 `#18181B` „Vorname, Teamkontext", avatar initial 40px circle `#F5F3FF`/`#6D28D9`, no photos). Civic-neutral, du-form, no superlatives.
- Process `id="ablauf"`: 3 numbered steps with feature-card tokens — 1 Pin setzen, 2 Status pflegen, 3 Überblick behalten; icon + title + 1–2 sentences each.

**(d) Features grid + status lifecycle** — grounding: §5.5, §5.6, §8.4, §8.5, §2, §3

- Features `id="funktionen"`: 6 cards (Karte & Pins, Status & Flags, Pin-Farben pro Mitglied, Umkreis-Ansicht, Offline-PWA, Zahlen & Auswertung). Icon tiles 48px `#F5F3FF` radius-md, inline stroke SVGs `#6D28D9`. Grid 3/2/1, gap 24, hover border `#D4D4D8` + shadow-sm ≤200ms.
- Lifecycle: all 5 real badges per §8.5 (separate badges, dot 6px + 12/600 label, py-1 px-3, pill, §6.3 pairs); mandatory combo „Gestohlen" + „Anzeige erstattet" + recommended „Beschädigt" + „Entfernt" as badge rows (8px gap, wrap, never merged); short model explanation. Presentation: 2–3 fictional „Plakat-Eintrag" sample cards reusing feature-card tokens.

**(e) Stats strip + final CTA + footer** — grounding: §5.7, §5.8, §5.9, §8.7, §8.9, §8.10, §3

- Stats band bg `#FAFAFA`: exactly 4 fixed values, German formatting — 12.480 / 1.270 / 38 / 4 Minuten. Value 32/600 `#18181B`, label 14/500 `#52525B`; 2→4 cols at 768px. No count-up.
- Final CTA: panel bg `#F5F3FF`, radius-lg, padding 48–64px; claim „Jedes Plakat. Ein Pin. Eine Karte." as H2 verbatim, 1 support line (free, du-form), „Kostenlos starten" filled primary, optional „So funktioniert's" text link.
- Footer: bg `#FAFAFA`, border-t `#E4E4E7`; wordmark + 1 sentence (14 `#52525B`), nav anchors, „Impressum · Datenschutz" → `#`, „© 2026 Plakatradar" (12, `#71717A`).

**(f) Validation pass** — grounding: §10 (all 16 items)
After (e): 1. 9 sections in order (DOM check). 2. fixed strings verbatim via grep; „Plakatwache" nowhere. 3. all ~30 hexes verbatim, no extras beyond white. 4. one filled primary per view; header secondary. 5. lifecycle 3+2+combo. 6. fiction (Musterstadt, attribution format, no real refs). 7. stats verbatim, no comparisons. 8. light mode only (`prefers-color-scheme` = 0 hits). 9. Inter 400/500/600, type scale, 4px grid. 10. keyboard tab-through. 11. pin hexes only inside teaser SVG. 12. map abstract. 13. responsive 360–1440, no h-scrollbar. 14. text-balance/pretty + consistent eyebrow. 15. two-element pattern + 1152px + one gap. 16. single index.html, only Tailwind+Alpine CDN scripts. Method: open index.html directly in browser, devtools responsive mode + keyboard pass + greps. Tailwind CDN production-notice is accepted, not a defect.

## Out of scope

No dark mode, no pricing, no second file, no build step, no htmx, no CSS custom-properties block, no animations beyond free MAY, no real map/party/person/brand references, no changes to design-briefing.md.

## Risks

Tailwind CDN console notice (accepted). Hero/final-CTA primaries must never share a viewport (holds by construction on a 9-section page; check in (f)-4). Free microcopy must follow §3 tone (German, du-form, no superlatives).
