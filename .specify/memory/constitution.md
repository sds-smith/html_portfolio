<!--
  Sync Impact Report
  Version change: 1.0.0 → 1.0.1 (clarify mailto compliance)
  Modified principles:
    - II. Zero External Dependencies — clarified that user-initiated mailto: links
      are compliant because they do not load remote assets during page render
    - Technical Constraints / Assets — narrowed passive asset restrictions and
      explicitly permits mailto: href values for direct-contact CTAs
  Added sections: None
  Removed sections: None (template placeholders replaced in full)
  Templates reviewed:
    - .specify/templates/plan-template.md ✅ no changes needed (Constitution Check gates are resolved at /speckit.plan time)
    - .specify/templates/spec-template.md ✅ no changes needed (generic structure compatible with static-site features)
    - .specify/templates/tasks-template.md ✅ no changes needed (test tasks marked OPTIONAL; aligned with zero-dependency posture)
    - .specify/templates/commands/*.md ✅ not present
    - README.md ✅ no changes needed (dependency language remains compatible)
  Follow-up TODOs: None — all placeholders resolved.
-->

# HTML Portfolio Constitution

## Core Principles

### I. CSS-First, HTML-Native

All styling, visual effects, and interactive states MUST be implemented in CSS. HTML MUST use semantic elements appropriate to content meaning. JavaScript is permitted ONLY when a behavior is technically impossible to achieve with HTML and CSS alone. The total JavaScript footprint MUST remain at or below ~30 lines. No JavaScript libraries, polyfill bundles, or framework runtimes are permitted.

**Rationale**: The project exists as proof of concept that sophisticated UIs can be built without JavaScript complexity. This constraint is the core premise — violating it undermines the entire demonstration.

### II. Zero External Dependencies

The site MUST be fully functional by opening any HTML file directly in a browser with zero outbound network requests during initial page load and passive rendering. CDN resources, npm packages, web fonts from third-party hosts, analytics scripts, icon libraries, and build tools are all prohibited. Every asset MUST be self-contained within the repository. User-initiated `mailto:` links are permitted for direct-contact actions because they do not load remote assets during page rendering and do not introduce runtime dependencies.

**Rationale**: External dependencies introduce latency, privacy exposure, and supply-chain risk, and break the zero-dependency claim that is central to the project's technical identity.

### III. Brand Integrity

Every content, layout, and visual decision MUST reinforce the professional identity: **Product Builder grounded in Software Engineering**. Copy MUST be precise, technically confident, and free of generic filler. Design MUST signal craftsmanship and intentionality. Any change that dilutes, contradicts, or weakens this positioning is prohibited.

**Rationale**: The site is a primary branding artifact. Its quality and coherence directly represent the owner's professional reputation. Bland or inconsistent presentation is a brand failure.

### IV. Minimalist Excellence

Every element, page, and interaction MUST earn its place. Reduction is the primary design tool — sophistication is achieved through restraint, not addition. Features that add complexity without proportionate user value are prohibited. Decoration without function is prohibited. When in doubt, remove.

**Rationale**: Minimalism is the aesthetic expression of the engineering philosophy the site embodies. Accumulation of features or styles without purpose contradicts the brand message directly.

### V. Accessibility & Graceful Degradation

All pages MUST use semantic HTML5 elements. The site MUST respect `prefers-color-scheme` and `prefers-reduced-motion` media queries. CSS visual effects MUST degrade gracefully when `backdrop-filter` or other modern CSS features are unsupported. All interactive elements MUST be keyboard-navigable and MUST meet WCAG 2.1 AA contrast requirements.

**Rationale**: Accessibility is a baseline engineering standard, not optional polish. A site demonstrating engineering craft that fails on accessibility fails its own premise.

## Technical Constraints

The technology stack is fixed and non-negotiable:

- **Markup**: Semantic HTML5; no template engines or generated HTML
- **Styling**: Vanilla CSS with custom properties; no preprocessors (Sass, Less, PostCSS)
- **Scripting**: Inline or `<script>`-embedded vanilla JavaScript; ≤30 lines total; no `import` or `require`
- **Delivery**: Static files served directly from `public/`; no build step, no server-side rendering, no bundler
- **Assets**: Local only — no external URLs in `src` or `url()` references. `mailto:` values are permitted in `href` attributes when used for explicit user-initiated direct-contact CTAs.

Any deviation MUST be documented in the plan's Complexity Tracking table with explicit justification and explicit user approval before implementation.

## Design & Brand Standards

- The **liquid glass** visual theme is the defining aesthetic and MUST be preserved across all pages; achieved exclusively via CSS (`backdrop-filter`, `background`, `box-shadow`, `border`, and layered opacity)
- **Design tokens** MUST follow the `--lg-{group}-{subgroup}-{token}` naming convention defined in `public/index.css`
- All pages MUST share the single stylesheet `public/index.css`; page-specific overrides require justification
- **Typography** MUST use a system font stack; external web font loading is prohibited
- **Dark mode** support via `prefers-color-scheme: dark` is REQUIRED for all new components

## Governance

This constitution is the decision authority for all design and engineering choices in this project. It supersedes personal preferences, convention, and external style guides.

Amendment procedure:

1. Propose the change with explicit rationale for why the current principle is insufficient
2. Identify which pages, CSS rules, or JavaScript are affected
3. Increment the version and update this document before implementing the change

All feature specifications (`spec.md`) and implementation plans (`plan.md`) MUST include a **Constitution Check** verifying compliance with Principles I–V before work begins. Any approved violations MUST be documented in the Complexity Tracking table of `plan.md`.

**Version**: 1.0.1 | **Ratified**: 2026-06-07 | **Last Amended**: 2026-06-07
