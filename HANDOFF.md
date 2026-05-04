# AMP Signal — Project Handoff

**Last updated:** May 2, 2026
**Repo:** `scottehrlich-lang/amp-signal` (public)
**Live URLs:**
- POC: https://scottehrlich-lang.github.io/amp-signal/
- Executive pitch deck: https://scottehrlich-lang.github.io/amp-signal/pitch/
- Inside the Signal (adoption campaign hub): https://scottehrlich-lang.github.io/amp-signal/inside/

This document is the single source of truth for picking this project up. It covers what AMP Signal is, what's been built, what's broken, what's missing, and the exact next steps to ship.

---

## 1 · What AMP Signal Is

AMP Signal is an AI-native sales intelligence platform for Sinclair's regional broadcast sales force (~800 sellers).

**Vision:** Make every Sinclair seller — regardless of experience, market size, or role — operate with the intelligence, focus, and strategic clarity of a 20-year media veteran with a team of analysts working for them around the clock.

**Five design principles:**
1. **Bespoke over broadcast** — every view custom to the user's role, market, and accounts
2. **Push over pull** — intelligence comes to the user, not the other way around
3. **Agents do the work** — specialized AI agents per domain, users see output not machinery
4. **Clarity at every level** — every view answers: where do I stand / what needs me now / what's my move
5. **(Principle 5)** — not extracted; check the original PRD source

