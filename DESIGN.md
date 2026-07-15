# Mindbook DESIGN.md — Implementation Rules (v2)

> Read order for any design task: **[BRAND.md](./BRAND.md)** (what it feels like) → **this file** (how to build it) → **[tokens/tokens.json](./tokens/tokens.json)** (exact values). Never invent tokens, colors, components, or patterns not documented in these three files. If something is missing, propose it, document it here, then use it.
>
> **Canon source of truth:** [`prototypes/onboarding/index.html`](./prototypes/onboarding/index.html) is the built reference every new screen copies from. When this doc and that file disagree, the file wins and this doc gets fixed.

## 0. Hard rules (non-negotiable)

1. **Warm-cool but soft.** Canvas `#F3F6F6` (light) / `#0F181C` (dark), surfaces `#FCFEFD` / `#17232A`, text ink `#213238` / `#E7EEF0`. Never pure white, never pure black. Every neutral is cool (blue-green) but soft — never hospital-white, never a dead grey.
2. **Tide `#33718A` is interaction only** — CTAs, active tabs, links, focus rings. Status uses sage/peri/moon/rose tint pairs. Text on tide = `#F2FAFC` (light) / `#0D1A20` on the lighter dark-mode tide.
3. **Weight discipline.** UI (Switzer) tops at 600; display serif (Baloo 2) tops at **500**. Nothing renders at 700. `b, strong { font-weight: 600 }`.
4. **Two voices, strict split.** Baloo 2 (rounded, 500) = emotional register: greetings, screen titles, onboarding lines, mood words, empty-state headlines, the composer prompt. Switzer (sans) = every functional string: buttons, labels, meta, body. A button never wears the display face.
5. **Cards: no borders, one shadow** — `0 2px 16px rgba(35,60,70,.08)` light, radius 20px. Selected state = `outline: 2px solid var(--tide)`, not a border.
6. **Shape language: circles for meaning, softness for the rest.** Avatars, mood orbs, icon frames = circles. Buttons/inputs 14px, cards/sheets 20px, chips 999px. Media thumbs only may be 12px.
7. **Icons: outline, 1.75 stroke, round caps, inline `stroke="currentColor"`.** Never filled (only the logo + mood orbs are filled). Every icon container shows a real glyph.
8. **4px spacing grid.** Mobile gutter 20px. No 7/11/15px values.
9. **No emoji in UI. No em dashes in copy** — use ` · ` or a comma.
10. **Mobile confirmations = bottom sheets. Back-office (web) confirmations = centered dialogs.** Never crossed.
11. **Both themes are first-class.** Every screen must be built and checked in light (morning lake) AND dark (night lake). Theme is toggled via `data-theme="dark"` on the app root; persist the choice.
12. **Anonymity is visible.** Any surface where a member's content becomes visible to others states the posting identity ("Posting as QuietRiver").
13. **Safety is reachable.** Report/block on every post and comment; crisis resources ≤2 taps from anywhere.
14. **One primary CTA per screen. Canvases:** mobile 390×844 (primary), back-office web 1440. Prototypes are device-only on the deep-lake backdrop `#0A1418`, no external chrome (the theme toggle is an in-app control, not chrome).

## 1. CSS foundations (copy into every prototype)

