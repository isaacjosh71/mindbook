# Mindbook DESIGN.md — Implementation Rules

> Read order for any design task: **[BRAND.md](./BRAND.md)** (what it feels like) → **this file** (how to build it) → **[tokens/tokens.json](./tokens/tokens.json)** (exact values). Never invent tokens, colors, components, or patterns not documented in these three files. If something is missing, propose it, document it here, then use it.

## 0. Hard rules (non-negotiable)

1. **Warm everything.** Canvas `#FAF5EE`, surfaces `#FFFCF8`, text ink `#2E2433`. Never pure white, never pure black, never a cool/blue-leaning grey.
2. **Clay `#B9542F` is interaction only** — CTAs, active tabs, links, focus rings. Status uses sage/dusk/honey/rose tint pairs. Text on clay = `#FFF9F4`, never pure white, never dark.
3. **Weight ceiling 600.** Nothing renders at 700. `b, strong { font-weight: 600 }` in every base stylesheet.
4. **Two voices, strict split.** Sentient (serif) = emotional register: greetings, screen-title moments, onboarding lines, mood words, empty-state headlines. Author (sans) = every functional string: buttons, labels, meta, body copy. A button never wears the serif.
5. **Cards: no borders, one shadow** — `0 2px 16px rgba(76,54,44,0.08)`, radius 20px. Selected state = `outline: 2px solid var(--clay)`, not border.
6. **Circles for meaning, softness for everything else.** Avatars, mood orbs, icon frames = perfect circles. Buttons/inputs 14px, cards/sheets 20px, chips 999px. Media thumbs only may be 12px rounded squares.
7. **Icons: outline, 1.75 stroke, round caps, inline `stroke="currentColor"`.** Never filled (only the logo + mood orbs are filled). Every icon container shows a real glyph.
8. **4px spacing grid.** Mobile gutter 20px. No 7/11/15px values.
9. **No emoji in UI. No em dashes in copy** — use ` · ` or a comma.
10. **Mobile confirmations = bottom sheets. Back-office (web) confirmations = centered dialogs.** Never crossed.
11. **Anonymity is visible**: any surface where a member's content becomes visible to others must state the posting identity ("Posting as HopefulSoul").
12. **Safety is reachable**: report/block affordance on every post and comment; crisis resources ≤2 taps from anywhere.
13. **One primary CTA per screen.**
14. **Canvases**: mobile 390×844 (primary product), back-office web 1440. Prototypes are device-only on a dark warm backdrop `#171219`, no external chrome.

## 1. CSS foundations (copy into every prototype)

```css
:root{
  /* materials */
  --paper:#FAF5EE; --surface:#FFFCF8; --hover:#F3ECE3; --track:#F0E8DD;
  --ink-1:#2E2433; --ink-2:#6E6172; --ink-3:#9C92A1;
  --border:#EBE1D6; --border-soft:#F2EAE0;
  /* brand */
  --clay:#B9542F; --clay-press:#9C4426; --clay-dim:rgba(185,84,47,.10); --on-clay:#FFF9F4;
  /* status */
  --sage:#5E8C63; --sage-dim:rgba(94,140,99,.14); --sage-deep:#3F6B45;
  --dusk:#567A9B; --dusk-dim:rgba(86,122,155,.13); --dusk-deep:#3E5F7E;
  --honey:#D9982B; --honey-dim:rgba(217,152,43,.16); --honey-deep:#8A5B0F;
  --rose:#C24545; --rose-dim:rgba(194,69,69,.10); --rose-deep:#A03030;
  /* mood ramp */
  --mood-heavy:#4E3A5C; --mood-low:#567A9B; --mood-okay:#A5907C;
  --mood-good:#D9982B; --mood-light:#5E8C63;
  /* shape + elevation */
  --r-control:14px; --r-card:20px; --r-media:12px;
  --sh-card:0 2px 16px rgba(76,54,44,.08);
  --sh-sheet:0 -8px 40px rgba(46,36,51,.18);
  --sh-fab:0 6px 20px rgba(185,84,47,.32);
  /* type */
  --f-display:'Sentient',Georgia,serif;
  --f-ui:'Author',system-ui,sans-serif;
}
*{margin:0;padding:0;box-sizing:border-box;-webkit-font-smoothing:antialiased}
body{font-family:var(--f-ui);color:var(--ink-1);font-size:15px;line-height:1.4}
b,strong{font-weight:600}
button{font-family:var(--f-ui);border:none;background:none;cursor:pointer;color:inherit}
```

Fonts:
```html
<link href="https://api.fontshare.com/v2/css?f[]=sentient@400,401,500,501,600&f[]=author@400,500,600&display=swap" rel="stylesheet">
```

## 2. Type scale

| Use | Face / size / weight | Notes |
|---|---|---|
| Hero greeting ("How are you, really?") | Sentient 32/600, lh 1.2, ls −0.01em | One per screen max |
| Screen display title | Sentient 26/600 | Onboarding statements, big moments |
| Section headline / empty-state title | Sentient 22/500 | |
| Card / row title | Author 16/600 | |
| Body (posts, stories) | Author 15/400, lh 1.6 | |
| UI body / buttons | Author 15/500–600, lh 1.4 | |
| Meta / secondary | Author 13/400–500, `--ink-2` | |
| Caption / timestamp | Author 12/400, `--ink-3` | |
| Eyebrow label | Author 11/600, uppercase, ls 0.08em, `--ink-3` | Sparingly |

## 3. Core components (mobile v1)