**Six core modules:**
1. The Critical Few (Sinclair's strategic priorities, surfaced live)
2. Opportunity Intelligence (new business, lapsed-account reactivation, scatter alerts, political-window timing)
3. Client Intelligence (pre-meeting briefs, account history, contact and trigger events)
4. Pacing & Sell-Through (real-time pacing, leading indicators, every daypart and product)
5. Action Queue (daily ranked list by revenue + urgency, talking points + rescue plays)
6. Competitive Intelligence (category momentum, competitor spend, displacement opportunities)

**Seven-agent architecture:** Pacing · Client Intelligence · Opportunity · Coaching · Competitive · Critical Few · Synthesis

**Five user personas:** AE → Sales Manager → Regional Manager/VP → EVP/Division Lead → CRO/C-Suite

The full PRD is not in this repo — it lives in an earlier conversation with Claude, exported as a docx. Recommend recovering it before next major work.

---

## 2 · Two Deliverables

### A · The executive sell-in pitch deck (`/pitch/`)

A single-page scrollytelling pitch site designed for live executive presentation (primary) and async forwarding (secondary). Pitches a funded pilot: one Sinclair regional sales group, 25–40 AEs under one Regional Sales Manager, 12 weeks, ~30% net composite lift modeled.

**10 sections:**
1. Open — pitchman + "See the signal first"
2. Noise — the 14-tabs problem
3. Platform — One platform, three lenses (AE / RSM / Executive)
3b. What it is — vision, principles, modules, agent architecture, POC proof
4. Renewal vignette — cross-property upsell + pacing
5. Call vignette — pre-meeting brief
6. Cycle vignette — political-window planner
7. Math — +30% composite (10% increased sales / 10% loss mitigation / 10% cost efficiency)
8. Pilot — the ask: 1 region, 12 weeks, embedded pod
9. Signoff — pitchman + "See it first. Win it first."

### B · Inside the Signal — internal adoption campaign (`/inside/`)

A 12-week internal marketing campaign architected to drive AMP Signal adoption across the pilot region (and templated to scale to other regions post-pilot). Goal: neutralize the historic Sinclair "great idea but no one will use it" objection by walking into the executive pitch with adoption already in motion.

**Cast (5 recurring characters):**
1. **The Pitchman** — Scott (host)
2. **Maya** — believer AE, Latina mid-30s
3. **Marcus** — skeptic AE, mid-40s, burned by past rollouts
4. **Diane** — Regional Sales Manager, mid-50s, battle-tested
5. **The Dashboard** — the AMP Signal UI itself, recurring on-screen presence

**26 drops across 12 weeks:**
- 5 hero pieces (H1 Launch Film, H2 Win Story ×3-4, H3 Manager Moment ×2, H4 The Reckoning, H5 The Recap)
- 7 reusable drop formats (Tab Count, Marcus Says/Does, AE Diary, Before/After, Leaderboard, Sources Say, Reaction Frame)
- ~60% static / ~40% motion mix for distribution flexibility (Teams, email, intranet, all-hands, vertical social)

---

## 3 · Production Stack

| Layer | Tool | Notes |
|---|---|---|
| Hosting | GitHub Pages | Auto-deploys from `main`. Only reliable deploy path from Claude container; Netlify/Vercel APIs blocked |
| Source control | `scottehrlich-lang/amp-signal` (public) | Fine-grained PAT scoped to Contents read/write |
| Character/visual gen | Higgsfield Nano Banana 2 | Caricature-style illustration; full-body painterly |
| Vignette video | Higgsfield Seedance 2.0 std-mode | 6s loops; std-mode > fast (less stiff) |
| Voice / narration | Birdie pipeline → ElevenLabs | Manifest-driven via `narration.json` |
| Compositional design | Canva | Recommended for cast composite; Higgsfield can't preserve identity in multi-character generations |
| POC frontend | Single-file HTML/CSS/JS at `/index.html` | v6 build, GitHub Pages |

---

## 4 · Brand Rules (locked, applied across all surfaces)

- **Background:** white `#ffffff`
- **Primary action / typography:** AMP navy `#0a1634`
- **Performance indicators only (never decorative):** green `#00a86b` good · amber `#e07b00` warn · red `#e03450` risk
- **Typography:** Lato 400/900 throughout · Space Mono for terminal/source/caption accents
- **Audio rendering convention:** in narration `text` fields, write "Amp Signal" mixed-case (lowercase forces single-word read; ElevenLabs reads "AMP" as letter-by-letter A-M-P). Visible text on screen still says "AMP Signal."

---

## 5 · Sinclair Cultural Integration Rules

- **Rob Weisbord (COO/sales)** — fair to use his catchphrases sparingly: *"skate to where the puck is going,"* *"keep it on your frontal lobes,"* *"let's get the cash"*
- **Ryan Moore (CRO)** — reference as tone register (no-nonsense, get-to-the-point), never by name in copy
- **Chris Ripley (CEO)** — GATED: never include without Scott's explicit per-use approval
- **Sinclair brand identity** — Baltimore-based, prides itself on efficiency. Fair to lean into in copy.
- **"Keep it on your frontal lobes"** — used exactly once in the campaign, scheduled for D6 Sources Say Week 4

---

## 6 · Repository Structure

```
amp-signal/
├── index.html                          # AMP Signal v6 POC (the actual product)
├── pitch/
│   └── index.html                      # Executive sell-in pitch deck
├── inside/
│   ├── index.html                      # Inside the Signal campaign hub
│   └── scripts/
│       └── h1-launch-film.md           # H1 Launch Film screenplay (script only, not produced)
├── campaign/
│   └── index.html                      # WORKFLOW POC ONLY — not the real campaign. Reference artifact.
├── marketing-assets/
│   ├── pitchman.jpg                    # Scott caricature (canonical character file)
│   ├── audio/
│   │   ├── narration.json              # Birdie source manifest (voice_id, settings, sections)
│   │   ├── README.md                   # Audio integration notes
│   │   ├── 01-open.mp3 ... 09-signoff.mp3  # Pitch deck section narrations
│   │   └── teaser-01.mp3               # Inside the Signal pre-pilot teaser
│   ├── video/
│   │   ├── 04-renewal.mp4              # Maya — walking into the renewal
│   │   ├── 05-call.mp4                 # Maya — finding the brief
│   │   └── 06-cycle.mp4                # Maya — studying the markets
│   └── screenshots/
│       ├── 01-cro-overview.png         # POC CRO overview ($151.2M / 94% pacing)
│       ├── 02-ae-action-queue.png      # POC AE action queue (5 ranked priorities)
│       └── 03-regional-critical-few.png # POC regional drill-down
└── README.md
```

---

## 7 · What's Working

- **Pitch deck (`/pitch/`)** — full 10-section scroll site, navigation rail, section counter, audio engine with progress hairline + end-of-audio "Continue" cue + auto-advance toggle, keyboard nav (arrow keys / spacebar / pageup-pagedown)
- **Inside hub (`/inside/`)** — campaign hub with hero, cast, calendar, drop library, stats, footer; teaser narration plays on demand
- **Audio v3 narration** — all 10 sections including teaser, natural cadence settings (stability 0.40 / style 0.50), "Amp Signal" reads correctly
- **Three vignette videos** — Maya in renewal/call/cycle moments, Seedance 2.0 std-mode 6s loops with Ken Burns CSS zoom layered on
- **POC screenshots** — captured via Playwright at 1440×900 @ 2x DPR
- **Birdie pipeline** — manifest-driven, self-deploying. Birdie pulls `narration.json`, generates MP3s via ElevenLabs, commits and pushes back to repo. No human intermediary needed.

---

## 8 · What's Broken / Missing — Critical Issues

### 🔴 Visual identity inconsistency (BIGGEST PROBLEM)

**The problem:** The pitchman caricature (`marketing-assets/pitchman.jpg`) is in a *painterly digital illustration* style — heavy shading and texture, big-head/small-body proportions, full body, light grey gradient background, casual hoodie/jeans/sunglasses styling.

The Maya/Marcus/Diane characters that were generated and used in the live videos are in a *flat editorial caricature* style — different proportions, head-only/chest-up framing, white background, professional attire. They do not visually match the pitchman.

This was discovered late on May 2 after Scott repeatedly pointed it out. Three new candidates were generated in the *correct* painterly style but were never pushed to the repo because of CloudFront network restrictions in the Claude container.

**The new (correct-style) characters exist as Higgsfield job IDs only:**
- Maya v2 (locked, "Maya C"): job `61fc3e6c-15ec-417c-8d8a-401f0ca704bf`
- Marcus v2: job `c8fb00c1-eedc-402c-83cb-817a1c859adb`
- Diane v2: job `181f9b5a-b397-43fc-a0db-fa21027f97cf`

**Scott will need to download these from Higgsfield and either:**
- Drop them in chat with the next Claude/agent and have them pushed to `marketing-assets/character/` in the repo, OR
- Push them to the repo directly via the GitHub web UI

**Once the new characters are in the repo, the cascade fix is:**
1. Update `/inside/index.html` cast section image references (`maya-base.jpg` etc.) — files exist as fallbacks but don't match
2. Regenerate the three vignette videos with new Maya as start-frame reference (Higgsfield Seedance 2.0, std-mode, 6s, prompts already proven)
3. Replace the three videos in `/marketing-assets/video/` and the pitch deck picks them up automatically

### 🔴 Cast composite frame — never built

The H1 Launch Film script's signoff calls for a single 16:9 frame with all four characters together. This was never produced because:
- Nano Banana 2 multi-character generation averages facial features (tested with all 4 reference images at once; Scott still came out generic)
- Programmatic composite was blocked because Claude couldn't fetch Higgsfield CloudFront images directly

**Recommended path:** Once the new characters are in the repo (above), do a manual composite in Canva. Brief at `/mnt/user-data/outputs/cast-composite-canva-brief.md` (or wherever it ended up — may need to be reconstructed). Layout: Maya / Scott / Marcus (back-half) / Diane on white 1920×1080, background-removed character cutouts.

### 🟡 H1 Launch Film not produced

Script complete at `inside/scripts/h1-launch-film.md`. Production blocked on:
- Cast composite (above)
- Voice casting for Maya/Marcus/Diane lines (script calls for separate ElevenLabs library voices)
- Final assembly (audio over visuals — could be done in Canva, After Effects, or a video editor)

### 🟡 Section 03b audio not yet regenerated for v2.2 copy

The pitch deck section 03b was rebuilt from a screenshot dump into a PRD-anchored "what it is" section on May 2. The narration text in `narration.json` was updated to match, but the corresponding MP3 was not regenerated. **Birdie needs to run again** to regenerate `03b-whatlooks.mp3`. Currently the section will play the older narration that describes screenshots that no longer exist as the focal point.

### 🟡 26-drop campaign content production

The campaign architecture is designed but only the pre-pilot teaser was produced. The remaining 25 drops exist as named slots in the calendar with no produced content. This was always a post-greenlight effort but the format-proof drops (one Tab Count, one AE Diary, one static asset) were planned for the executive sell-in and never built.

---

## 9 · Pickup Sequence (Recommended)

If picking this up to ship the executive pitch:

**Priority 1 — Fix the visual identity (~1 day)**
1. Pull new Maya/Marcus/Diane portraits from Higgsfield jobs above
2. Push to `marketing-assets/character/`
3. Update Inside hub cast section image references
4. Regenerate three vignette videos with new Maya
5. Replace videos in repo

**Priority 2 — Lock the executive pitch (~half day)**
1. Run Birdie against current `narration.json` to regenerate 03b audio
2. Walk through `/pitch/` end-to-end with audio, react, polish
3. Test forwarded link experience (mobile, async, audio off)

**Priority 3 — Prove the campaign exists (~1-2 days)**
1. Cast composite in Canva
2. Produce H1 Launch Film (cast composite + audio narration over it; can be slideshow-style for v1)
3. Produce one Tab Count drop, one AE Diary drop, one static Leaderboard drop — format proofs
4. Update `/inside/` to show real produced content in week 1 slot

**Priority 4 — Templating for post-greenlight scale**
1. JSON manifest per drop format (script + generation prompt + layout)
2. Calendar automation so weeks 2-12 are content-fill not from-scratch

---

## 10 · Birdie Audio Pipeline (Working)

Birdie is Scott's automation for generating narration via ElevenLabs.

**Manifest:** `marketing-assets/audio/narration.json`
**Voice ID (Scott trained voice):** `EV4R1ZIcLtNYU4JyFxOe`
**Model:** `eleven_turbo_v2_5`
**Settings:** stability 0.40 / style 0.50 / similarity_boost 0.85 / speaker_boost true (these are tuned for natural cadence; don't lower without testing)

**Workflow:**
1. Edit per-section `text` in manifest (preserve em-dashes, ellipses, "Amp Signal" mixed-case)
2. Birdie pulls manifest from GitHub raw
3. Birdie POSTs each section to `https://api.elevenlabs.io/v1/text-to-speech/{voice_id}/stream`
4. Birdie writes `{section.id}.mp3` to `marketing-assets/audio/`
5. Birdie commits + pushes to main
6. GitHub Pages auto-deploys; site picks up new audio in ~60s

Has been validated end-to-end multiple times. Self-deploying, no Claude required in the loop.

---

## 11 · Known Constraints

- **GitHub Pages deploys from `main`** — no PR review gate; commits go live in ~60s
- **Sinclair political franchise content** trips Bytedance content filters in Seedance/Kling; neutralize prompt language ("regional zones," "market planning") to avoid "sensitive content" rejections
- **Kling 3.0** letterboxes on aspect-ratio mismatch (4:5 source → 9:16 output produces bars + filler). Prefer Seedance 2.0 or Cinema Studio 3.0 for portrait content
- **Higgsfield doesn't preserve identity in multi-character generations** — averages faces across reference images. Composite work belongs in Canva, not Nano Banana 2
- **Claude container CANNOT fetch Higgsfield CloudFront URLs directly** — neither via bash curl (host not in allowlist) nor web_fetch (URLs not user-provided per provenance rules). Image pull-down requires manual upload to chat or repo

---

## 12 · Tokens & Credentials

⚠️ The repo has been operated with these credentials. Rotate if handing off to a new operator.

- **GitHub fine-grained token** (scoped: Contents read/write on `scottehrlich-lang` repos): see Scott's secure storage
- **Netlify personal access token** (Birdie1 team account): unused on this project; was attempted then abandoned in favor of GitHub Pages
- **ElevenLabs API key**: not in repo; lives with Scott / Birdie

---

## 13 · Honest Status

This handoff is being written because the May 2 working session did not deliver a completable executive pitch. The fundamentals are solid: the pitch deck structure, the audio pipeline, the campaign architecture, and the POC itself all work. The visual identity is the tallest unresolved blocker — the cast doesn't share a style, and the cast composite was never produced.

A capable operator (human or AI) with this document plus the repo can probably ship the executive pitch in 1-2 working days. The Inside the Signal campaign is a longer effort; ~1 week to produce the launch-week kit, multi-week templated production for the rest.

If picking up with a new AI agent: **read the actual `pitchman.jpg` file before generating any new visual content.** That single step would have prevented most of today's wasted work.
