# Implementation Plan: Plakatradar Landing Page (`index.html`)

> DES: Plakatradar-Landingpage umsetzen — see .plans/plakatradar-landingpage.md (id: `6hPhjRVvh8373GgH`)

- **Date:** 2026-08-31
- **Status:** Done — delivered and reviewed 2026-08-31 (fresh-context reviewer verdict OK after 2 P1 fixes: component borders + 24px grid gaps)
- **Todoist:** DES: Plakatradar-Landingpage umsetzen — see .plans/plakatradar-landingpage.md (id: `6hPhjRVvh8373GgH`)
- **Predecessor plan:** `.plans/design-briefing-landingpage.md` (briefing authoring — done; preserved unchanged)

## Findings (the mismatch, and repo state)

1. **Mismatch (medium severity):** `.plans/design-briefing-landingpage.md` is the plan for *authoring the briefing document* ("Status: Planned — ready for worker handoff", Todoist `DES: Design-Briefing Plakatradar-Landingpage verfassen`, id 6hPhR4F7Q3RvQHPH) — that work is **done**: `design-briefing.md` v1.0 exists and is marked reviewed in `README.md`. Yet `prompt.md` invokes `/design @design-briefing.md @.plans/design-briefing-landingpage.md`, attaching the stale document-plan to an execution request. There is **no plan for the page artifact** (`index.html`); a worker handed the existing plan would re-plan briefing authoring, not the landing page. This plan closes that gap.
2. **No artifact exists:** the worktree contains only `.agents/skills/design/`, `.plans/design-briefing-landingpage.md`, `README.md`, `design-briefing.md`, `prompt.md`. No `index.html`, no build/test infra — verification must be the briefing's §10 self-check + grep + manual viewport inspection, not a test suite.
3. **Design skill lives in-repo:** `.agents/skills/design/SKILL.md` (+ `design-guidelines.md`, ~40 files under `guidelines/`). Its Load Contract requires loading every applicable rule file before writing UI; `dark-mode.md` must be skipped (briefing forbids dark mode). Where the skill's defaults differ from the briefing's fixed tokens, the briefing wins ("Preserve user constraints").
4. **Spec is exhaustively pinned:** stack (Tailwind CDN + Alpine/htmx only, single self-contained `index.html`), 9-section page map, ~30 hex values, tokens, components, fixed German strings, German number formatting, light mode only. Free space is limited to inner layout, illustration style, microcopy, and which CDN-JS lib per interaction.

## Goal

Deliver the Plakatradar landing page as a single self-contained `index.html` (repo root) implementing `design-briefing.md` v1.0 verbatim, verified against the 16-item self-check (§10) and the in-repo design skill.

*Plan-only note: this file describes the implementation work; the deliverable is the landing-page artifact itself, not further documents.*

## Current state

- Spec: `design-briefing.md` (fixed: §3 strings/brand, §4 page map, §6 colors, §7 tokens, §8 components, §9 MUST/MAY/NEVER, §10 self-check).
- Skill: `.agents/skills/design/SKILL.md` — Load Contract + workflow (inspect → load guidelines → implement → verify breakpoints/states).
- `prompt.md` is the eval invocation line; `README.md` describes the sandbox (project code DES).
- No existing HTML, no tooling — nothing to reuse, nothing to migrate.

## Plan

