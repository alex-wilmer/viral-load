# Viral Load

An Asteroids-style microbiology game made for Wendy. You are a macrophage on a microscope slide, firing antibodies at viruses (and a few bacteria), each one with a mechanic drawn from how the real thing behaves.

The whole game is one file, `index.html`: plain canvas and Web Audio, no build step. Open it in a browser to play, or deploy the folder as a static site.

## Controls

- Keyboard: arrows rotate and crawl, Space fires, X perforin lance, B bleach bomb, H jump, C cytokine storm (Viral Overload), P pause, M sound.
- PS5 / standard gamepad: stick or d-pad rotate, R2 crawl, ✕ / R1 fire, □ lance, L2 bleach bomb, ○ jump, △ storm, Options pause.

## Deploy

Netlify serves the repo root as-is (`netlify.toml` sets `publish = "."`); there is nothing to build.
