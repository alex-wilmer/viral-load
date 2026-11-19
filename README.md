# Viral Load

An Asteroids-style microbiology game made for Wendy. You are a macrophage on a microscope slide, firing antibodies at viruses (and a few bacteria), each one with a mechanic drawn from how the real thing behaves.

The whole game is one file, `index.html`: plain canvas and Web Audio, no build step. Open it in a browser to play, or deploy the folder as a static site.

## Controls

- Keyboard: arrows rotate and crawl, Space fires, X perforin lance, B bleach bomb, H jump, C cytokine storm (Viral Overload), P pause, M sound.
- PS5 / standard gamepad: stick or d-pad rotate, R2 crawl, ✕ / R1 fire, □ lance, L2 bleach bomb, ○ jump, △ storm, Options pause.

## Deploy

Netlify serves the repo root as-is (`netlify.toml` sets `publish = "."`); there is nothing to build.

## How the code is organised

Everything lives in `index.html`: styles, markup, then one script.

- **Tuning constants** sit near the top of the script, one object per thing (`POX`, `RHABDO`, `BLEACH`, `MEMBRANE`, `DIFFICULTIES`, `WEAPONS`, `BOSSES`…). Change numbers there, not inside functions.
- **Every enemy is a plain object** in `game.virions` with a `kind`. Makers (`makePox`, `makeHIV`…) build them; `freshRun()` is the single source for per-run state.
- **Per-kind behaviour is registered once**, in the registry block at the end of the script:
  - `STEPS[kind]` runs each frame,
  - `DEATHS[kind]` describes the death burst, sound, pickups and any follow-up (`then`),
  - `DRAWERS[kind]` draws it.

### Adding a virus

1. Add its constants object and a `make…` function.
2. Add it to `NEW_WAVE` with the passage it first appears on (and a hint in `passageHint`).
3. Register its step, death and drawer in the registry block.
4. Add a Pathodex entry to `DEX`.
