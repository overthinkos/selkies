# image/selkies — signpost (not the rule-set)

This submodule is the **Selkies streaming-desktop** image family (Wayland in a
container, browser-accessible): a `charly.yml` (plus per-kind sibling files) that imports the main
repo under the `charly` namespace and `build.yml` flat.

**Load these skills FIRST (R0):**

- `/charly-selkies:selkies` — the Selkies streaming engine (pixelflux/pcmflux).
- `/charly-selkies:selkies-desktop-layer` — the full Wayland desktop metalayer.
- `/charly-selkies:selkies-labwc-nvidia` — the GPU variant.
- `/charly-selkies:sway-desktop`, `/charly-selkies:chrome` — desktop + browser layers.

**Authoritative rules live in the `opencharly` superproject's root `CLAUDE.md`**
(R0–R10, hard-cutover, AI attribution, git-workflow). This file only signposts
and restates no rule. The multi-agent workflow is in `/charly-internals:agents`.
History lives in `CHANGELOG.md`.
