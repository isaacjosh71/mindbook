# Mindbook Brand & Creative Direction

> The single source of truth for what Mindbook looks, sounds, and feels like. Tokens live in [tokens/tokens.json](./tokens/tokens.json); implementation rules in [DESIGN.md](./DESIGN.md).

## 1. The concept — *a lamplit room*

Think about **when** someone opens Mindbook: late at night when the thoughts are loud, on a danfo after a hard day, between lectures, after the call that broke them. They are not coming to be entertained. They are coming to put something heavy down.

So Mindbook is not a dashboard, not a clinic, and not a social feed. It is **a lamplit room** — warm, quiet, slightly dim, with a few trusted people in it. Everything in the design serves that image:

- **Paper, not screens.** Warm cream surfaces, ink instead of black, a serif voice for the moments that matter. The "book" in Mindbook is literal: this is a shared journal, not a timeline.
- **Lamplight, not neon.** One warm clay accent that glows against the paper. No gradients-of-the-week, no glassmorphism, no electric anything.
- **Circles, everywhere.** The Circle is the product's heart, so the circle is the brand's core shape — avatars, mood orbs, member rings, the logo's embrace. Soft corners on everything else.
- **Quiet, not silent.** Calm ≠ clinical. The room has warmth: Nigerian directness in the copy ("Do life alone? Nah."), human textures, gentle motion like breathing.

### What Mindbook is NOT (anti-references)
- ❌ Calm/Headspace clone — no meditating silhouettes, no lotus, no lavender-teal gradient wash
- ❌ Clinical health app — no medical blue, no charts-first, no "patient" energy
- ❌ Social media — no infinite scroll dopamine, no like-counters as scoreboard, no red badge anxiety
- ❌ Church app — Faith is one Community, not the brand
- ❌ Rechaj or any sibling — no electric green, no cool-grey off-whites, no General Sans

## 2. Color — *paper, ink, clay*

The palette is built from three materials: **paper** (warm cream surfaces), **ink** (deep plum-charcoal text — never pure black), and **clay** (the terracotta accent: earthy, Nigerian, human, warm). Support tones are dusk blue, sage green, and honey amber — all muted, all warm-leaning.

| Role | Token | Value | Notes |
|---|---|---|---|
| Brand / primary action | `clay.6` | **#B9542F** | Terracotta. CTAs, active states, focus. Warm cream `#FFF9F4` text on clay (AA at this depth). |
| Clay pressed/hover | `clay.7` | #9C4426 | |
| Clay tint | `clay-dim` | rgba(185,84,47,.10) | Selected/hover washes, tonal icon frames |
| Page canvas | `paper` | **#FAF5EE** | Warm cream — never pure white, never cool |
| Card surface | `surface` | #FFFCF8 | Warm near-white; floats on paper |
| Ink primary | `ink.1` | **#2E2433** | Plum-charcoal. All primary text. Never #000. |
| Ink secondary | `ink.2` | #6E6172 | |
| Ink muted | `ink.3` | #9C92A1 | |
| Border | `border` | #EBE1D6 | Warm; hairlines only, never on cards |
| Success / growth | `sage.6` | #5E8C63 | Tint rgba(94,140,99,.14), text-on-tint #3F6B45 |
| Info / calm | `dusk.6` | #567A9B | Tint rgba(86,122,155,.13), text-on-tint #3E5F7E |
| Attention | `honey.6` | #D9982B | Tint rgba(217,152,43,.16), text-on-tint #8A5B0F |
| Danger (muted) | `rose.6` | #C24545 | Tint rgba(194,69,69,.10). Soft — never alarm-red screaming at a hurting person. |
| Night canvas (dark mode, later) | `night` | #211B26 | Plum-black, warm |

**Rules**
- Clay is for **interaction** (buttons, active tabs, links, focus) — never for status.
- Status semantics: sage = positive/growth · dusk = info/in-progress · honey = attention · rose = danger/report. Tinted-bg + deep-tint-text pairs, same recipe everywhere.
- Every neutral in the app is **warm** (yellow-plum leaning). If a grey looks blue, it's wrong.

### Mood ramp (check-ins)

Five felt states, named in body language — not clinical terms, not emoji:

| Mood | Color | Orb idea |
|---|---|---|
| **Heavy** | deep plum #4E3A5C | low, dense orb |
| **Low** | dusk #567A9B | drifting orb |
| **Okay** | warm taupe #A5907C | level orb |
| **Good** | honey #D9982B | rising orb |
| **Light** | sage #5E8C63 | floating orb |

Mood orbs are the app's one expressive illustration system: soft circular gradients/shapes, consistent geometry, no faces.

## 3. Typography — *a book that talks like a friend*

| Layer | Face | Use |
|---|---|---|
| **Display serif** | **Sentient** (Fontshare) | The "book voice": greetings ("How are you, really?"), screen-title moments, onboarding statements, empty-state headlines, big mood words. Weights 400/500/600 + italic for warmth. |
| **UI sans** | **Author** (Fontshare) | Everything functional: body, labels, buttons, meta. Humanist and warm, nothing like General Sans/Inter/Satoshi defaults. Weights 400/500/600. |
| Numerals/meta mono | system mono, sparingly | timestamps, IDs in back office |

```html
<link href="https://api.fontshare.com/v2/css?f[]=sentient@400,401,500,501,600&f[]=author@400,500,600&display=swap" rel="stylesheet">
```

