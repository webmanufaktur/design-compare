# DesignTest (DES)

Design-eval sandbox, not a product: several AI models receive one identical design briefing and each delivers a landing page from it, so their design capabilities can be compared fairly. The design system is fixed (brand, colors, tokens, components, page map); the visual execution is free.

## Current artifact

- `design-briefing.md` — v1.0, reviewed. English design briefing for the landing page of „Plakatradar“, a fictional multi-party election-poster map app. Brand, ~30 hex colors, px/rem tokens, 10 components, 9-section page map; deliverable is one responsive light-mode landing page, fixed stack: HTML + Tailwind CSS (CDN) + Alpine.js/htmx.
- `index.html` — the evaluated landing-page deliverable (glm-5.3-flash slot): 9 sections per page map, tokens 1:1, Alpine.js für Header-Scroll-State + Mobile-Menü, sonst statisch. Öffnen: Datei direkt im Browser (CDN nötig).
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
