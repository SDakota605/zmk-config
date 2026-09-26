# zmk-config — Corne 42

ZMK firmware configuration for a **Corne 42** on **nice!nano v2** controllers.

Edit `config/corne.keymap` (in the browser is fine), commit, and GitHub Actions builds the firmware.
Download `firmware.zip` from the bottom of the completed run on the **Actions** tab.

## Layout

| Layer | Trigger | Purpose |
|---|---|---|
| 0 BASE | default | QWERTY, tap-hold thumbs |
| 1 NAV | hold left inner thumb | arrows on `hjkl`, left-hand mods, undo/cut/copy/paste |
| 2 SYM | hold right inner thumb | symbols (top row = shifted number row) |
| 3 NUM | hold left mid thumb | right-hand numpad, F1–F8 |
| 4 FUN | hold NAV + SYM (conditional) | Bluetooth, USB/BLE, bootloader, media |

Thumb keys (base layer):

| Pos | Tap | Hold |
|---|---|---|
| 36 | — | `Ctrl` |
| 37 | `Tab` | NUM |
| 38 | `Space` | NAV |
| 39 | `Enter` | SYM |
| 40 | `Backspace` | FUN |
| 41 | — | `Alt` |

Home row mods are **intentionally absent** — that's a later phase.

## Files

| File | What it does |
|---|---|
| `build.yaml` | which board/shield combos to build (incl. `settings_reset`) |
| `config/corne.keymap` | the keymap — the thing you actually edit |
| `config/corne.conf` | feature flags (ZMK Studio, deep sleep) |
| `config/west.yml` | pins the ZMK source revision |
| `.github/workflows/build.yml` | calls ZMK's official user-config build workflow |

## Flashing

1. Download and unzip `firmware.zip` from the Actions run.
2. Double-tap reset on a half → it mounts as a USB drive (`NICENANO`).
3. Drag the matching `.uf2` on. It reboots automatically. Repeat for the other half.

`settings_reset-nice_nano_v2-zmk.uf2` clears stored Bluetooth pairings — flash it to both halves when
they refuse to talk to each other, then reflash the real firmware.

## Notes

Design rationale, layer diagrams, and the change log live in the Obsidian vault at
`Atlas/Neovim & Corne 42/03 Corne 42/06 - My Layout.md`. **This repo is the authoritative copy of the
keymap**; the vault note mirrors it for context.