**Rules**
- Body is **15px** (support text deserves comfort; 14 is for meta), line-height 1.6 for reading, 1.4 for UI.
- Weight ceiling: **600**. No 700 anywhere in v1 — even display numerals sit at 600 in serif; the serif carries the presence. `b, strong { font-weight: 600 }`.
- Serif = emotional register only. If a string is functional (button, tab, form label), it's Author. If it's the room speaking to you, it's Sentient.
- No uppercase-with-tracking labels except tiny section eyebrows (11px/600/0.08em, used sparingly).

## 4. Shape, elevation, texture

- **Radius scale:** cards & sheets **20px** · buttons/inputs **14px** · chips/pills 999px · avatars/mood orbs/icon frames **50%**.
- **Cards have no borders.** One warm shadow only: `0 2px 16px rgba(76,54,44,0.08)` (`--sh-card`). Sheets get `0 -8px 40px rgba(46,36,51,0.18)`.
- **Icon containers are circular** tonal frames (tint bg + deep-tint glyph). Photos/media may be rounded squares (12px).
- **Spacing:** strict 4px grid. Mobile gutter 20px. Generous breathing room is a feature — when in doubt, add space, not elements.
- Texture: none in v1 (no noise/paper grain overlays yet); warmth comes from color and type.

## 5. Iconography

- **Outline icons, 1.75 stroke, round caps/joins, `stroke="currentColor"` inline on every `<svg>`.** Never filled glyphs (the two-tone logo and mood orbs are the only filled marks).
- Slightly **rounded, soft geometry** — icons should feel drawn by a calm hand, not stamped by a grid.
- 20px glyph inside a 40px circular tonal frame (16px inside 32px for compact rows).

## 6. Logo — *the open book, held*

Concept: **an open book cradled inside a circle** — the shared journal, held by the Circle. Two-tone: clay left page, ink right page, on a paper-tint ring.

v1 mark (to be refined visually in the first prototype pass):

```html
<svg viewBox="0 0 64 64" fill="none" xmlns="http://www.w3.org/2000/svg">
  <circle cx="32" cy="32" r="30" fill="#F4E7D9"/>
  <path d="M32 20c-5.5-4.2-13.5-4.6-18-2.4v26.2c4.5-2.2 12.5-1.8 18 2.4V20z" fill="#B9542F"/>
  <path d="M32 20c5.5-4.2 13.5-4.6 18-2.4v26.2c-4.5-2.2-12.5-1.8-18 2.4V20z" fill="#2E2433"/>
</svg>
```

Wordmark: **mindbook** — lowercase, Sentient 600, ink, letter-spacing −0.01em. Lowercase because the brand sits beside you, it doesn't announce itself.

## 7. Voice & copy

- **Warm Nigerian directness.** "Do life alone? Nah." is the register: short, human, zero jargon. Not corporate-wellness ("Unlock your best self" ❌), not clinical ("Log your symptoms" ❌).
- The app asks like a friend: **"How are you, really?"** (check-in) · **"What's going on with you today?"** (composer) · "Small circle, real ones" (Circle intro).
- Never diagnose, never prescribe, never toxic-positivity ("Good vibes only" ❌). Acknowledge first, encourage second.
- Anonymity is stated visibly and often: "Posting as **HopefulSoul** · your real identity stays yours."
- No emoji in UI chrome. No em dashes in copy — use ` · ` or a comma.
- Crisis copy is calm, direct, and always one tap away.

## 8. Motion

- Default 220ms `cubic-bezier(0.3, 0, 0.2, 1)`; sheets 300ms `cubic-bezier(0.2, 0.9, 0.25, 1)`.
- One signature: **breathing** — the check-in orb and success moments scale 1→1.035→1 on a slow 3.2s loop. Calm, alive, never bouncy.
- No confetti, no fireworks. Milestones glow (soft honey halo), they don't explode.

## 9. UX doctrine (product-level rules)

1. **Calm by default** — no engagement bait, no streak-shaming, no red-badge anxiety; notification copy is gentle and skippable.
2. **Anonymity you can see** — the user's anonymous identity is visibly confirmed at every point of exposure (composer, comments, join screens).
3. **Small rooms first** — the Circle is home base; Community feeds are secondary; there is no global public firehose.
4. **Consent at every share** — audience picker is explicit on every post; nothing defaults to wider than the Circle.
5. **Warmth over metrics** — reactions are "encouragements", counts stay quiet and small; no leaderboards on pain.
6. **Safety one tap away** — report/block on every piece of content; crisis resources reachable from anywhere in ≤2 taps.
7. **The ritual gets space** — check-in and posting are full, unhurried moments (own screens, breathing motion), not cramped modals.

## 10. Personas & naming conventions

| Context | Persona | Anonymous handle |
|---|---|---|
| Primary member (Seeking Support) | Chidera, 23, final-year UNILAG student | **QuietRiver** |
| Supporter member | Emeka, 29, product designer, healed from burnout | **SteadyOak** |
| Verified Guide | Amara, 31, navigated grief | **StillWaters** (Guide ring) |
| Moderator / back office | Folake Adeyemi, community ops | (real name, back office only) |

Display names: two gentle words, PascalCase (HopefulSoul, BraveHeart, StillHealing). Avatars: circular, abstract warm-palette patterns — never photos, never initials of real names.

ID formats (backend/back-office): user `MB-U-NNNNNN` · community `MB-C-NNNN` · circle `MB-C-NNNN-CIR-NN` · post `MB-P-NNNNNNNN` · report `RPT-YYMMDD-NNN`.
