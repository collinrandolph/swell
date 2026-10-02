# Swell

A phone-only breathwork app (placeholder name). Your jellyfish pulses with your breath, and each session you rise from the ocean floor to the surface by syncing with the jellyfish you meet.

## Live page

`index.html` is the public page: just the app, with Sound, Microphone and Restart. It's a single self-contained file, so any static host works. To serve it with GitHub Pages, go to the repository's Settings → Pages, choose "Deploy from a branch", then pick `main` and `/ (root)`. It appears at `https://collinrandolph.github.io/swell/`. Pages serves over https, which browsers require before they'll allow microphone access.

## Prototype

Open `prototype.html` in a browser. It's the same app plus the test controls: guide rhythms, fish layers, distance and sync readouts. No build step and no dependencies.

- **Hold to exhale** stands in for the microphone: press when you start breathing out, release when you stop. Space or Enter works when the button is focused.
- **Guide rhythm** sets the guide jellyfish, the on-screen cue and the breathing world. It does not move your jellyfish.
- **Your jellyfish** follows your own rhythm: impulse physics for speed, steadiness for form.
- **Sync** with the guide drives the glow, color variety and guidance fading.
- **Sound (headphones)** turns on the tuned binaural bed, fish tones and breath noise. Browsers only allow audio after a tap.

## Breath lab

`breath-lab.html` is a test bench for breath identification: your jellyfish and the microphone pipeline, with no environment, guides or sound. It shows the level against the threshold, each detected sound against the cue on screen, a table of recent sounds (level, brightness, cue, live and final label), and the sounds plotted by their features. Like the live page, the microphone needs https.

## Repository

| Path | What it is |
| --- | --- |
| `index.html` | Live page (just the app) |
| `prototype.html` | Prototype with test controls |
| `breath-lab.html` | Breath identification test bench |
| `design/BreathLab.dc.html` | Design-canvas source of the breath lab |
| `docs/tentacle-motion.md` | Tentacle movement principles |
| `docs/spec.md` | Snapshot of the product spec |
| `design/Swim.dc.html` | Design-canvas source of the prototype |
| `design/BodyStages.dc.html` | The five reference body stages |
