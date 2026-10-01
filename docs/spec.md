# Swell — spec

Snapshot of the living spec as of Oct 1, 2026. The editable version lives in Claude Docs; this file is a copy for the repository.

## Overview

Swell is a phone-only breathwork app: your jellyfish pulses with your breath, and each session you rise from the ocean floor to the surface by syncing with the jellyfish you meet.

Placeholder name: **Swell** (repository: `swell`), for the breath's swell and the ocean's.

- **Platform:** phone only, breath read through the microphone.
- **Separate product:** distinct from the wearable creature game. Rules don't carry over between the two, and not every feature of the other app is needed here.
- **Not included:** no gem.

## Session structure

Every session is one ascent on a fixed path, built from a published breathwork routine.

1. You start on the ocean floor.
2. You swim upward, meeting jellyfish one encounter at a time.
3. Each encounter ends when the jellyfish swims off to the side and a new one arrives.
4. This repeats until the session timer runs out and you reach the surface.

- **Start state:** the session opens on the ocean floor with your jellyfish completely hidden in a seaweed field. The first exhale lifts it out of the seaweed and it begins rising above the seafloor.
- **End state:** the surface is reached at a set height, not a set time. The jellyfish leaps out of the water at whatever velocity it carries, gravity brings it back, and it settles into idly floating on the surface. The sky above is one of a random set (golden hour, blue sky, aurora, starry night, full moon, orange sunrise, purple sunset); the prototype has blue sky only.
- **Fixed timing:** sync never changes how long the ascent takes.
- **Energy and length:** higher-energy sessions have shorter durations. They feel faster without any programmed link between sync and speed.

## Encounters

Each jellyfish you meet has one fixed breathing rhythm, and syncing with it is the whole goal of an encounter.

- **One rhythm each:** a jellyfish never changes its rhythm partway through an encounter.
- **Groups:** some levels have several jellyfish at once. They all pulse in sync on the same rhythm, but each has its own tuned binaural beat.
- **Order:** the sequence of jellyfish follows the routine the session is built on.
- **Guide jellyfish (prototype):** swims beside yours, driven only by the guide rhythm. Its bell pushes on each "Breathe out", its form follows the guide's rhythm, its color shows its beat, and it swims with the same impulse physics. If it out-swims you it pulls ahead up the screen; if you out-swim it, it drops back. Your color converges on its color as you sync.

## Visual language

A jellyfish's shape shows its pulse speed, and its color shows its beat value; because faster pulses use higher beats, the two always agree.

| Trait | Driven by | Reads as |
| --- | --- | --- |
| Shape | Pulse speed | Spikier and sharper at high energy, rounder and smoother at low energy |
| Color | Binaural beat value | Hue moves with the beat |
| Group color | Related beats in a tuned chord | Neighboring shades of one color family |

- **Parametric shape:** body shape is driven continuously by pulse speed rather than by fixed stages (five reference stages, big spike to shiny, are in `design/BodyStages.dc.html`).
- **Swimming path:** jellyfish rise along a vertical sine wave. The faster the pulse, the wider the side-to-side movement.
- **Swim cycle:** the tentacles do the pushing. On the inhale the bell flares and the tentacle roots open with the rim. On the exhale the bell contracts and the push travels down the tentacles. Motion follows overlap and follow-through: the tips lag the bell, never splay without a force acting on them, and keep moving after the bell stops before settling in the glide. Simple and iconic: no central oral arms.
- **Tentacles never overlap:** they keep their left-to-right order with a small gap at every point along their length.
- **Smooth by default:** tentacles are smooth curves at the default rhythm; jaggedness only appears at high energy.
- **Speed lines:** drifting particles stretch along the y-axis with swimming speed, peaking at top speed and settling fully back to dots. Subtle at low energy, stronger as intensity increases.
- **Fish layers:** sporadic fish in three background and two foreground depth layers. Fish swim horizontally only, enter at the top of the screen, and are fully opaque. Depth sets size, speed and drift with the ascent (parametric perspective) and darkness (atmospheric perspective: far fish fade into the water, near fish are dark silhouettes). Background and foreground can be toggled separately.

## Audio

A volume swell carries the breathing pattern you sync to; binaural beats add reinforcement and texture on top. Headphones are required for binaural beats to work.

- **Binaural beats:** standard Starsounds setup, carrier in the left ear and carrier plus beat in the right. Higher-energy rhythms use beats in higher ranges.
- **Chords:** Starsounds' consonant rule. Tones sit on just-intonation intervals of a root, and each tone's beat scales with its carrier (beat = root beat × carrier / root carrier), so both ears hear the same chord in tune.
- **Particles:** carry a low-volume binaural beat (the root) that breathes: it swells on the inhale, ebbs on the exhale and nearly vanishes in the glide; its pitch lifts slightly as the breath fills and settles as it empties, and an octave overtone opens at the top of the breath.
- **Fish:** each fish plays a tuned binaural chord tone rooted on the particle bed, panned with it across the screen. Its volume follows its vertical position: full near the screen's center, softer toward the top and bottom edges, fading to zero off-screen.
- **Breath noise:** a brown or pink noise undercurrent follows the same breath envelope: warm and dark on the inhale, brighter on the exhale, silent in the glide. Deep and bass-heavy, kept well below the tones.
- **Turn of the breath:** the sound crests audibly at the top of the inhale, then eases down into a brief soft dip (about half a second, never full silence) before the exhale rises back out of it. No chime or other cliché marker.

