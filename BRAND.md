# Mindbook Brand & Creative Direction — v2

> The single source of truth for what Mindbook looks, sounds, and feels like. Tokens live in [tokens/tokens.json](./tokens/tokens.json); implementation rules in [DESIGN.md](./DESIGN.md). v2 replaces the v1 "paper & clay" direction with a cool, calm water-based identity.

## 1. The concept — *a quiet lake at dusk*

Mindbook is where people come to put a feeling down. The image that carries the whole brand: **a still lake in the evening — a single drop lands, the water receives it, the ripples widen and settle.**

It maps 1:1 to the product:

- **The drop** = the feeling you've been carrying (the mood orb, the post you finally write).
- **The water** = the app: calm, deep, judgment-free, it receives everything without splashing back.
- **The ripple** = your Circle: one share reaching a small ring of people, then settling into calm.

Everything in the design serves that image: cool misty surfaces, deep-water ink, one calm tide-blue for action, a single moonlight-gold accent for warmth, motion that behaves like water (rises, ripples, breathes — never bounces).

### What Mindbook is NOT (anti-references)
- ❌ Calm/Headspace clone — no meditating silhouettes, no purple-navy gradient wash, no cartoon blobs
- ❌ Clinical health app — cool ≠ cold; no hospital blue-on-white, no charts-first energy
- ❌ Social media — no dopamine loops, no like scoreboards, no red badge anxiety
- ❌ AI-default kit — no Inter/Satoshi, no teal-lavender gradient, no glassmorphism
- ❌ Anything from sibling products (no Rechaj green, no General Sans)

## 2. Color — *mist, deep water, moonlight*

Cool and calm, built from three materials: **mist** (cool off-white surfaces), **deep water** (blue-green ink, never black), and **tide** (the calm ocean-blue action color). One warm note — **moonlight gold** — so the coolness never turns clinical. Both light and dark themes ship from day one; dark is the "night lake".

### Light theme

| Role | Token | Value | Notes |
|---|---|---|---|
| Brand / primary action | `tide.6` | **#33718A** | Deep calm ocean blue. CTAs, active states, links, focus. Text on tide = `#F2FAFC`. |
| Tide pressed | `tide.7` | #285D73 | |
| Tide tint | `tide-dim` | rgba(51,113,138,.10) | Selected washes, tonal icon frames |
| Page canvas | `mist` | **#F3F6F6** | Cool off-white — never pure white |
| Card surface | `surface` | #FCFEFD | |
| Ink primary | `ink.1` | **#213238** | Deep-water slate. Never #000. |
| Ink secondary | `ink.2` | #5C6E74 | |
| Ink muted | `ink.3` | #8FA1A6 | |
| Border | `border` | #DDE6E5 | Hairlines/inputs only, never cards |
| Growth / success | `sage.6` | #4E8D7C | Cool sea-green. Tint rgba(78,141,124,.14), deep #33685A |
| Info / calm | `peri.6` | #6B7FB3 | Periwinkle. Tint rgba(107,127,179,.13), deep #4A5C8F |
| Warmth / celebration | `moon.6` | #C9A24B | Moonlight gold — the one warm note. Tint rgba(201,162,75,.16), deep #8A6A1F |
| Danger (muted) | `rose.6` | #C05B5B | Tint rgba(192,91,91,.10), deep #9E4343. Soft, never alarm-red. |
| Storm (mood/story) | `storm.6` | #4A4E75 | Indigo-storm. Tint rgba(74,78,117,.12) |

### Dark theme — *the night lake*

| Role | Value |
|---|---|
| Canvas | `#0F181C` · Surface `#17232A` · Hover `#1E2D34` · Track `#22333B` |
| Ink | `#E7EEF0` / `#9FB2B8` / `#6E8188` |
| Borders | `#26363E` / `#1D2C33` |
| Tide (action) | **#5CA2BC** with dark text `#0D1A20` on fills |
| Moon `#D9B66A` · Sage `#6FAE9C` · Peri `#8B9CC9` · Rose `#D07A7A` |
| Tints | same rgba recipes at slightly higher alpha; tinted text uses the light-theme main colors |

**Rules**
- Tide is for **interaction only** — never status. Status: sage = positive/growth · peri = info/in-progress · moon = attention/celebration · rose = danger/report.
- Every neutral is **cool** (blue-green leaning) but soft — if a surface reads hospital-white or the grey feels dead, warm it a step with green, not yellow.
- Moon gold is precious: celebration glows, the logo drop, "Good" moods, tiny highlights. Never large fills.

### Mood ramp (check-ins) — *weather over water*

| Mood | Color | Feels like |
|---|---|---|
| **Heavy** | storm indigo #4A4E75 | storm over the lake |
| **Low** | rain slate #5C7A99 | grey drizzle |
| **Okay** | mist green-grey #7F958F | fog lifting |
| **Good** | clear aqua #4E9B8F | clean water |
| **Light** | dawn gold #C9A24B | sun on the surface |

Orbs stay circular, soft radial highlight, no faces, no emoji.

## 3. Typography — *soft voice, clear hands*

