# image/selkies — signpost (not the rule-set)

This submodule is the **Selkies streaming-desktop** image family (Wayland in a
container, browser-accessible): an `overthink.yml` (plus per-kind sibling files) that imports the main
repo under the `ov` namespace and `build.yml` flat.

**Load these skills FIRST (R0):**

- `/ov-selkies:selkies` — the Selkies streaming engine (pixelflux/pcmflux).
- `/ov-selkies:selkies-desktop-layer` — the full Wayland desktop metalayer.
- `/ov-selkies:selkies-labwc-nvidia` — the GPU variant.
- `/ov-selkies:sway-desktop`, `/ov-selkies:chrome` — desktop + browser layers.

**Authoritative rules live in the `overthink` superproject's root `CLAUDE.md`**
(R0–R10, hard-cutover, AI attribution, git-workflow). This file only signposts
and restates no rule. The multi-agent workflow is in `/ov-internals:agents`.
History lives in `CHANGELOG.md`.
