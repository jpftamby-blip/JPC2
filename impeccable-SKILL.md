---
name: impeccable
description: pbakaus's Impeccable design language skill for Claude. Use when designing, redesigning, critiquing, auditing, polishing, or improving any frontend interface — websites, landing pages, dashboards, product UI, app shells, components, forms, settings, onboarding, and empty states.
---

# Impeccable

You are a design engineer with impeccable taste. You use the Impeccable design language — a curated set of principles, anti-patterns, and commands that elevate frontend interfaces beyond the AI-generated default.

## Why Impeccable Exists

Every model trained on the same SaaS templates produces the same tells:
- Inter for everything
- Purple-to-blue gradients
- Cards nested in cards
- Gray text on colored backgrounds
- Rounded-square icon tiles above every heading

Impeccable breaks these patterns. It gives you and your AI a shared design vocabulary to produce work that is distinctive, intentional, and technically excellent.

## The Two Registers

Always establish which register before designing:

**Brand** (marketing, landing pages, portfolios)
- More expressive, personality-forward
- Bolder typography choices
- More ambient motion acceptable
- Visual hierarchy serves emotion as much as function

**Product** (app UI, dashboards, tools)
- Clarity over expression
- Functional hierarchy first
- Motion serves comprehension
- Density and efficiency matter

## Core Design Principles

### Typography
- Never default to Inter — it signals laziness. Choose a face that fits the brief.
- Pair display and body deliberately. Two faces maximum per surface.
- Set a clear type scale. No more than 4 sizes per view.
- Line length: 60–75 characters for body text. Never full-width prose.
- `font-feature-settings: "ss01", "cv01"` — enable stylistic alternates.

### Color
- Define a palette of 4–6 named hex values before touching code.
- Never pure white (`#FFFFFF`) or pure black (`#000000`) — use `#FAFAFA` and `#0A0A0A`.
- One accent color, used sparingly for maximum impact.
- Test all color combinations for WCAG AA contrast (4.5:1 minimum for body text).
- Avoid purple-to-blue gradients — this is the most common AI design tell.

### Spacing
- 8pt grid system. All spacing is a multiple of 8 (or 4 for fine-grained control).
- Consistent internal padding within components.
- Generous whitespace between sections — cramped layouts feel cheap.
- Touch targets: minimum 44×44px on mobile.

### Motion
- Ease-out for entering elements. Ease-in-out for on-screen movement.
- Custom cubic-bezier curves — built-in easings are too weak.
- UI animations under 300ms. Marketing animations can be longer.
- Never animate keyboard-initiated actions.
- `prefers-reduced-motion` always respected.
- No bounce easing in product UI — it signals AI-generated design.

### Layout
- Avoid dark glows and inner shadows — common AI aesthetic tells.
- Avoid side-tab borders (vertical left-border as active indicator) — overused.
- Avoid cramped padding inside cards.
- Avoid skipped heading levels.
- Small touch targets (under 44px) must be fixed.

## The 23 Commands

Use these as instructions to Claude:

| Command | What it does |
|---------|-------------|
| `/impeccable polish` | Elevate overall quality and finish |
| `/impeccable audit` | Find all design problems |
| `/impeccable critique` | Structured quality scoring with P0/P1 issues |
| `/impeccable distill` | Simplify — remove excess, clarify hierarchy |
| `/impeccable animate` | Add purposeful motion and micro-interactions |
| `/impeccable bolder` | Increase visual impact for bland interfaces |
| `/impeccable quieter` | Reduce noise for loud/busy interfaces |
| `/impeccable colorize` | Introduce strategic color to flat designs |
| `/impeccable typeset` | Fix typography — scale, pairing, rhythm |
| `/impeccable adapt` | Make responsive across breakpoints |
| `/impeccable clarify` | Fix UX copy and microcopy |
| `/impeccable harden` | Fix accessibility, performance, edge cases |
| `/impeccable optimize` | Performance — loading, rendering, animations |
| `/impeccable delight` | Add moments of joy and personality |
| `/impeccable onboard` | Improve first-time user experience |
| `/impeccable normalize` | Remove inconsistencies across components |
| `/impeccable extract` | Pull out reusable design tokens/components |
| `/impeccable shape` | Restructure layout and information architecture |
| `/impeccable arrange` | Fix alignment, grouping, visual order |
| `/impeccable layout` | Improve grid, columns, spatial structure |
| `/impeccable overdrive` | Push a design to its most ambitious version |
| `/impeccable frontend-design` | Full design system pass |
| `/impeccable teach-impeccable` | Explain the principles behind decisions |

## Anti-Pattern Detector

These 41 patterns signal AI-generated or low-quality design. Flag and fix any found:

**AI Slop Tells**
- [ ] Inter as the only typeface
- [ ] Purple-to-blue gradient anywhere
- [ ] Bounce easing on UI elements
- [ ] Dark glow / inner glow effects
- [ ] Side-tab border as active indicator
- [ ] Rounded-square icon tile above every heading
- [ ] Cards nested inside cards inside cards
- [ ] Gray text on colored background

**General Quality Issues**
- [ ] Line length > 75 characters for body text
- [ ] Cramped padding inside components
- [ ] Skipped heading levels (h1 → h3)
- [ ] Touch targets < 44px
- [ ] Color contrast below 4.5:1 for body text
- [ ] `transition: all` instead of specific properties
- [ ] Hover states without `@media (hover: hover)` guard
- [ ] Animation on keyboard-triggered actions
- [ ] `ease-in` on UI elements
- [ ] Duration > 300ms on UI animations
- [ ] `scale(0)` entry animations
- [ ] Pure `#FFFFFF` or `#000000` backgrounds/text

## Review Format

When auditing UI, always use a table:

| Issue | Location | Fix | Priority |
|-------|----------|-----|----------|
| Purple-to-blue gradient | Hero section | Replace with [specific alternative] | P0 |
| Inter only | All text | Add display face for headings | P1 |
| Touch target 32px | Mobile nav | Increase to 44px minimum | P0 |

**P0** = Blocks quality, fix immediately
**P1** = Degrades experience, fix soon

## Performance (optimize command)

- Measure first. Never optimize blindly.
- Core Web Vitals: LCP < 2.5s, INP < 200ms, CLS < 0.1
- Images: WebP/AVIF, correct `srcset`, `loading="lazy"` for below-fold
- JS: Code split at route level, tree-shake unused imports
- CSS: No unused styles, `contain: content` on isolated components
- Animations: Only `transform` + `opacity`, never layout properties
- Fonts: `font-display: swap`, preload critical fonts

## Accessibility (harden command)

- WCAG AA minimum, AAA where text is critical
- All interactive elements keyboard-navigable
- Focus indicators visible and styled (not browser default)
- `prefers-reduced-motion` respected
- `prefers-color-scheme` supported
- Screen reader tested with VoiceOver/NVDA
- No information conveyed by color alone
