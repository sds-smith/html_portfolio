# Feature Specification: Home Page — Three-Tier Product Builder Hero

**Feature Branch**: `001-home-page-hero`  
**Created**: 2026-06-07  
**Status**: Draft  
**Input**: User description: "Three-tier content approach on the Home page (index.html) that differentiates the owner as a Product Builder — an engineer capable of weighing in on and contributing to discovery and design, not just engineering — and lands a clear 'direct connect' call to action. Target audience: recruiters and hiring managers."

---

## Constitution Check

| Principle                               | Status | Notes                                                                                                                          |
| --------------------------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------ |
| I. CSS-First, HTML-Native               | ✅     | No new JS. SpeedDial script remains at 23 lines (within ≤30 limit). All tiers implemented in semantic HTML + CSS only.         |
| II. Zero External Dependencies          | ✅     | No CDN, no web fonts, no external URLs in markup or CSS. All assets already local.                                             |
| III. Brand Integrity                    | ✅     | Feature is the primary brand expression. Every content decision reinforces "Product Builder grounded in Software Engineering." |
| IV. Minimalist Excellence               | ✅     | Three sections, each with a defined purpose. No decoration without function. Copy is precise and intentional.                  |
| V. Accessibility & Graceful Degradation | ✅     | Semantic HTML5 elements, WCAG 2.1 AA contrast, dark mode via existing tokens, `prefers-reduced-motion` inherited.              |

**Approved Deviation**: Removing `body.layout-fullscreen` from `index.html` to enable multi-section vertical scroll. This is a layout model change, not a stack change. No new CSS primitives required — existing `.scrollable` and `body:not(.layout-fullscreen)` rules already handle this pattern.

---

## User Scenarios & Testing

### User Story 1 — Recruiter Scans the Hero (Priority: P1)

A recruiter lands on the home page for the first time. Within 5 seconds they understand who Shawn is, what differentiates him from a standard software engineer, and how to contact him — without scrolling.

**Why this priority**: The hero is the only content guaranteed to be seen. If the positioning and CTA are not above the fold, the feature fails its primary goal.

**Independent Test**: Open `index.html` in a browser at 1280×800 viewport. Without scrolling, the H1, lead paragraph, primary CTA button, and secondary text links are all visible and functional.

**Acceptance Scenarios**:

1. **Given** a recruiter opens `index.html`, **When** the page loads, **Then** the H1 "Architecting Products. Engineering Solutions." is the first prominent text they see.
2. **Given** a recruiter is on the hero, **When** they click "Let's Start a Conversation", **Then** their default mail client opens a new email addressed to `sds.smith24@gmail.com`.
3. **Given** a recruiter is on the hero, **When** they click "View the Work", **Then** the page smooth-scrolls to the Portfolio Teaser section.
4. **Given** a recruiter is on the hero, **When** they click "Read the Philosophy", **Then** they are routed to `about.html`.

---

### User Story 2 — Hiring Manager Validates the Claim (Priority: P2)

A hiring manager who read the hero scrolls down to validate that the "Product Builder" positioning is substantiated — not just marketing copy. They encounter three scannable capability pillars that map directly to their hiring criteria: product thinking, engineering execution, and AI-forward tooling.

**Why this priority**: Without the proof pillars, the hero claim is unverified. This section converts interest into qualified confidence.

**Independent Test**: Scroll past the hero fold. Three distinct pillar cards are visible: "The Product Mindset", "High-Fidelity Engineering", and "Agentic Orchestration". Each contains a heading and supporting copy.

**Acceptance Scenarios**:

1. **Given** a user scrolls below the hero fold, **When** the pillars section enters the viewport, **Then** three equal-width cards are visible side-by-side on desktop and stacked on mobile.
2. **Given** a hiring manager reads Pillar 1, **When** they read the copy, **Then** they understand the owner leads with the human goal before technical architecture.
3. **Given** a hiring manager reads Pillar 3, **When** they read the copy, **Then** they understand the owner designs AI workflows as engineering systems, not consumer tools.

---

### User Story 3 — Recruiter Validates Technical Depth (Priority: P3)

After reading the pillars, a recruiter wants to see actual work before reaching out. They scroll to the portfolio teaser, see two curated featured projects with brief descriptions, and click through to the full portfolio.

**Why this priority**: Provides the evidence layer that supports the CTA. A recruiter confident in both positioning and proof is more likely to initiate contact.

**Independent Test**: Below the pillars, a "Built for the Human Goal" section header is visible with two project cards (Cup and Wine Rack) and an "Explore All Projects" button linking to `portfolio.html`.

**Acceptance Scenarios**:

1. **Given** a user scrolls to Section 3, **When** the portfolio teaser renders, **Then** two project cards are visible: Cup and Wine Rack, each with a title and brief description.
2. **Given** a user clicks "Explore All Projects", **When** the link is activated, **Then** they are routed to `portfolio.html`.

---

### Edge Cases

- **Reduced motion**: Smooth-scroll behavior on "View the Work" anchor link must respect `prefers-reduced-motion: reduce` (already handled by existing CSS `scroll-behavior: auto` rule on the root).
- **Mobile viewport**: Pillar cards stack vertically on viewports ≤768px. Primary CTA remains tap-target compliant (minimum 44×44px).
- **Missing background image**: If `background-image-profile.jpeg` fails to load, the `--lg-palette-background-fallback` gradient renders as the background — hero copy must remain legible against it.
- **Keyboard navigation**: The primary CTA, secondary links, and "Explore All Projects" button must all be reachable and activatable via keyboard alone.
- **Dark mode**: All three sections must render correctly under `prefers-color-scheme: dark` using existing token overrides.

