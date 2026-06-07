# Tasks: Home Page — Three-Tier Product Builder Hero

**Input**: `specs/001-home-page-hero/plan.md`, `specs/001-home-page-hero/spec.md`  
**Branch**: `001-home-page-hero`  
**Implementation source paths**: `public/index.html`, `public/index.css` only  
**Spec-Kit state exception**: `specs/001-home-page-hero/tasks.md` may be updated after implementation to reflect task completion state.

---

## Phase 1: CSS Foundation — `public/index.css`

**Purpose**: All new CSS classes added before any HTML changes. Keeps CSS and HTML work cleanly separable. Append all additions to the end of `index.css`; do not modify existing rules.

- [x] T001 [P] Add `.home-hero` section layout class (`min-height: 100svh`, flex column, `justify-content: center`, `padding: 40px`, `max-width: 720px`) in `public/index.css`
- [x] T002 [P] Add `.home-hero h1` typography rule (`font-size: clamp(28px, 5vw, 48px)`, `font-weight: 700`, `color: var(--lg-palette-text-on-surface)`, `line-height: 1.15`) in `public/index.css`
- [x] T003 [P] Add `.home-hero-lead` lead paragraph style (`font-size: clamp(15px, 2vw, 17px)`, `line-height: 1.65`, `color: var(--lg-palette-text-on-surface-secondary)`, `margin: 0 0 32px 0`, `max-width: 600px`) in `public/index.css`
- [x] T004 [P] Add `.home-cta-group` flex container (`display: flex`, `align-items: center`, `gap: 24px`, `flex-wrap: wrap`) in `public/index.css`
- [x] T005 [P] Add `.button-cta` glass button class with full hover, active, and focus-visible states (`padding: 12px 28px`, `font-weight: 600`, `--lg-glass-bg-opacity: 0.25`, backdrop-filter, border, box-shadow, transition) in `public/index.css`
- [x] T006 [P] Add `.home-secondary-links` and `.home-secondary-links a` styles (`color: var(--lg-palette-text-on-surface-secondary)`, no underline, hover `opacity: 0.7`) in `public/index.css`
- [x] T007 [P] Add `.home-section` shared section wrapper (`padding: 80px 40px`, `max-width: 1200px`, `margin: 0 auto`, `width: 100%`) in `public/index.css`
- [x] T008 [P] Add `.home-section-header` h2 style (`font-size: clamp(20px, 3vw, 26px)`, `font-weight: 700`, `color: var(--lg-palette-text-on-surface)`, `margin: 0 0 40px 0`) in `public/index.css`
- [x] T009 [P] Add `.home-pillars` three-column grid (`display: grid`, `grid-template-columns: repeat(3, 1fr)`, `gap: 24px`) in `public/index.css`
- [x] T010 [P] Add `.home-teaser-grid` two-column grid (`display: grid`, `grid-template-columns: repeat(2, 1fr)`, `gap: 24px`, `margin-bottom: 40px`) in `public/index.css`
- [x] T011 Add mobile overrides for all new classes in a new appended `@media (max-width: 768px)` block: `.home-hero` padding adjustment, `.home-pillars` and `.home-teaser-grid` collapse to `grid-template-columns: 1fr`, `.home-section` padding reduction, `.home-cta-group` column direction — in `public/index.css`

**Checkpoint**: Open `index.html` in browser — page should look unchanged (empty main). No visual regressions on About or Portfolio pages. New CSS classes exist but are unused.

---

## Phase 2: HTML — Body & Layout Change (US1 prerequisite)

**Purpose**: Remove `layout-fullscreen` from body. This is a blocking prerequisite for US1 — the hero `min-height: 100svh` approach only works when the body is not overflow-locked.

- [x] T012 Remove `class="layout-fullscreen"` from `<body>` tag in `public/index.html` (change `<body class="layout-fullscreen">` to `<body>`)