| Layer | Face | Use |
|---|---|---|
| **Display** | **Baloo 2** (Google Fonts) | The app's voice: greetings ("How are you, really?"), screen titles, onboarding statements, mood words. A soft rounded sans — warm, friendly, unhurried. Rendered at **weight 500**. No italic (Baloo has none) — taglines are upright. |
| **UI** | **Switzer** (Fontshare) | Everything functional: body, labels, buttons, meta. Quiet, highly legible, disappears behind the content. Weights 400/500/600. |

```html
<link href="https://api.fontshare.com/v2/css?f[]=switzer@400,500,600&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Baloo+2:wght@400;500;600;700&display=swap" rel="stylesheet">
```

**Rules**
- Body 15px, reading line-height 1.6, UI 1.4. UI weight ceiling **600**; display renders at **500** — nothing shouts in this app. `b, strong { font-weight: 600 }`.
- Baloo = emotional register only. Buttons, tabs, form labels are always Switzer.
- Lowercase wordmark: **mindbook** — Baloo 2 500, letter-spacing -0.01em.

## 4. Logo — *the mind that reads as an open book*

The mark is **a mind — two hemispheres — drawn so the central fissure also reads as the spine of an open book**. Two ideas in one shape: the *mind* (this is emotional inner life) and the *open book* (Mind-book — a shared, honest page). Clean and uncluttered; no motif inside.

Outline in a **tide → storm** vertical gradient (calm at the crown, deeper at the base). Files: `assets/logo/mark.svg` (in-app, on mist/dark surfaces) and `assets/logo/app-icon.svg` (night-lake gradient ground, lighter strokes + soft glow so it reads on dark; export square, platform masks it).

Construction rules: symmetric about x-centre; hemispheres are soft rounded lobes (never anatomical/veiny — this is calm, not clinical); the centre spine is essential (it carries the open-book read); nothing else inside. On the splash the mark scales in and settles into the **breath** loop while two **ripple** rings expand outward once.

Wordmark: **mindbook** — lowercase, Baloo 2 500, letter-spacing -0.01em. Lowercase because the brand sits beside you, it doesn't announce itself.

## 5. Shape, elevation

- Radius: cards & sheets **20px** · buttons/inputs **14px** · chips/pills 999px · orbs/avatars/icon frames **50%**.
- Cards: no borders, one cool shadow `0 2px 16px rgba(35,60,70,.08)` (light) — in dark, elevation comes from the lighter surface color, shadow stays subtle.
- Icon containers circular, outline icons 1.75 stroke, round caps, `stroke="currentColor"` inline. Only the logo and mood orbs are filled.
- Strict 4px grid, 20px mobile gutter. Space is the loudest design element in a calm app.

## 6. Motion — *water physics*

- Default 220ms `cubic-bezier(0.3, 0, 0.2, 1)`; sheets 300ms `cubic-bezier(0.2, 0.9, 0.25, 1)`.
- Two signatures:
  - **Breath** — orbs and success moments scale 1→1.035→1 on a 3.2s loop.
  - **Ripple** — celebration/arrival moments expand a soft ring outward once (logo splash, Circle reveal, check-in saved). Ripples settle; they never bounce.
- No confetti, no fireworks, no springy overshoot.

## 7. Voice & copy

Unchanged from v1 — it was never the problem:
- Warm Nigerian directness: "Do life alone? Nah."
- Ask like a friend: "How are you, really?" · "What's going on with you today?"
- Acknowledge first, encourage second. Never diagnose, never toxic-positivity.
- Anonymity stated visibly: "Posting as **HopefulSoul** · your real identity stays yours."
- No emoji in UI. No em dashes — use ` · ` or a comma. Crisis help is calm, direct, ≤2 taps away.

## 8. UX doctrine

1. **Calm by default** — no engagement bait, no streak-shaming, no red-badge anxiety.
2. **Anonymity you can see** — identity confirmed at every point of exposure.
3. **Small rooms first** — the Circle is home; no global firehose.
4. **Consent at every share** — explicit audience picker, never defaults wider than the Circle.
5. **Warmth over metrics** — "encouragements", quiet counts, no leaderboards on pain.
6. **Safety one tap away** — report/block everywhere; crisis resources ≤2 taps.
7. **The ritual gets space** — check-in and posting are unhurried, full-screen moments.
8. **Both themes are first-class** — light = morning lake, dark = night lake; dark is not an afterthought (many users open this app at 1am).

## 9. Personas & naming

| Context | Persona | Handle |
|---|---|---|
| Primary member (Seeking) | Chidera, 23, final-year UNILAG student | **QuietRiver** |
| Supporter | Emeka, 29, designer, healed from burnout | **SteadyOak** |
| Verified Guide | Amara, 31, navigated grief | **StillWaters** (sage Guide ring) |
| Moderator (back office) | Folake Adeyemi, community ops | real name, back office only |

Display names: two gentle words, PascalCase. Avatars: circular abstract patterns in the cool palette — never photos, never real initials.

ID formats: user `MB-U-NNNNNN` · community `MB-C-NNNN` · circle `MB-C-NNNN-CIR-NN` · post `MB-P-NNNNNNNN` · report `RPT-YYMMDD-NNN`.