---

## Requirements

### Functional Requirements

- **FR-001**: `index.html` MUST render a hero section (Section 1) that is fully visible without scrolling at a 1280×800 desktop viewport.
- **FR-002**: Section 1 MUST contain an `<h1>` with the text "Architecting Products. Engineering Solutions."
- **FR-003**: Section 1 MUST contain a lead paragraph establishing the Product Builder positioning and referencing operational leadership, React/TypeScript, and agentic orchestration.
- **FR-004**: Section 1 MUST contain a primary CTA anchor styled as a glass button with text "Let's Start a Conversation" linking to `mailto:sds.smith24@gmail.com`.
- **FR-005**: Section 1 MUST contain two secondary text links: "View the Work" (smooth-scroll anchor to Section 3) and "Read the Philosophy" (route to `about.html`).
- **FR-006**: `index.html` MUST render a proof pillars section (Section 2) with exactly three cards: "The Product Mindset", "High-Fidelity Engineering", and "Agentic Orchestration", each with supporting copy.
- **FR-007**: `index.html` MUST render a portfolio teaser section (Section 3) with the header "Built for the Human Goal", two featured project cards (Cup, Wine Rack), and a "Explore All Projects" link to `portfolio.html`.
- **FR-008**: The page layout MUST support vertical scroll. The `layout-fullscreen` class MUST be removed from `<body>`.
- **FR-009**: All new HTML elements MUST use semantic tags (`<section>`, `<article>`, `<h1>`–`<h3>`, `<p>`, `<a>`).
- **FR-010**: All new visual styling MUST use existing `--lg-*` design tokens. New CSS classes MUST follow the `--lg-{group}-{subgroup}-{token}` naming convention where new tokens are required.
- **FR-011**: No JavaScript MUST be added. The existing SpeedDial script (23 lines) MUST remain intact and functional.
- **FR-012**: All new interactive elements (links, buttons) MUST be keyboard-navigable and meet WCAG 2.1 AA contrast requirements.

### Key Entities

- **Hero Section**: The above-the-fold unit. Contains identity claim, positioning lead, primary CTA, and secondary navigation links.
- **Proof Pillar**: A glass card (`card-elevated`) containing a heading and supporting copy paragraph. Three instances required.
- **Portfolio Teaser Card**: A simplified project card (subset of full portfolio card) showing project title and brief description. Two instances required (Cup, Wine Rack).
- **Primary CTA Button**: An `<a>` element styled as a glass button. Distinct from the existing `.button` class — requires higher visual prominence.

---

## Success Criteria

### Measurable Outcomes

- **SC-001**: A user opening `index.html` at 1280×800 can read the H1, lead, and locate the primary CTA without scrolling.
- **SC-002**: The "Let's Start a Conversation" link opens a mail client compose window pre-addressed to `sds.smith24@gmail.com` in one click.
- **SC-003**: The "View the Work" anchor scrolls the viewport to Section 3 without a full page navigation.
- **SC-004**: All three sections render without horizontal overflow on viewports from 375px (iPhone SE) to 1440px (standard desktop).
- **SC-005**: The page passes WCAG 2.1 AA contrast check for all text on glass surfaces in both light and dark modes.
- **SC-006**: Total JavaScript line count across `index.html` does not exceed 30 lines after implementation.
- **SC-007**: No outbound network requests are made when the page loads (verified via browser DevTools Network tab with cache cleared).

---

## Assumptions

- The existing background image (`background-image-profile.jpeg`) and its right-side positioning remain unchanged; the hero copy is positioned to the left to complement this.
- The `.card-elevated` and `.card` CSS classes are sufficient base patterns for Sections 2 and 3; only layout-specific modifier classes will be added.
- `index.css` is the sole stylesheet — no new CSS file will be created.
- The featured project descriptions in Section 3 are abbreviated summaries drawn from existing `portfolio.html` copy, not new content.
- The SpeedDial component remains on `index.html` and continues to function as the persistent contact mechanism across all three sections.
- The `about.html` and `portfolio.html` pages are out of scope; this spec covers `index.html` and `index.css` only.

---

## Phase 4 Clarification Record

Gaps identified and resolved during `/speckit.clarify`. These decisions are binding for implementation.

| Gap                        | Decision                                                                                                                                                                                                                                                                                                         |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **CTA visual prominence**  | A new `.button-cta` CSS class is required. Larger padding than `.button`, `font-weight: 600`, higher `--lg-glass-bg-opacity` (≈0.25) for stronger surface presence.                                                                                                                                              |
| **Hero min-height**        | The hero `<section>` receives `min-height: 100svh` with flex centering (`display: flex; flex-direction: column; justify-content: center`). This replaces the role previously held by `body.layout-fullscreen`.                                                                                                   |
| **Secondary link styling** | "View the Work" and "Read the Philosophy" styled equivalently to `nav a`: `color: var(--lg-palette-text-on-surface-secondary)`, no underline, `opacity: 0.8` on hover.                                                                                                                                           |
| **Section 3 card format**  | Portfolio teaser cards are **image-free**. Title + brief description only. No `.media` element.                                                                                                                                                                                                                  |
| **Pillar copy length**     | Pillar copy averages ~35 words per card. This is a justified exception to the site's typical ~25-word paragraph length. Justification: proof pillars serve a persuasion function requiring minimal elaboration; the brand positioning depends on this content being substantive enough to be credible. Approved. |