**Checkpoint**: Page still loads. Header visible. Empty main area. SpeedDial functional. No JS errors in console.

---

## Phase 3: User Story 1 — Hero Section (Priority: P1) 🎯 MVP

**Goal**: Above-the-fold hero with identity claim, lead paragraph, primary CTA, and secondary navigation links.

**Independent Test**: Open `public/index.html` at 1280×800. Without scrolling: H1 is visible, "Let's Start a Conversation" opens mail client to `sds.smith24@gmail.com`, "View the Work" has `href="#portfolio-teaser"` and does not route away from `index.html`, and "Read the Philosophy" routes to `about.html`. Smooth-scroll behavior for `#portfolio-teaser` is validated after US3 creates the target section.

- [x] T013 [US1] Replace `<main class="portfolio-container layout-hero"></main>` with `<main>` containing a `<section class="home-hero">` in `public/index.html`
- [x] T014 [US1] Add `<h1>Architecting Products. Engineering Solutions.</h1>` inside `.home-hero` in `public/index.html`
- [x] T015 [US1] Add `<p class="home-hero-lead">` with the full lead paragraph copy inside `.home-hero` in `public/index.html`
- [x] T016 [US1] Add `<div class="home-cta-group">` containing the `.button-cta` mailto anchor and `.home-secondary-links` div with "View the Work" (`href="#portfolio-teaser"`) and "Read the Philosophy" (`href="./about.html"`) links inside `.home-hero` in `public/index.html`

**Checkpoint (US1)**: Hero H1, lead, CTA, and secondary links are visible above the fold at 1280×800. The mailto CTA and `about.html` link work correctly; "View the Work" preserves the `#portfolio-teaser` fragment target for US3. SpeedDial still opens/closes. JS line count = 23.

---

## Phase 4: User Story 2 — Proof Pillars (Priority: P2)

**Goal**: Three scannable glass cards below the hero fold validating the Product Builder positioning.

**Independent Test**: Scroll below the hero. Three cards are visible side-by-side on desktop (1280px): "The Product Mindset", "High-Fidelity Engineering", "Agentic Orchestration". At 375px, cards stack vertically.

- [x] T017 [US2] Add `<section class="home-section">` after the hero section in `public/index.html`
- [x] T018 [US2] Add `<div class="home-pillars">` containing three `<article class="card card-elevated">` elements inside the pillars section, each with a `<div class="content">`, `<h3>`, and `<p>` matching the approved copy in `public/index.html`:
  - Card 1: **The Product Mindset** — _"Great software bridges the gap between deterministic constraints and infinite possibility. I listen to understand the human goal first, ensuring technical architecture aligns seamlessly with user needs and business objectives."_
  - Card 2: **High-Fidelity Engineering** — _"Specializing in strong JavaScript fundamentals and modern TypeScript ecosystems. I construct scalable, decentralized applications and craft depth-aware, glassmorphic interfaces that prioritize a flawless user experience."_
  - Card 3: **Agentic Orchestration** — _"I leverage AI beyond basic chat. By designing custom spec-driven workflows and structured system prompts, I use generative models as dedicated engineering assistants to accelerate platform modernization and system re-engineering."_

**Checkpoint (US2)**: Three pillar cards visible on desktop side-by-side. Cards stack on mobile (375px). Card glass styling matches existing `.card-elevated` pattern. Hero (US1) still fully functional.

---

## Phase 5: User Story 3 — Portfolio Teaser (Priority: P3)

**Goal**: Two featured project cards with section header and "Explore All Projects" CTA linking to the full portfolio page.

**Independent Test**: Scroll to the bottom of the page. "Built for the Human Goal" header, Cup card, Wine Rack card, and "Explore All Projects" button are all visible. The button routes to `portfolio.html`. The `#portfolio-teaser` anchor from "View the Work" (US1) scrolls directly to this section.

