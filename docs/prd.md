# Mindbook — Product Requirement Document (v1.1, working copy)

> Source: original PRD ([Mindbook-PRD-original.pdf](./Mindbook-PRD-original.pdf), Lagos, Nigeria). This working copy restructures it, locks terminology, and records PM reconciliations where the original was ambiguous. Changes from the original are marked **[PM]**.

## 1. Introduction

Mental well-being remains an overlooked aspect of everyday life for many Nigerians. Financial pressures, academic demands, career uncertainty, family responsibilities, and societal stigma often prevent people from seeking emotional support, even when they need it. Awareness of mental health is growing, but access to affordable, trusted, judgment-free support remains limited.

Existing social platforms are designed for engagement, not emotional support. Professional therapy is inaccessible for many due to cost, availability, or stigma.

**Mindbook is a community-driven emotional wellness platform designed so that no one has to face life's challenges alone.** It combines supportive communities, anonymous sharing, emotional check-ins, guided resources, and access to people who have walked similar roads — a safe digital space to receive encouragement, build resilience, and grow emotionally.

Mindbook **complements, never replaces,** professional mental health care.

## 2. Problem statement

Many Nigerians experience stress, anxiety, loneliness, grief, burnout, and relationship difficulties, yet lack safe, affordable, judgment-free spaces to seek support and connect with people who truly understand. Social platforms aren't built for emotional well-being; professional services are inaccessible or under-utilized due to cost, stigma, and limited availability.

## 3. Proposed solution

A mobile application providing a safe, private, supportive environment for emotional wellness:

- **Daily emotional check-ins** with mood history and personalized recommendations
- **Communities and Circles** built around shared life experiences and emotional journeys
- **Anonymous or identified sharing** with encouragement from peers and verified Guides
- **Curated emotional wellness resources**
- Intelligent recommendations connecting users to relevant communities, resources, and support based on their current emotional state

Unlike engagement-driven social media, Mindbook is intentionally designed for meaningful conversation, emotional safety, and personal growth.

## 4. Target audience

| Tier | Who |
|---|---|
| **Primary (MVP)** | University students · NYSC members · Young professionals · Job seekers · Entrepreneurs · Remote workers |
| **Secondary** | People who have recovered from burnout, healed from heartbreak, managed anxiety, navigated grief, overcome postpartum challenges; people passionate about peer support |
| **Future** | Licensed psychologists · Therapists · Counsellors · Faith-based counsellors · Wellness coaches |

## 5. Objectives

1. Create a safe, private, inclusive digital environment where users openly express emotions without fear of judgment.
2. Connect users with supportive communities based on shared life experiences and journeys — not temporary emotions alone.
3. Reduce isolation through meaningful peer connections and encouragement from verified Guides and community members.
4. Foster healthy, respectful interactions through moderation, reporting tools, and community guidelines.
5. Build a trusted emotional wellness platform that complements, not replaces, professional mental health care.

## 6. Core taxonomy **[PM — locked]**

The original PRD used "Circles" for both the big and small groups. Locked as:

| Term | Definition |
|---|---|
| **Community** | A topic space (Relationships, Anxiety, Faith, Career, …). Users browse and join many. Has a description, feed, announcements, featured resources, and many Circles. |
| **Circle** | A small private pod of **5–10 members** inside a Community, auto-assigned, balanced between members *seeking support* and members *supporting others*. The user's primary support space. May include a **Verified Guide**. |
| **Guide** | A vetted member who has walked a similar road and encourages healthy conversation. Applied-for; verified after training and platform review. |
| **Moderator** | Oversees multiple Circles/Communities; reviews reports, enforces guidelines. |
| **Journey stage** | The user's self-identified stage: **Seeking Support → Healing → Guiding Others**. Lives on the profile, changeable anytime. **[PM]** When joining a specific Circle the user picks a *binary per-Circle role* — Seeking Support / Supporting Others — which is how Circles stay balanced. Journey stage = identity; Circle role = per-room posture. |

## 7. Scope — MVP 1.0

### Mobile app

| Area | Capabilities |
|---|---|
| **Authentication** | Register (email + password), verify email, login/logout, forgot password |
| **Anonymous identity** | Choose display name (e.g. HopefulSoul, BraveHeart, StillHealing) + avatar. Real identity never visible to other members. |
| **Onboarding** | Welcome intro → community guidelines + privacy consent → support topics selection → recommended Communities → per-Circle role choice → auto Circle assignment → first emotional check-in |
| **Daily check-ins** | Daily mood selection, mood history, personalized recommendations based on check-ins |
| **Communities** | Browse, join multiple, leave; public and private; community feed, description, member/Circle counts, featured resources, announcements |
| **Circles** | Auto-assignment (5–10 members, balanced); share experiences, ask questions, encourage, celebrate milestones, guided conversations. Full Circle reached → assign to next available Circle in the same Community. |
| **Posting** | Composer "What's going on with you today?" → choose purpose (**I Need Support · I Need Advice · I Want to Encourage Someone · I Want to Share My Story · Prayer Request**) → write → choose audience (**My Circle · Entire Community · Moderators Only**). Anonymous by default. |
| **Engagement** | Comments, reactions, encourage members, save helpful posts, report content |
| **Home feed** | Personalized greeting, check-in prompt/composer, recent posts from joined Communities & Circles, recommended Communities, wellness resources, community updates |
| **Safety** | Report posts/comments/users, block users, community guidelines, crisis-resource signposting **[PM: added — non-negotiable for this category]** |
| **Notifications** | Daily check-in reminders, replies, community updates |
| **Search** | Search Communities and topics |
| **Profile & settings** | Edit display name/avatar, journey stage switch, joined Communities, assigned Circles, mood history, activity history, privacy settings, change password, logout, delete account |