### Buttons
```css
.btn{height:54px;width:100%;border-radius:var(--r-control);background:var(--clay);
  color:var(--on-clay);font-size:15.5px;font-weight:600;display:flex;
  align-items:center;justify-content:center;gap:8px;transition:background .22s}
.btn:active{background:var(--clay-press)}
.btn-quiet{background:var(--clay-dim);color:var(--clay)}          /* secondary */
.btn-ghost{background:transparent;color:var(--ink-2);height:44px} /* tertiary  */
.btn-danger{background:var(--rose-dim);color:var(--rose-deep)}    /* destructive: tinted, never solid red */
```
Solid rose fill only inside a confirmation sheet's final action.

### Inputs
50px height, 14px radius, `1.5px solid var(--border)`, surface bg; focus = clay border + `box-shadow:0 0 0 3px var(--clay-dim)`. Labels 13/500 `--ink-2` above the field.

### Cards
`.card { background:var(--surface); border-radius:var(--r-card); box-shadow:var(--sh-card); padding:16px 18px; }` — no border ever. Status tone lives on a small 36px circular tonal icon or a pill, never a full-card tint, never a colored left border.

### Chips / filter pills
Warm track behind, surface-white active pill with clay text:
```css
.chips{display:flex;gap:6px;background:var(--track);border-radius:999px;padding:4px}
.chip{height:34px;padding:0 16px;border-radius:999px;font-size:13.5px;font-weight:500;color:var(--ink-2)}
.chip.on{background:var(--surface);color:var(--clay);font-weight:600;box-shadow:var(--sh-card)}
```
Multi-select topic chips (onboarding) are standalone pills: `border:1.5px solid var(--border)` → selected: `background:var(--clay-dim); border-color:var(--clay); color:var(--clay)`.

### Badges & status pills
22px tall, 12px/500, 999px radius (fully round — this app has no square badges), tint bg + deep-tint text, no uppercase.
Post-purpose mapping: **Need Support** rose-dim · **Need Advice** dusk-dim · **Encouragement** sage-dim · **My Story** honey-dim · **Prayer Request** plum tint `rgba(78,58,92,.12)/#4E3A5C`.

### Bottom sheets (all mobile overlays)
Overlay `rgba(33,27,38,.5)`; sheet: surface bg, top radius 24px, drag pill 36×4 `--track`, padding 8px 20px 32px, `--sh-sheet`, slide-up 300ms. Pickers, confirmations, audience selection, report flows, success moments — all sheets.

### Toast
Top-center pill, tint family by type (sage/dusk/honey/rose), 13px/500 deep-tint text, auto-dismiss ~3.5s. Never dark, never bottom-anchored.

### Bottom nav (root screens only)
5 slots: **Home · Communities · ⊕ Compose (center, 52px clay circle, `--sh-fab`) · My Circle · Profile**. Inactive `--ink-3`, active clay glyph + 10.5px/600 label. Detail screens: no bottom nav, back chevron in a 40px circular surface button, centered screen title (Author 16/600).

### Avatars & identity
Circular always. Anonymous avatars = abstract warm-palette generative patterns (no photos, no real initials). Guide avatars carry a 2px sage ring + tiny "Guide" sage pill. The composer always shows "Posting as **{DisplayName}**" with a swap affordance where allowed.

### Mood orbs (check-in)
56px circles in a 5-across row, each a soft radial fill of its mood color on `--track` base; selected = 2px ring in mood color + breathing animation (`scale 1→1.035→1`, 3.2s loop). Mood word beneath in Sentient 15/500 of the deep mood tone.

## 4. Screen anatomy (mobile)

- **Phone shell**: 390×844, radius 32px, on `#171219` backdrop, `box-shadow: 0 50px 130px rgba(0,0,0,.65), inset 0 0 0 1px rgba(255,255,255,.05)`. Device-only, zero external chrome.
- **Status bar**: standard 3-icon set (time + signal + wifi + battery), ink on paper screens, cream on plum/dark heros.
- **Home**: warm greeting block (Sentient, time-aware: "Good evening, QuietRiver"), check-in nudge card (or today's mood if done), composer prompt card "What's going on with you today?", Circle activity, then Community recommendations. The page scrolls as one.
- **Rhythm**: section eyebrow → 8px → content; same-kind cards stack at 12–16px; unlike sections 28px+.
- Root screens keep bottom nav; drilled-in screens never do.

## 5. Accessibility & sensitivity floor

- Text contrast ≥ 4.5:1 (body) / 3:1 (18px+). All tint-pair combos in tokens.json pass on their dim backgrounds.
- Tap targets ≥ 44px. Focus states visible (clay ring).
- Mood data is private by default; no UI ever shows another member's mood.
- Destructive/report flows: calm language, confirm via sheet, never guilt-trip copy.

## 6. Where things live

| What | Where |
|---|---|
| PRD + product docs | `docs/` |
| Brand & creative direction | `BRAND.md` |
| Tokens | `tokens/tokens.json` |
| Implementation rules (this) | `DESIGN.md` |
| Interactive HTML prototypes | `prototypes/<flow-slug>/index.html` |
| Starter template (once canon exists) | `templates/` |
| Flutter app | `app/` (later) |
| Backend (Spring Boot) | `backend/` (later, or its own repo) |

Prototype-first workflow: every flow ships as a clickable device-only HTML prototype before any Flutter code. The first built flow (onboarding → check-in → home) becomes the **canon source** future flows copy from; components extracted from it get documented here as they stabilize.