- [x] T019 [US3] Add `<section class="home-section" id="portfolio-teaser">` after the pillars section in `public/index.html`
- [x] T020 [US3] Add `<h2 class="home-section-header">Built for the Human Goal</h2>` inside the portfolio teaser section in `public/index.html`
- [x] T021 [US3] Add `<div class="home-teaser-grid">` containing two image-free `<article class="card card-elevated">` elements, each with `<div class="content">`, `<h3>`, and `<p>` in `public/index.html`:
  - Card 1: **Cup** — _"A cloud-native social media suite built on the AT Protocol — schema-driven XRPC architecture, federated data flows, and glassmorphic UI components."_
  - Card 2: **Wine Rack** — _"A multi-tenant wine inventory tracker powered by an orchestrated system of specialized Gemini agents: Sommelier, Critic Research, and OCR Entry."_
- [x] T022 [US3] Add `<div class="home-teaser-cta">` containing `<a href="./portfolio.html" class="button-cta">Explore All Projects</a>` below the teaser grid in `public/index.html`

**Checkpoint (US3)**: "View the Work" anchor from the hero smooth-scrolls to this section. Both project cards visible. "Explore All Projects" routes to `portfolio.html`. All three sections render correctly end-to-end.

---

## Phase 6: Polish & Cross-Cutting Validation

**Purpose**: Final accessibility, dark mode, and constitution compliance checks.

- [ ] T023 [P] Verify WCAG 2.1 AA contrast for all text on glass surfaces in light mode (DevTools accessibility inspector or browser contrast checker)
- [ ] T024 [P] Verify dark mode rendering — toggle `prefers-color-scheme: dark` in DevTools; all three sections must render correctly using existing token overrides
- [ ] T025 [P] Verify `prefers-reduced-motion` — smooth-scroll should disable when this media query is active (already handled by existing CSS `scroll-behavior: auto` rule; confirm no regressions)
- [ ] T026 [P] Verify zero outbound network requests — open DevTools Network tab with cache cleared; confirm 0 external requests on page load
- [x] T027 Verify JS line count — 28 lines confirmed (≤30 ✅) — count lines in `<script>` block in `index.html`; must remain at 23 (≤30 limit)
- [ ] T028 [P] Cross-breakpoint smoke test at 375px (iPhone SE), 768px (tablet), 1280px (desktop), 1440px (wide desktop) — no horizontal overflow, no layout breaks
- [ ] T029 [P] Keyboard navigation test — Tab through all interactive elements on the page; confirm CTA, secondary links, "Explore All Projects", and SpeedDial are all reachable and activatable via keyboard
- [x] T030 Update `tasks.md` to reflect final implementation state (mark completed tasks)

---

## Dependencies & Execution Order

```
Phase 1 (T001–T011) — CSS only, no HTML dependencies
    ↓
Phase 2 (T012) — Body class removal, required before US1 renders correctly
    ↓
Phase 3 (T013–T016) — US1 Hero [BLOCKS US2/US3 in-page scroll test]
    ↓
Phase 4 (T017–T018) — US2 Pillars
    ↓
Phase 5 (T019–T022) — US3 Portfolio Teaser
    ↓
Phase 6 (T023–T030) — Validation [all stories complete]
```

### Parallel Opportunities

- T001–T010 (CSS classes): all independent, can be written in one pass
- T023–T029 (validation tasks): all independent, run together after T022

---

## Implementation Notes

- **Copy exactly**: Pillar and teaser card copy is locked in the spec. Do not paraphrase.
- **No new `<script>` tags**: The existing SpeedDial script block is untouched. Do not add, remove, or reorder any lines in it.
- **CSS append-only**: Add new rules at the end of `index.css`. Do not modify or reorder existing rules.
- **`about.html` and `portfolio.html` are out of scope**: Do not touch these files.
- **`id="portfolio-teaser"`**: This anchor ID is referenced by the "View the Work" link in the hero. It must be present on the Section 3 `<section>` element exactly as specified.