### Back office (web)

| Area | Capabilities |
|---|---|
| Users | Manage accounts, suspend/reactivate, view profiles & account status |
| Onboarding | Configure onboarding content and community guidelines |
| Check-ins | Anonymous emotional trends + engagement analytics |
| Communities & Circles | Create, edit, archive, manage; capacity/balance oversight |
| Feed | Remove inappropriate posts, pin announcements |
| Guides | Assign, verify, review Guide status |
| Notifications | Announcements + notification campaigns |
| Moderation | Review reports, moderate content, suspend users, manage moderators |
| Search | Manage searchable categories and keywords |
| Settings | Platform settings and moderation policies |

### Support topics (onboarding + search)

Relationships · Men's Issues · Women's Issues · Career · School · Anxiety · Loneliness · Family · Financial Stress · Faith · Healing · Other

### Out of scope (future releases)

AI emotional companion · therapist video consultations · voice/video rooms · live streaming · group calls · marketplace · courses · corporate wellness portal · church/university communities · premium subscriptions · emotional analytics dashboard · AI-powered matching · ML recommendations · wearables · multi-language.

## 8. MVP user flow (happy path)

1. **Download & register** — email + password → verify email → sign in.
2. **Create anonymous identity** — display name + avatar. Email/real identity never shown to members.
3. **Welcome** — "Welcome to Mindbook. Do life alone? Nah. A safe space where you can share, heal, grow, and support others through life's challenges." → Continue.
4. **Guidelines & consent** — accept Community Guidelines, Privacy Policy, T&Cs.
5. **"What would you like support with?"** — multi-select topics.
6. **Recommended Communities** — join one, many, or skip.
7. **"What brings you to this Community today?"** — Seeking Support / Supporting Others (changeable anytime).
8. **Auto Circle assignment** — private 5–10-member Circle, balanced; overflow → next Circle.
9. **Home feed** — greeting, composer, Circle/Community posts, recommendations, resources.
10. **Daily rhythm** — return to check in, share, continue conversations, join more Communities, switch role as needs change.
11. **Growth** — users naturally move Seeking → Healing → Guiding; consistently empathetic members may apply to become **Verified Guides** (training + review).

## 9. PM reconciliations & open items **[PM]**

| # | Item | Resolution |
|---|---|---|
| 1 | Original "Dependencies & Prerequisites" section referenced alumni lists, donations, and class notes — copy-paste from another product. | Replaced (§10). |
| 2 | Circles vs Communities naming collision | Locked in §6. |
| 3 | 3 journey stages vs binary Circle role | Both kept, layered (§6). |
| 4 | Mood scale undefined | **Proposed:** 5-step felt scale — **Heavy · Low · Okay · Good · Light** (body-language words, no clinical labels, no emoji). Design owns the visual system. |
| 5 | Crisis path undefined | Added crisis-resource signposting to MVP safety scope. A support app in this category cannot ship without it. |
| 6 | Guide verification detail | MVP: back-office manual assign/verify. Training-flow product is post-MVP. |
| 7 | "Anonymous and identified posting" (features) vs "every user has an anonymous profile" (user flow) | MVP: **all member-facing identity is the anonymous identity**. "Identified" = display name visible vs fully anonymous ("A Circle member") per post. |

## 10. Dependencies & prerequisites **[PM — rewritten]**

**Technical** — Flutter mobile app (iOS + Android) · Java/Spring Boot backend API · push notifications · email verification service · object storage for avatars/resources.

**Legal & compliance** — NDPA (Nigeria Data Protection Act) + GDPR-aligned consent, encryption at rest/in transit, access logs, opt-outs · Terms of Service, Privacy Policy & Community Guidelines published before registration opens · special care: emotional/mood data is **sensitive personal data** — minimize collection, never expose individual mood data to other members, aggregate-only analytics.

**Trust & safety** — moderation rules + workflows live before launch · crisis-escalation protocol with local resources (e.g., lifeline directory for Nigeria) · Guide vetting standard.

**Feedback** — target-audience testers (students, NYSC, young professionals) in UAT · in-app feedback + surveys post-launch.
