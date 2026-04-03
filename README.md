# Design & UX Skills

28 agent skills for a complete design-to-polish pipeline. Works with Claude Code, Cursor, and other AI coding agents.

Managed with [`npx skills`](https://github.com/vercel-labs/skills) — the open agent skills ecosystem by Vercel Labs.

## Install

Install all skills globally:

```bash
npx skills add https://github.com/Creaturro/skills.git -g --all
```

Install specific skills:

```bash
npx skills add https://github.com/Creaturro/skills.git -g -s frontend-design -s polish -s audit
```

## Update

```bash
npx skills update -g
```

## Dependency Tree

The most important thing to understand — skills call other skills:

```
FOUNDATION (run once per project):

  /teach-impeccable → design context → .impeccable.md
         ↓ (read automatically)
  /frontend-design  → aesthetics, typography, color, motion
         ↓
  ┌──────┴───────────────────────────────────┐
  │  14 design skills depend on these:       │
  │  /adapt /animate /arrange /bolder        │
  │  /clarify /colorize /delight /distill    │
  │  /normalize /onboard /overdrive          │
  │  /polish /quieter /typeset               │
  └──────────────────────────────────────────┘

ORCHESTRATORS (run when you don't know what's wrong):

  /audit    → technical diagnosis → recommends skills to fix
  /critique → UX evaluation → points to which skills to run

ANTAGONIST PAIR:

  /bolder  ←──── intensity ────→ /quieter
  amplifies                      tones down
```

## Pipeline — step by step

| Step | Command | What it does |
|------|---------|--------------|
| 01 | `/teach-impeccable` | One-time setup: gathers design context (audience, brand, tone) |
| 02 | `/make-plan` | Plan features and UI architecture |
| 03 | `/frontend-design` or `/shadcn` | Build the interface |
| 04 | `/typeset` + `/arrange` + `/colorize` | Visual details |
| 05 | `/animate` | Micro-interactions where they improve UX |
| 06 | `/audit` or `/critique` | Diagnosis → skill recommendations |
| 07 | Targeted skills from recommendations | `/adapt`, `/clarify`, `/distill` ... |
| 08 | `/polish` | Final pass before publishing |

## When to use which?

| Problem | Skill |
|---------|-------|
| Don't know what's wrong | `/audit` or `/critique` — they analyze and point |
| UI is boring | `/bolder`, `/colorize`, `/delight` |
| UI is chaotic | `/quieter`, `/distill`, `/normalize` |
| Text is unclear | `/clarify` |
| Typography doesn't work | `/typeset` |
| Layout is broken | `/arrange`, `/adapt` |
| No animations | `/animate`; want wow → `/overdrive` |
| Need design tokens | `/extract` |
| Before publishing | `/polish` (always last) |

## Skills

### 1. Planning & Setup

| Skill | Description |
|-------|-------------|
| `teach-impeccable` | One-time design context setup (audience, brand, tone) → .impeccable.md |
| `make-plan` | Phased implementation plan with documentation discovery |
| `do` | Executes plan from /make-plan via subagents |
| `feature-dev` | Guided feature development with codebase understanding |

### 2. Design & Build UI

| Skill | Description |
|-------|-------------|
| `frontend-design` | Production-grade interfaces with strong aesthetics, anti-AI-slop |
| `emil-design-eng` | Emil Kowalski's philosophy — UI polish, animations, invisible details |
| `shadcn` | shadcn/ui component management — add, search, debug, presets |
| `theme-factory` | Theme toolkit for artifacts (slides, reports, landing). 10 presets + custom |
| `playground` | Interactive single-file HTML playgrounds with live preview |
| `onboard` | Onboarding flows, empty states, first-run experience |
| `colorize` | Strategic color for monochromatic UIs |
| `typeset` | Typography — fonts, hierarchy, sizing, readability |
| `arrange` | Layout, spacing, visual rhythm, hierarchy |
| `animate` | Animations and micro-interactions that improve UX |
| `overdrive` | Shaders, spring physics, scroll-driven reveals, 60fps — wow factor |

### 3. Critique & Audit

| Skill | Description |
|-------|-------------|
| `audit` | Technical audit — a11y, perf, theming, responsive. P0-P3 report. Orchestrator: recommends 20 skills. |
| `critique` | UX evaluation — visual hierarchy, cognitive load, quantitative scoring. Orchestrator. |
| `web-design-guidelines` | Review UI against Web Interface Guidelines — a11y, UX, best practices |

### 4. Polish & Refinement

| Skill | Description |
|-------|-------------|
| `polish` | Final quality pass — alignment, spacing, consistency, micro-details |
| `adapt` | Responsive — breakpoints, fluid layouts, touch targets, cross-device |
| `normalize` | Realign UI to design system standards — tokens, spacing, patterns |
| `extract` | Extract reusable components and design tokens into design system |
| `distill` | Simplify — remove complexity, reveal design essence |
| `clarify` | UX copy — error messages, labels, microcopy, instructions |
| `delight` | Joy moments — from functional to memorable |
| `bolder` | Amplify boring designs — add character and visual impact |
| `quieter` | Tone down aggressive designs — calm, quality, balance |

### Meta

| Skill | Description |
|-------|-------------|
| `find-skills` | Discover and install new skills from the ecosystem |

## Sources

These skills are curated from multiple sources:

- **Impeccable.dev** — UI design skills (adapt, animate, arrange, audit, bolder, clarify, colorize, critique, delight, distill, extract, frontend-design, normalize, onboard, overdrive, polish, quieter, teach-impeccable, typeset)
- **Anthropic** — workflow skills (make-plan, do, feature-dev, theme-factory, playground)
- **Emil Kowalski** — design engineering philosophy (emil-design-eng)
- **shadcn** — component management (shadcn)
- **Vercel** — web design guidelines (web-design-guidelines)
- **Skills ecosystem** — discovery (find-skills)

## Skill structure

Each skill is a folder with a `SKILL.md` file (and optional `references/`, `examples/` dirs):

```
skill-name/
├── SKILL.md              # Frontmatter (name, description) + instructions
├── references/           # Supporting docs the agent can read
└── examples/             # Code examples
```