```css
/* light · morning lake */
:root{
  --canvas:#F3F6F6; --surface:#FCFEFD; --hover:#EAF0F0; --track:#E7EEEE;
  --ink-1:#213238; --ink-2:#5C6E74; --ink-3:#8FA1A6;
  --border:#DDE6E5; --border-soft:#E6EDEC;
  --tide:#33718A; --tide-press:#285D73; --tide-dim:rgba(51,113,138,.10); --on-tide:#F2FAFC;
  --sage:#4E8D7C; --sage-dim:rgba(78,141,124,.14); --sage-deep:#33685A;
  --peri:#6B7FB3; --peri-dim:rgba(107,127,179,.13); --peri-deep:#4A5C8F;
  --moon:#C9A24B; --moon-dim:rgba(201,162,75,.16); --moon-deep:#8A6A1F;
  --rose:#C05B5B; --rose-dim:rgba(192,91,91,.10); --rose-deep:#9E4343;
  --storm:#4A4E75; --storm-dim:rgba(74,78,117,.12);
  --mood-heavy:#4A4E75; --mood-low:#5C7A99; --mood-okay:#7F958F; --mood-good:#4E9B8F; --mood-light:#C9A24B;
  --r-control:14px; --r-card:20px;
  --sh-card:0 2px 16px rgba(35,60,70,.08);
  --sh-sheet:0 -8px 40px rgba(15,24,28,.20);
  --sh-fab:0 6px 20px rgba(51,113,138,.32);
  --f-d:'Baloo 2','Trebuchet MS',sans-serif; --f-u:'Switzer',system-ui,sans-serif;
}
/* dark · night lake — set data-theme="dark" on the app root */
[data-theme="dark"]{
  --canvas:#0F181C; --surface:#17232A; --hover:#1E2D34; --track:#22333B;
  --ink-1:#E7EEF0; --ink-2:#9FB2B8; --ink-3:#6E8188;
  --border:#26363E; --border-soft:#1D2C33;
  --tide:#5CA2BC; --tide-press:#4A8DA6; --tide-dim:rgba(92,162,188,.16); --on-tide:#0D1A20;
  --sage:#6FAE9C; --sage-dim:rgba(111,174,156,.18); --sage-deep:#9FD3C4;
  --peri:#8B9CC9; --peri-dim:rgba(139,156,201,.18); --peri-deep:#B3C0E0;
  --moon:#D9B66A; --moon-dim:rgba(217,182,106,.18); --moon-deep:#E8CE92;
  --rose:#D07A7A; --rose-dim:rgba(208,122,122,.16); --rose-deep:#E5A3A3;
  --storm:#8489B8; --storm-dim:rgba(132,137,184,.18);
  --mood-heavy:#7B7FB0; --mood-low:#7C9AB9; --mood-okay:#9FB5AF; --mood-good:#6FBBAF; --mood-light:#D9B66A;
  --sh-card:0 2px 16px rgba(0,0,0,.30);
}
*{margin:0;padding:0;box-sizing:border-box;-webkit-font-smoothing:antialiased}
body{font-family:var(--f-u);color:var(--ink-1);font-size:15px;line-height:1.4}
b,strong{font-weight:600}
```

Fonts:
```html
<link href="https://api.fontshare.com/v2/css?f[]=switzer@400,500,600&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@400;500;600;700&display=swap" rel="stylesheet">
```

**Note on Baloo 2:** display renders at weight **500** (rounded and soft; heavier reads chunky). Set every display element to `font-family:var(--f-d); font-weight:500`. Baloo has **no italic** — never set `font-style:italic` on the display face; taglines are upright.

## 2. Type scale

| Use | Face / size / weight | Notes |
|---|---|---|
| Hero greeting ("How are you, really?") | Baloo 2 30/500, lh 1.24, ls −.005em | One per screen |
| Screen display title | Baloo 2 28/500 | Onboarding statements, big moments |
| Section headline / empty-state title | Baloo 2 22/500 | |
| Sheet title | Baloo 2 22/500 | |
| Card / row title | Switzer 16/600 | |
| Body (posts, stories) | Switzer 15/400, lh 1.6 | |
| UI body / buttons | Switzer 15/500–600, lh 1.4 | |
| Meta / secondary | Switzer 13/400–500, `--ink-2` | |
| Caption / timestamp | Switzer 12/400, `--ink-3` | |
| Eyebrow label | Switzer 11/600, uppercase, ls .08em, `--ink-3` | Sparingly |

## 3. Core components (mobile v1) — see the prototype for full CSS

