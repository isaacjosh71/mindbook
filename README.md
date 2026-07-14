# Mindbook

The master Mindbook design repository — single source of truth for the product's designs, prototypes, PRDs, tokens, and design canon.

**Status: awaiting PRD.** No design work begins until the PRD lands in `docs/prd.md`. The repository structure, tokens, and canon will be derived from it — nothing here is invented ahead of the product definition.

## Planned shape (to be confirmed against the PRD)

```
mindbook/
  README.md            ← you are here
  DESIGN-PRINCIPLES.md ← the operating philosophy for this design system
  docs/prd.md          ← the PRD (to be added)
  tokens/tokens.json   ← W3C DTCG design tokens (once brand is defined)
  DESIGN.md            ← global tokens + hard rules (derived from tokens)
  PATTERNS.md          ← per-platform widget recipe book
  templates/           ← per-form-factor flow starters
  products/            ← flows, screens, prototypes
  scripts/             ← canon lint + tooling
```
