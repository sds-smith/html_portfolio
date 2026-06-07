# Context Snapshot — Home Page Hero Feature

**Generated**: 2026-06-07  
**Phase**: End of Phase 4 (Clarify) → Handoff to Phase 5 (Plan & Tasks)  
**Purpose**: Restore full context in a new session with zero chat history. Read this before running `/speckit.plan`.

---

## The Mission

Build a three-section scrolling home page for `public/index.html` that positions Shawn Smith as a **Product Builder** — not just a software engineer — to recruiters and hiring managers. The page must be pure HTML + CSS with zero new JavaScript.

---

## Who Shawn Is (The Proof Behind the Positioning)

This context is critical for copy-accuracy during implementation:

- **10 years as District Manager at Panera Bread** (Lemek LLC, July 2011 – Oct 2021): Directed $20M+ annual revenue across 6 business units. Cross-functional stakeholder alignment, OKRs, talent development. This is the operational leadership that makes the "Product Builder" claim credible — not engineering credentials alone.
- **Principal Engineer at Metamatopoeia** (Oct 2021 – present): Self-directed. Built Liquid Glass UI (open-source React library on npm), CUP (AT Protocol social app), 1on1Boss (enterprise SPA from Figma to production). This is the proof of full end-to-end product ownership.
- **Full-Stack Developer → Software Engineer at DESI** (Feb 2023 – present): Enterprise modernization at scale. Multi-agent Code Transformation pipeline, AWS infrastructure, SharePoint migration, Agile SDLC formalization, mentorship.
- **Open Source**: `@metamatopoeia/liquid-glass-ui` (maintainer), DefinitelyTyped (contributor).

---

## What the Page Does (Three Sections)

### Section 1 — Hero (above the fold, `min-height: 100svh`)
- **H1**: `Architecting Products. Engineering Solutions.`
- **Lead paragraph**: *"With a decade of high-volume operational leadership, I don't just write code — I partner in discovery, shape UI/UX, and deliver the final product. I build high-fidelity, human-centered web applications by combining robust React and TypeScript ecosystems with forward-thinking agentic orchestration."*
- **Primary CTA**: `<a href="mailto:sds.smith24@gmail.com">` styled with `.button-cta` — text: *"Let's Start a Conversation"*
- **Secondary links** (plain text, `nav a` style): *"View the Work"* (smooth-scroll anchor `#portfolio-teaser`) · *"Read the Philosophy"* (href `./about.html`)

### Section 2 — Proof Pillars (three `.card-elevated` cards, side-by-side on desktop, stacked on mobile)
| Card | Heading | Copy |
|---|---|---|
| 1 | The Product Mindset | *"Great software bridges the gap between deterministic constraints and infinite possibility. I listen to understand the human goal first, ensuring technical architecture aligns seamlessly with user needs and business objectives."* |
| 2 | High-Fidelity Engineering | *"Specializing in strong JavaScript fundamentals and modern TypeScript ecosystems. I construct scalable, decentralized applications and craft depth-aware, glassmorphic interfaces that prioritize a flawless user experience."* |
| 3 | Agentic Orchestration | *"I leverage AI beyond basic chat. By designing custom spec-driven workflows and structured system prompts, I use generative models as dedicated engineering assistants to accelerate platform modernization and system re-engineering."* |

### Section 3 — Portfolio Teaser (`id="portfolio-teaser"`, two image-free `.card-elevated` cards)
- **Section header**: *"Built for the Human Goal"*
- **Card 1 — Cup**: Title + *"A cloud-native social media suite built on the AT Protocol — schema-driven XRPC architecture, federated data flows, and glassmorphic UI components."*
- **Card 2 — Wine Rack**: Title + *"A multi-tenant wine inventory tracker powered by an orchestrated system of specialized Gemini agents: Sommelier, Critic Research, and OCR Entry."*
- **Section CTA**: `<a href="./portfolio.html">` — *"Explore All Projects"*

---

## Key Architectural Decisions (Binding)

1. **Remove `body.layout-fullscreen`** from `index.html`. The page scrolls naturally like `about.html`. The `body:not(.layout-fullscreen)` CSS rule applies padding automatically.
2. **Hero section** uses `min-height: 100svh` + `display: flex; flex-direction: column; justify-content: center` to sit above the fold.
3. **New CSS class `.button-cta`**: Larger padding (`12px 28px`), `font-weight: 600`, `--lg-glass-bg-opacity: 0.25`, same glass treatment as `.button` base. Added to `index.css`.
4. **No new JS**: SpeedDial script stays exactly as-is (23 lines). No new script tags.
5. **Section 3 cards are image-free**: `.content` only, no `.media` element.
6. **Pillar copy length** (~35 words each) is a documented and approved exception to the ~25-word site norm.

---

## Files In Scope

| File | Change |
|---|---|
| `public/index.html` | Major — replace empty `<main>` with three-section content; remove `layout-fullscreen` from `<body>` |
| `public/index.css` | Additive — new `.button-cta` class; new section layout modifier classes as needed |

**Out of scope**: `about.html`, `portfolio.html`, any other file.

---

## Constitution Constraints Reminder

- JS total: ≤30 lines. Currently 23 (SpeedDial). **Hard ceiling: add 0 lines.**
- No CDN, no external URLs.
- Design tokens: `--lg-{group}-{subgroup}-{token}` naming. Use existing tokens first.
- Dark mode (`prefers-color-scheme: dark`) must work for all new components via existing `:root` overrides.
- All interactive elements: keyboard-navigable, WCAG 2.1 AA contrast.

---

## Spec Location

Full spec: `.specify/memory/spec.md`  
Constitution: `.specify/memory/constitution.md`