- **Buttons** `.btn` 54px, radius 14, `var(--tide)` bg + `var(--on-tide)` text; `.btn-quiet` (tide-dim), `.btn-ghost` (transparent ink-2), `.btn-danger` (rose-dim fill; solid rose only in a confirm sheet's final action).
- **Inputs** `.inp` 50px, radius 14, `1.5px var(--border)`, surface bg; focus = tide border + `0 0 0 3px var(--tide-dim)`.
- **Cards** `.card` surface + `var(--sh-card)` + radius 20, no border. Tone on a small 36–40px circular tonal icon or a pill — never a full-card tint, never a colored left border.
- **Chips / filter pills** warm-cool track (`--track`) with a surface-white active pill in tide text. Multi-select topic chips: `1.5px var(--border)` → selected `tide-dim` bg + tide border + tide text.
- **Badges / status pills** fully round, 22px, 12px/500, tint bg + deep-tint text, no uppercase. Post-purpose map: **Need Support** rose · **Need Advice** peri · **Encouragement** sage · **My Story** storm · **Prayer Request** moon.
- **Bottom sheets** overlay `rgba(10,20,24,.55)`; sheet surface, top radius 24, drag pill, `var(--sh-sheet)`, slide-up 300ms. All overlays are sheets (pickers, confirms, audience, report, success).
- **Toast** top-center pill, tint family (sage/moon/…), auto-dismiss ~3.5s. Never dark, never bottom.
- **Bottom nav** 5 slots — Home · Rooms · ⊕ Compose (center, 52px tide circle, `--sh-fab`) · My Circle · Profile. Inactive `--ink-3`, active tide glyph + 10.5/600 label. Detail screens: no nav, back chevron in a 40px circular surface button, centered Switzer 16/600 title.
- **Avatars & identity** circular; anonymous avatars = abstract cool-palette generative patterns (no photos, no real initials). Guide avatars carry a sage ring + "Guide" sage pill. Composer always shows "Posting as {DisplayName}".
- **Mood orbs** 54px circles, soft radial highlight over the mood color on `--track`; selected = 2px ring in the mood color + breath loop. Mood word beneath in Baloo 2 500 of the deep mood tone.
- **Theme toggle** 40px circular surface button, sun/moon glyph; flips `data-theme` on the app root and persists.

## 4. Motion — water physics

- Default 220ms `cubic-bezier(.3,0,.2,1)`; sheets 300ms `cubic-bezier(.2,.9,.25,1)`.
- **Breath** — orbs + success moments scale 1→1.04→1 on a 3.2–3.6s loop.
- **Ripple** — an outlined ring expands from center once and fades (`scale .5→1.9, opacity .45→0`). Used on the splash mark and the Circle-reveal. Never bounces.
- Screen entrance: fade + 14px rise. No confetti, no springy overshoot.

## 5. Accessibility & sensitivity floor

- Body contrast ≥ 4.5:1, 18px+ ≥ 3:1 — verified in both themes. Tap targets ≥ 44px. Focus rings visible (tide).
- Mood data is private; no UI ever shows another member's mood.
- Report/destructive flows use calm language, confirm via sheet, never guilt-trip copy.

## 6. Where things live

| What | Where |
|---|---|
| PRD + product docs | `docs/` |
| Brand & creative direction | `BRAND.md` |
| Tokens | `tokens/tokens.json` |
| Implementation rules (this) | `DESIGN.md` |
| Logo assets | `assets/logo/` |
| Interactive HTML prototypes | `prototypes/<flow-slug>/index.html` |
| Flutter app | `app/` (later) |
| Backend (Spring Boot) | `backend/` (later) |

Prototype-first: every flow ships as a clickable device-only HTML prototype (light + dark) before any Flutter code.

**Canon prototypes (copy from these):**
- `prototypes/onboarding/` — splash, auth, anonymous identity, house rules, topics, communities, Circle reveal, first check-in, home feed, composer.
- `prototypes/circle/` — Circle space (identity crest, member ring, guided-conversation card, feed with milestone posts), post detail (threaded replies + reply bar), Community page (hero + stats + your-Circle shortcut + moderator announcement + featured resources + community feed), and the safety set: post-actions sheet, report sheet (with self-harm-concern → crisis escalation), block confirm, crisis-support sheet, members sheet.

**Components introduced in prototype 02** (reuse verbatim): `.circle-id`/`.circle-crest`/`.member-ring`; `.guided` (guided-conversation card); `.post` + `.milestone` variant; post-purpose pills `.p-support/.p-advice/.p-enc/.p-story/.p-prayer`; `.comment` thread + `.reply-bar`; `.com-hero`/`.cstat`/`.yc-card`/`.announce`/`.res-card`; safety sheets `.act-row`/`.reason`/`.crisis-line`/`.mem-row` + `.role-chip`. **Horizontal scroll rows inside a flex-column `.body` must carry `flex-shrink:0`** or they collapse.