1. **Preflight — load skill + spec** (`core`). Read `.agents/skills/design/design-guidelines.md` and the applicable rule files: `general`, `landing-pages`, `section-layout`, `heading-groups`, `typography`, `colors`, `buttons`, `badges`, `headers`, `navigation`, `feature-lists`, `testimonials`, `stats`-relevant `surfaces`, `interactivity`, `responsive-design`, `icons`, `svg`, `shadows`, `border-radius`, `copywriting`, `footers`, `flexbox-layout`. Skip `dark-mode.md` (NEVER per briefing §6.6.5). Confirm briefing-MUST > skill-default precedence; if a `⚠️ ask-user` guideline rule is *not* already resolved by the briefing, escalate via `contact_supervisor` instead of guessing. *Verify:* applicable-files checklist ticked in the run log.
2. **Skeleton** (`core`). Create `index.html`: `<html lang="de">`, viewport meta, Google-Fonts `<link>` for Inter 400/500/600, Tailwind via CDN `<script>`, Alpine.js via CDN `defer`. Zero config block — every briefing value as Tailwind arbitrary values (`bg-[#6D28D9]`, `shadow-[0_4px_12px_rgba(24,24,27,0.08)]`, `max-w-[1152px]`, …). `scroll-behavior:smooth` via CSS for anchors. *Verify:* file opens, no console errors, CDN scripts resolve.
3. **Sections 1–5 in page-map order** (`core`). Header (sticky, scrolled state via Alpine `@scroll.window`, secondary CTA, hamburger panel w/ ≥44px targets, closes on link/outside tap), Hero (eyebrow/H1/subline, primary+secondary pair, inline-SVG map teaser: `#FAFAFA` base, 2px/4–6px streets, ~8 pin dots + 2 teardrop status pins, Musterstadt stats chip), testimonial strip (2–3 cards, initials avatars, "Vorname, Teamkontext"), how-it-works (3 numbered steps), features grid (6 cards, 3/2/1 columns). Two-element section pattern + 24px gap everywhere. *Verify:* §10 items 1, 11, 12, 15 spot-check.
4. **Sections 6–9** (`core`). Status lifecycle — all 5 badge variants per §8.5 with real dot+pill anatomy, flag combination row „Gestohlen“ + „Anzeige erstattet“, short model explanation; stats strip (12.480 / 1.270 / 38 / 4, German formatting); final CTA (claim + one filled primary on `#F5F3FF` panel); footer (anchors, „Impressum · Datenschutz“ → `#`, © 2026). *Verify:* §10 items 2, 3, 4, 5, 7.
5. **Copy pass** (`core`). All copy German, du-form, §3 tone (short main clauses, concrete numbers, no superlatives, no political siding); fixed strings verbatim incl. „So funktioniert's" typography; „Plakatwache“ appears nowhere. *Verify:* §10 item 2 + §3 do/don't table review.
6. **Acceptance pass — 16-item self-check + grep** (`core`). Walk `design-briefing.md` §10 item-by-item, each answered "met" with evidence. Grep gates (implementer runs): fixed strings present (`grep -c 'Kostenlos starten\|Jedes Plakat. Ein Pin. Eine Karte.\|Anzeige erstattet\|Impressum · Datenschutz' index.html`); forbidden absent (`grep -nE 'prefers-color-scheme|dark:|leaflet|mapbox|google' index.html` → no hits); filled primary limited to hero + final CTA (count `bg-[#6D28D9]` button usages; header stays outline). *Verify:* all 16 items "met" or the deviation reported to the parent.
7. **README sync** (`optional`, documenter, post-review): add `index.html` to "Current artifact".

## Out of scope

The app itself (screens/flows), dark mode, any build step or extra files beyond `index.html`, changes to `design-briefing.md` or the existing `.plans/design-briefing-landingpage.md`, pricing sections, real parties/people/places/map services, Todoist changes (documenter registers the new task separately).

## Risks & open questions

| Risk / question | Assessment / mitigation |
| --- | --- |
| No browser in the subagent run | Self-check item 13 (360–1440px, no horizontal overflow) and item 14 can only be verified by code-level reasoning (no fixed widths, `min-w-0`, responsive classes) plus the parent's final eyeball render. Not blocking; flagged so the parent renders the file once before accepting. |
| Tailwind CDN flavor (v3 Play vs v4 browser build) unpinned by the briefing | Both satisfy "via CDN"; implementer picks one, no decision needed. |
| Alpine vs htmx | Only the mobile menu and header scroll state need JS → Alpine alone; htmx stays unused (a MAY per §1). |
| Material requirement conflict | None found; nothing to escalate. |

## Handoff

- Plan file: `.plans/plakatradar-landingpage.md`
- Todoist: `DES: Plakatradar-Landingpage umsetzen — see .plans/plakatradar-landingpage.md` (id `6hPhjRVvh8373GgH`, p2, label DES, Inbox)
