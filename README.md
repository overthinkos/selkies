# overthinkos/selkies

The **Selkies / Sway streaming-desktop image family** for
[Overthink](https://github.com/overthinkos/overthink), split into its own
repository and mounted as a git submodule at `image/selkies` of the main repo.

## What's here

| Kind | Entries |
|---|---|
| `image:` | `selkies-labwc` (CPU streaming desktop, CachyOS base), `sway-browser-vnc` (minimal Sway + wayvnc + Chrome, Fedora base) |
| `eval:` | `eval-sway-browser-vnc-pod`, `eval-selkies-labwc-pod` (disposable R10 beds) |

The desktop **layers** (`selkies-desktop`, `sway-desktop-vnc`, and their subtrees:
chrome, labwc, sway, wayvnc, pixelflux/selkies, waybar, swaync, pipewire, …) are
**not** here — they stay in the main repo. `selkies-desktop` is shared with
`openclaw-desktop` and its subtree is shared widely, so by the shared-layer rule
they remain in `main/layers/` and are reached here by `@github` reference.

## Composition by reference — nothing is vendored

- `agent-forwarding` + `ov` + `build.yml` pin the ecosystem tag `v2026.141.1600`;
- the selkies desktop metalayers (`selkies-desktop`, `sway-desktop-vnc`) AND `dbus`
  pin `v2026.144.0531` — the metalayers carry the chrome CDP/MCP + pixelflux fixes
  that landed after the older ecosystem tag, and they transitively require `dbus` at
  their own tag, so the explicit `dbus` pin matches (avoiding a swaync/a11y-tools
  `require: dbus` conflict);
- `pixi`/`nodejs` are pulled transitively by the metalayers at `v2026.144.0531`
  while the shared arch/fedora builders pin them at the ecosystem `v2026.141.1600`
  → 2 accepted newest-wins resolver notices (the resolver uses the newest);
- bases arrive via namespaced imports: `ov.fedora` / `ov.fedora-builder` /
  `ov.arch-builder` (main, `v2026.143.844`), `cachyos.cachyos` (`v2026.143.844`).
  Builder maps are declared per-image (they do not cross a namespace boundary).

## Build

```bash
ov --repo overthinkos/selkies image build selkies-labwc        # anywhere
ov -C image/selkies image build sway-browser-vnc               # from the parent
ov -C image/selkies eval run eval-sway-browser-vnc-pod         # R10 bed
```

## Verification

- `eval-sway-browser-vnc-pod` / `eval-selkies-labwc-pod` are the disposable R10
  beds (build → deploy → eval live → fresh update → teardown).
- The CPU desktops (`selkies-labwc`, `sway-browser-vnc`) run full deploy-scope R10.

---

*Assisted-by: Claude (fully tested and validated)*
