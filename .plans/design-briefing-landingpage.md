# Implementation Plan: `design-briefing.md` for a Landing-Page Design Eval

- **Date:** 2026-08-30/31
- **Status:** Planned — ready for worker handoff
- **Todoist:** DES: Design-Briefing Plakatradar-Landingpage verfassen — see .plans/design-briefing-landingpage.md (id: `6hPhR4F7Q3RvQHPH`)

## Goal

Write a single self-contained design briefing (`/Users/fvh/Code/DesignTest/design-briefing.md`) for the landing page of a fictional multi-party election-poster map app, with a fully pinned design system (brand, colors, tokens, components) plus deliberately open execution — so multiple AI models can be handed the identical document and compared fairly.

*Plan-only note: this file describes the work; the deliverable is the briefing document itself, not app code.*

## Current state

`DesignTest/` contains only `README.md`, `.agents/`, and `.git/` — no `design-briefing.md` yet. The briefing is written from scratch.

## Brand decision

- Name: `Plakatradar` · Claim: „Jedes Plakat. Ein Pin. Eine Karte." (alternative `Plakatwache` listed as rejected option in the briefing)
- Tone: sachlich-pragmatisch, field-tested, civic-neutral. German, du-Form. Short sentences, active voice, no superlatives. Never takes a political side. Fixed UI strings: CTAs „Kostenlos starten" (primary) / „So funktioniert's" (secondary); status labels „Aktiv", „Gestohlen", „Beschädigt"; flags „Anzeige erstattet", „Entfernt"; nav „Funktionen · Ablauf · Stimmen"; footer „Impressum · Datenschutz".

## Briefing outline (10 sections)

1. Title + "About this briefing" — fairness contract (system fixed, execution free), deliverable: one responsive landing page, light mode, any stack, tokens applied verbatim
2. Product (what it is / problem & audience / platform positioning / core workflows) — fresh spec of a multi-party election-poster map tracker: pin posters (GPS + address, ≤5 photos), status lifecycle active/stolen/damaged + reported/removed flags, per-user pin colors, stats, nearby, offline PWA, app behind auth. NO references to the real existing app's UI (plakate.abelt.de / Plakatkarte).
3. Brand (name & claim / tone of voice with do-don't table / EN→DE glossary ~10 rows)
4. Landing page strategy (conversion goal primary „Kostenlos starten" / secondary „So funktioniert's"; 9-section page map: Header → Hero incl. map teaser → Testimonial strip → How it works → Features grid → Status lifecycle → Stats strip → Final CTA → Footer)
5. Section-by-section UX (9 H3 subsections: order, headline intent, content requirements, components used, communication goal)
6. Color system (light-only; ~30 hex values: violet brand #6D28D9/#5B21B6/#F5F3FF; zinc neutrals ×10 #FAFAFA…#18181B; semantic pairs active #059669/#ECFDF5, stolen #DC2626/#FEF2F2, damaged #D97706/#FFFBEB, reported #2563EB/#EFF6FF, removed #52525B/#F4F4F5; 8 pin swatches #DC2626 #EA580C #CA8A04 #16A34A #0D9488 #2563EB #7C3AED #DB2777; surface roles; usage rules WCAG AA, one primary per view, status hues reserved for status)
7. Design tokens (typography Inter 400/500/600, scale 12/14/16/18/24/32/40/60px; spacing 4px grid 4/8/12/16/24/32/48/64/96; radii 6/12/20/pill; shadows sm/md/lg; breakpoints 640/768/1024/1280, container 1152px, two-element section pattern)
8. Components (header/nav, hero, buttons with default/hover/focus-visible/disabled, feature card, status badge with flag combos, map teaser — abstract stylized map, no real tiles, ~8 pins + 2 semantic status pins, stats strip, testimonial card, CTA block, footer; each with anatomy/variants/states)
9. Fixed vs. free (MUST/MAY two-column table)
10. Self-check checklist for the evaluating model

## Execution

Worker writes the file in 3 passes + final grep verification (forbidden strings: plakate.abelt, Plakatkarte, PLK, 009ee0, Rotenburg, Wümme, Cloudflare, Leaflet, Geoapify — only deliberate Plakatwache mention allowed). Target 400–600 lines, trim above 650.

## Out of scope

No current-UI references, no dark mode, no pricing section, no tech-stack mandate beyond Tailwind-mappable px/rem tokens, no real parties/people/places, no implementation code beyond one optional CSS-custom-properties block.

## Risks & open decisions

Not specified in the source plan. Implicit constraint carried by the Execution section: the grep verification must pass before handback (the only tolerated exception is the deliberate `Plakatwache` mention in section 3).
