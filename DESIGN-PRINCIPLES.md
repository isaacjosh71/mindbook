# Mindbook Design System — Operating Principles

Distilled from studying a mature production design system (Rechaj, design.rechaj.com). These are the *structural* lessons we carry over — Mindbook's actual brand, tokens, and components will be defined fresh from its PRD.

## 1. Layered documentation, strict lookup order

A design system is a **decision-elimination machine**. Every question ("what button? what tab? what modal?") must have exactly one place that answers it, consulted in a fixed order:

1. **PATTERNS.md** — per-platform widget recipe book. First file opened for any new design. Maps every UI atom (button, tab, table, badge, sheet, toast…) to one canonical class + concrete spec per form factor.
2. **DESIGN.md** — global tokens, typography, spacing, hard rules, cross-platform invariants.
3. **tokens/tokens.json** — machine-readable W3C DTCG token export. The precise values.
4. **Component library / canon extractions** — verbatim ground-truth markup.
5. **Precedent screens** — composition tie-breakers only, *never* canon (precedent drifts).
6. **Ask the human** — only about scope/persona, never about widget choice.

Never invent. If a token/component isn't documented, it doesn't exist yet — document it first, then use it.

## 2. Tokens first, semantic aliases second

- One brand color scale (11 steps light→dark) with a single canonical step; neutral scale; one accent scale used sparingly.
- Semantic layer on top: `--bg` (page canvas, off-white — never pure white), `--bg-surface` (cards/modals), `--bg-hover`, `--border`/`--border-soft`, `--text-1/2/3`.
- Interaction color ≠ status color: the brand color is for CTAs/focus/active states only; status semantics get their own families (green=done, blue=in-progress, amber=pending, red=failed, grey=neutral) with tinted-bg + strong-tint-text pairs.
- Everything exported as CSS custom properties AND a DTCG tokens.json so tooling and agents consume the same source.

## 3. Hard rules — few, memorable, non-negotiable

The Rechaj set worth emulating (adapt values to Mindbook's brand):

- **Strict 4px spacing grid.** No 7/11/15px ever.
- **Weight discipline:** headings/titles/labels = 600; 700 reserved for display numerals + splash display titles only. `b,strong { font-weight: 600 }` in base styles.
- **Cards have no borders — shadow only** (one precise, very subtle card shadow token). Selected state = outline, not border.
- **One badge spec everywhere:** small, 500 weight, small radius, no uppercase, tinted bg.
- **Icons are one style everywhere** (Rechaj: outline `stroke=currentColor`, never filled; circular icon containers). Pick one style, enforce it.
- **Per-platform confirmation pattern:** web = centered modal; mobile/tablet = bottom sheet. Never crossed.
- **One primary CTA per view.** Primary button = exact brand bg + fixed text color (Rechaj: green + dark text, never white-on-green).
- **Sibling-spacing rule:** label→content 8–12px; same-kind siblings 16px; unlike sections 24px+. One source of vertical rhythm per screen.
- No emojis in UI. No em dashes in copy (use ` · `).
- Fixed canvases: one width per form factor (web 1440 / tablet 834×1194 / mobile 390×844), no arbitrary sizes.
- Prototypes are device-only on a dark backdrop — zero external chrome.

## 4. Canon + starters + lint = consistency at scale

The mechanism that keeps many parallel authors consistent:

- **Source-of-truth apps per platform** — named reference files whose components are copied verbatim, plus written extractions of them.
- **Starter templates per form factor** — a new flow always begins from a template that ships the shell, tokens, tabs, table, overlay, toast, and buttons pre-wired; authors fill in *content only*, never restyle the shell.
- **A canon linter run in CI** — mechanical rules (banned legacy classes, dark-pill tabs, wrong overlay type per platform, invisible icon glyphs, title length caps) fail the merge. Drift is caught by machine, not by review vigilance.
- **Explicit deprecation table** — when the canon evolves, old atoms are listed with their replacements and the lint enforces migration.

## 5. Content conventions are part of the system

- Persona-driven flows: every flow belongs to a named persona with a realistic name, email, and role.
- Realistic data everywhere: defined ID formats (`XX-YYMMDD-NNN` style), real human names — never "User 1234".
- Copy rules: short single-line flow titles (~3 words, hard cap), page titles are short noun phrases, IDs live in body meta not titles.
- Every product carries its own `docs/prd.md`, `changelog.md` (Keep a Changelog), and scoped `DESIGN.md` overrides.

## 6. Routing table for generated work

A "where does X live" table (flow → `products/<x>/flows/<persona>/index.html`, screen → `screens/`, pattern → `patterns/`, token → `tokens.json`, spec → `specs/`) so no one ever guesses a path.

---

*Next step: receive the Mindbook PRD → define brand + tokens → write DESIGN.md + PATTERNS.md → build starter templates → then, and only then, design flows.*
