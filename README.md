# DesignTest (DES)

Design-eval sandbox, not a product: several AI models receive one identical design briefing and each delivers a landing page from it, so their design capabilities can be compared fairly. The design system is fixed (brand, colors, tokens, components, page map); the visual execution is free.

## Current artifact

- `index.html` — v1.0, reviewed (fresh-context verdict OK). Responsive light-mode landing page for „Plakatradar“ per `design-briefing.md`: 9 fixed sections, all fixed strings/hex/tokens verbatim, status lifecycle with flags, abstract SVG map teaser (8 pin colors + 2 status pins), Alpine.js mobile menu. Single self-contained file — Tailwind + Alpine via CDN, no build step.
- `design-briefing.md` — v1.0, reviewed. English design briefing for the landing page of „Plakatradar“, a fictional multi-party election-poster map app. Brand, ~30 hex colors, px/rem tokens, 10 components, 9-section page map; deliverable is one responsive light-mode landing page, fixed stack: HTML + Tailwind CSS (CDN) + Alpine.js/htmx.
- Plan: `.plans/design-briefing-landingpage.md`
- Todoist task: DES 6hPhR4F7Q3RvQHPH

## Tech Stack

- Briefing: Markdown. Evaluated deliverables: HTML + Tailwind CSS (CDN) + Alpine.js/htmx, no build step (fixed by briefing §1).

## Domains

| Env  | URL |
| ---- | --- |
| prod | TBD |
| dev  | TBD |

## Client

TBD (internal use: comparing AI models' design capabilities)
