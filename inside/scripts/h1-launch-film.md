# H1 — The Launch Film
**Inside the Signal · Episode One**
**Runtime: ~2:30 · Aspect: 9:16 (vertical primary) + 16:9 (all-hands cut)**
**Audio: Pitchman (Scott voice via ElevenLabs/Birdie) + character voices**
**Static derivative: Pull-frame poster + email banner crops**

---

## Scene 1 · Open · 0:00–0:18 *(pitchman, navy background)*

VISUAL: Pitchman caricature, full frame. Static. Navy backdrop with a single hairline of green at the bottom (the Signal pulse from /inside/).

PITCHMAN (V.O.):
> "Rob says skate to where the puck is going.
> The puck is the next deal.
> The puck is the renewal you didn't know was at risk.
> The puck is the buyer who's already in motion.
> AMP Signal puts the puck on the dashboard."

CUT TO: Title card. White on navy. *"INSIDE THE SIGNAL."* Hold 1.5s.

---

## Scene 2 · The Cast · 0:18–1:00 *(character introductions)*

Each character gets ~10 seconds. Static portrait + name card + one line in their voice. Cinematic Ken Burns drift across each portrait.

**MAYA** *(card: "MAYA — Account Executive · Pilot Region")*

MAYA (V.O.):
> "I had fourteen tabs open last quarter.
> This quarter I have two.
> I'm not back in my email at midnight anymore."

**MARCUS** *(card: "MARCUS — Account Executive · Pilot Region")*

MARCUS (V.O., Ryan-cadence — clipped, dry):
> "Six tools in five years.
> None of them got out of beta.
> Get to the point — what's different this time?"

**DIANE** *(card: "DIANE — Regional Sales Manager · Pilot Region")*

DIANE (V.O., battle-tested, even):
> "I don't care about the dashboard.
> I care if it gets us cash.
> Show me the cash."

---

## Scene 3 · The Answer · 1:00–1:45 *(pitchman + b-roll)*

PITCHMAN (V.O., over Maya/Marcus/Diane vignette video clips intercut with UI moments from the platform):

> "Sinclair runs lean.
> So why is your top AE running fourteen tabs?
>
> One platform.
> Every role.
> Tuned to each seat.
>
> Account intelligence the AE has before she walks into the room.
> Pacing data the manager has before forecast review.
> Regional posture the executive has before the all-hands.
>
> One source of truth.
> Three lenses.
> Built for how Sinclair already sells —
> just faster, sharper, and on the table when it matters."

VISUAL pace: 3-second cuts between vignette beats and UI screens. Quick-but-not-frantic.

---

## Scene 4 · The Pilot · 1:45–2:10 *(stat card style)*

VISUAL: Black-on-white card layout. Three stats appear in sequence, each with a Ken Burns push-in.

**Card 1:** *"One region."*
**Card 2:** *"Twelve weeks."*
**Card 3:** *"Twenty-five to forty AEs. Real pipeline. Real cash."*

PITCHMAN (V.O., spare):
> "One region.
> Twelve weeks.
> Real pipeline.
> Let's get the cash."

*(The "Let's get the cash" lands as the third Rob-callback — establishing that this campaign earns its Sinclair-insider energy.)*

---

## Scene 5 · The Sign-off · 2:10–2:30 *(pitchman + cast composite)*

VISUAL: All four illustrated characters in a single composite frame — pitchman center, Maya/Marcus/Diane flanking. Static. The campaign team revealed.

PITCHMAN (V.O.):
> "This is Inside the Signal.
> Twelve weeks. Twenty-six drops. Real wins, in real time.
>
> Watch this space."

End card: *"INSIDE THE SIGNAL · S1 · NOW LIVE"* + URL.

Final frame holds 2 seconds. End.

---

## Production notes

### Visual generation order
1. **Marcus vignette stills** (×2): pointedly *not* using platform / catching himself reaching for it
2. **Diane vignette stills** (×2): pipeline review at desk / walking the floor with tablet
3. **Maya vignette** (×1 NEW): the "two tabs" moment — clean desk, satisfied ease
4. **Cast composite frame**: all four characters in one frame for sign-off — generated as a single Nano Banana 2 image with all four in shot
5. **Vignette video clips** for the answer-section b-roll: Seedance 2.0 std-mode 6s loops from the new stills

### Audio production
Single MP3 for the whole launch film, generated against a `launch-h1` manifest entry. Birdie pipeline.

Voice casting note: Pitchman is Scott. Maya/Marcus/Diane lines need separate ElevenLabs voices (library voices are fine — these aren't trained voices). Recommended:
- Maya: warm mid-range female, conversational
- Marcus: dry mid-range male, slightly older, no-bullshit cadence
- Diane: lower-register female, measured, command presence

### Static derivatives (auto-generated from key frames)
- **Email banner** (1200×400): pitchman + headline + URL
- **Teams banner** (1200×600): cast composite
- **Intranet hero** (16:9 still): pitchman with title card
- **Print one-pager** (PDF): script as essay-style writeup with character portraits

### Sinclair-cultural lines used
- "Rob says skate to where the puck is going" — opening line *(Rob-callback #1)*
- Marcus's Ryan-cadence — register reference, no name *(Ryan as tone)*
- Diane's "Show me the cash" — recurring tag *(Rob "let's get the cash" channeled through Diane)*
- "Sinclair runs lean" — explicit Baltimore-efficiency call *(Sinclair brand-identity)*
- "Let's get the cash" — closing line *(Rob-callback #2)*

NOT used in launch film (held for later drops):
- "Keep it on your frontal lobes" — held for D6 Sources Say W4
- Chris Ripley — held entirely (gated, requires per-use approval)

---

## What gets generated for the executive sell-in vs. post-greenlight

**Generate now** (proves the campaign is real):
- Cast composite frame (Scene 5 visual)
- Audio narration via Birdie (single MP3)
- One Marcus vignette still (needed for the Marcus moment)
- One Diane vignette still (needed for the Diane moment)
- Reuse existing Maya footage where possible

**Post-greenlight only:**
- Full Seedance video clip generation for b-roll
- Static derivative production (banner, headers, one-pager)
- Voice casting and recording for Maya/Marcus/Diane lines (vs. placeholder)

This keeps generation budget tight for the sell-in while the script + cast composite + pitchman audio is enough to *prove* the launch film exists in spec.
