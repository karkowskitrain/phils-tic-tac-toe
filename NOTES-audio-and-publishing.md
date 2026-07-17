# Monkey Solitaire — Audio & Publishing Notes

Planning notes for two next steps: adding better audio, and publishing the
game as a real app. Nothing here is built yet — these are the options and
recommendations to decide from.

---

## 1. Audio — where to get it

Three realistic sources. Not mutually exclusive — the best result is a **mix**.

### Option A — Free download (royalty-free libraries)
- Best sources: **Pixabay Audio**, **Mixkit**, **Freesound.org** (filter to CC0),
  **OpenGameArt**, **Kenney.nl** (game SFX packs, all CC0).
- Pro: fast, huge selection, zero cost.
- ⚠️ Catch (matters because we may sell this): licenses vary. Need
  **CC0 / public domain** or a license that explicitly allows **commercial use
  and redistribution inside an app**. Avoid "non-commercial" or
  "attribution-only" unless willing to add credits. Freesound is mixed — check
  each clip.

### Option B — Make your own
- Ambience/music: **GarageBand** (free, iPhone/Mac), **BandLab**,
  **Audacity** (free desktop editor/looper).
- Animal one-shots: record real sounds or foley them, edit in Audacity.
- Pro: 100% original and copyright-clean — fits the project's "all original"
  ethos and removes all licensing risk when selling.
- Con: more time; polished jungle *music* is hard to make from scratch.

### Option C — AI-generated (middle ground)
- **ElevenLabs SFX** (text-to-sound: "monkey screech", "single bird caw",
  "light rain on leaves") — great for individual animal one-shots.
- **Suno / Udio** for looping jungle/night music beds.
- ⚠️ Check commercial-use terms on the plan used — paid tiers usually grant
  commercial rights, free tiers often don't. Read before selling.

### ✅ Recommendation
Hybrid — **CC0 ambience loops** (day / night / rain beds from Pixabay or Kenney)
+ **AI or self-recorded one-shots** for each animal. Fastest path to something
that sounds great and is safe to sell.

### Technical realities to design around
- **Format:** iOS Safari plays **MP3 / AAC (.m4a)**, *not* .ogg.
- **Loops:** short seamless files (~20–40s), **crossfade** on the
  day → night → rain transitions, hooked into the existing `checkPhase()` logic.
- **iOS quirk:** audio can't play until a user tap (audio-unlock already
  exists), and the **hardware mute switch silences web audio** — a native app
  wrapper bypasses this.
- **File size:** game is currently one self-contained `index.html`. Real audio
  means either base64-embedding (bloats file ~33%) or shipping separate asset
  files. Separate files preferred once we go the app route.

---

## 2. Publishing as an app

A ladder from "free and instant" to "real App Store listing." Goal is
**learning the process for future games**, which shapes the advice.

| Path | What it is | Cost | Learning value |
|---|---|---|---|
| **PWA** ("Add to Home Screen") | Add a manifest + icons; installs from Safari like an app | Free | Low — no store process |
| **Capacitor → App Store** | Wrap the HTML in a native shell, submit to Apple | **$99/yr** + a Mac | **High — the real pipeline** |
| **Capacitor → Google Play** | Same wrapper, Android | **$25 once** | High, cheaper |

- **Capacitor** (by Ionic) is the modern, recommended wrapper — drops
  `index.html` into a native project you open in Xcode / Android Studio. Also
  fixes the mute-switch audio problem.
- Apple requires the **Apple Developer Program ($99/year)**, a **Mac with
  Xcode**, screenshots, an icon, a privacy label, and passing review.

### ✅ Recommendation
Two steps. First make it a **PWA** (free, ~30 min) to install on the iPhone and
test audio. Then, for the real learning experience, wrap with **Capacitor and
submit to the App Store**. If $99/yr feels steep just to learn, do
**Google Play first at $25** — same skills, cheaper gate.

---

## 3. Purchase vs. another method

| Model | Fit for this game |
|---|---|
| **Paid upfront** ($0.99–$2.99) | Clean, no clutter, fewest downloads. Great for a learning launch. |
| **Free + ads** (AdMob) | Most downloads, but ads wreck a *relaxing* solitaire vibe and add SDK complexity. |
| **Free + optional IAP** | Sell extra scenes / card backs / seasons; keep base game free. Best long-term fit. |
| **Just free** | Perfect portfolio piece. |

### ✅ Recommendation
Since the goal is learning, launch **free or as a $0.99 paid app** — walk through
Apple's full pricing/tax/submission flow without an ads SDK. Later, **IAP**
(unlock more scenes) is the natural fit for a scene-rich game. **Avoid ads** —
they'd clash with the calm mood.

---

## Legal note before selling
- Keep all art **and audio** original or CC0 (same reason we kept the art
  original). Solitaire mechanics themselves are not copyrightable.
- Make sure the store listing and name don't reference "Burning Monkey
  Solitaire." "Monkey Solitaire" on its own is fine.

---

## Next actions (when ready)
- [ ] Choose audio source(s) and gather day / night / rain loops + per-animal one-shots
- [ ] Wire up the audio system: day/night/rain crossfades + per-animal one-shots hooked into the existing schedulers
- [ ] Add a PWA manifest + app icons; test install on iPhone
- [ ] Set up Capacitor; open in Xcode / Android Studio
- [ ] Decide pricing model and prepare store listing (screenshots, icon, privacy label)