## Sync and transformation

As your breath syncs with an encountered jellyfish, your jellyfish becomes more like it, in motion, shape and color.

- **Motion:** your pulse speed, tentacle undulation and swimming speed match the other jellyfish.
- **Shape:** your form shifts toward its form.
- **Color:** your color shifts toward its color.
- **Feedback:** the transformation is the main feedback.
- **Rhythm, not exhale length:** speed and form are set by your breathing rhythm, never by how long a single exhale lasts.
- **Gradual build:** there is no jump from standstill to full speed; speed and form build as you reach a sync point.
- **Your jellyfish reflects you:** its speed and form follow your real breathing rhythm, not the guide. Breathing too fast makes it fast and spiky.
- **Sync is separate:** sync with the guide is tracked on its own and shown through different cues (bioluminescence, color variety, the guidance fading back). When your rhythm matches the guide, your form matches the guide's naturally.
- **Impulse and momentum:** each breath delivers an impulse; water drag bleeds speed away. Quick breaths stack before drag takes the speed, so speed builds over a few breaths; slow breaths settle between pushes.
- **Bell shows power:** one push per breath. With no breath the bell rests. A breath never restarts the bell; it hurries it into its next power stroke, which releases that breath's push. At higher speed each pulse runs faster and contracts deeper.
- **Realistic range:** speed and form max out around 10 breaths per minute. The form is smooth near 4 per minute and fully spiky by 10.

## Flow state

Staying in sync builds a flow state: the ocean lights up with bioluminescence and the UI steps back, and both ease back if you drift out of sync.

- **Bioluminescence:** syncing transforms the background with bioluminescence. It fades out when the jellyfish leave.
- **UI:** the UI helps you get into sync, then fades away so you trust your own instincts. If you start drifting out of sync, it gradually reappears.
- **Builds gradually:** flow is driven only by time spent in sync.
- **Unwinds gradually:** time out of sync slowly undoes the visual changes.
- **Peak:** maximum flow arrives after a reasonable stretch of sync, not at the end of the level.
- **Breathing world:** the background, particles and jellyfish glow are linked to the breathing indicator. As the guide's swell rises, the particles and glow brighten and the water darkens, then all ease back. Always subtly present, stronger with sync.
- **Color opens with sync:** particles and fish are monochrome when unsynced and gain color variation as sync builds.

## Breath detection

The phone's microphone reads your breath, so headphones with a mic close to the mouth give the most reliable signal.

- **Exhales** are loud enough to detect reliably.
- **Holds** are silence, which is also easy to detect.
- **Inhales** are faint, so sync is best judged mainly on exhale timing and hold length.
- **Background noise** interferes; quiet settings work best.
- **Privacy:** audio should be processed on the device and never recorded.
- **Push driven by breath:** the swim push is triggered by detected exhales, not by a timer. The prototype uses a hold-to-exhale button in place of the microphone. The guide rhythm only drives the guidance UI and the guide jellyfish.
- **No-microphone mode:** the session plays out normally, but your jellyfish's sync and speed are linked to the guide instead of being driven by the microphone.

## Proposed but not yet agreed

| Area | Proposal |
| --- | --- |
| Routines | Resonance breathing (~6 breaths/min), cyclic sighing, box breathing, 4-7-8, gentle energizing rounds with a dizziness warning |
| Breath phases | Exhale = bell contracts and thrusts; inhale = bell relaxes open; hold = glide with a still bell |
| Beat ranges | Map energy to brainwave bands: delta ~1–4 Hz, theta ~4–8, alpha ~8–13, beta ~13–30 |
| Flow timing | Count flow time in breaths; full flow after ~6–8 synced breaths |
| Flow decay | Flow unwinds more slowly than it builds |
| UI buffer | UI returns only after a few breaths out of sync, and leaves after a few in sync |
| Afterglow | Some bioluminescence lingers until the next jellyfish arrives |
| Ascent light | The ocean brightens overall as you rise toward the surface |

**Prototype model (being tested):** two separate measures. *Steadiness* tracks your own rhythm from the gaps between breaths and shapes your form. *Sync* scores each breath on timing against the guide's cue and gap against the guide's cycle, moving 30% toward that score per breath; it drives the glow, color variety, the sync bar and the guidance fading back. Speed comes from impulse physics.

## Open questions

- [ ] Which published routines make the first set of sessions?
- [ ] How many encounters per session, and how long is each?
- [ ] Does a jellyfish leave on a fixed timer whether or not you sync?
- [ ] Is there anything after a session, such as a record of the jellyfish you met?
- [ ] What is your jellyfish's starting form and color at the beginning of each session?
- [ ] How are jellyfish in a group told apart, beyond small color differences?
- [ ] Calibration: how the microphone decides an exhale has started and ended (threshold, noise floor, per-user setup).
- [ ] User feedback: how sync with the guide is shown, beyond the jellyfish's own transformation.
