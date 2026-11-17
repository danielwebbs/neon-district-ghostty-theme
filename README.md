# Neon District

A portable cyberpunk theme for the [Ghostty](https://ghostty.org) terminal. It has a dark navy background, neon pink, purple and cyan accents, and a tiled grid background image.

## Files

| File | Purpose |
| --- | --- |
| `theme.ghostty` | Main config fragment: palette, colors, padding, split styling, titlebar, background image. |
| `cyberpunk.css` | GTK CSS that draws a pink underline on the active tab. Linux/GTK only. |
| `images/grid.png` | Tiled background image. |

## Install

1. Clone into the Ghostty config directory:

   ```sh
   git clone git@github.com:danielwebbs/neon-district-ghostty-theme.git ~/.config/ghostty/neon-district
   ```

2. Add this line to the end of `~/.config/ghostty/config`:

   ```
   config-file = neon-district/theme.ghostty
   ```

3. Reload Ghostty (`ctrl+shift+,`) or restart it.

The folder name must stay `neon-district` unless the `config-file` line changes to match.

## How it works

- `config-file` loads `theme.ghostty` after the main config, so its values override earlier ones, including any `theme =` line.
- Relative paths inside `theme.ghostty` (`cyberpunk.css`, `images/grid.png`) resolve from this folder, not from `~/.config/ghostty`. This is what keeps the theme self-contained.
- `gtk-custom-css` only applies on Linux with the GTK build. On macOS it is ignored.

## Palette

| Role | Color |
| --- | --- |
| Background | `#0b0c15` |
| Foreground | `#d6dcf5` |
| Cursor / accent pink | `#ff2a6d` |
| Selection | `#51309a` |
| ANSI 0–7 | `#23263a #ff4d7e #2bffa8 #ffe45e #4da6ff #c58aff #1fe5f0 #d6dcf5` |
| ANSI 8–15 | `#7078a3 #ff7a9c #7dffc8 #fff29a #85c2ff #dcb3ff #7df4ff #ffffff` |

## Editing notes for agents

- Keep all paths in `theme.ghostty` relative so the folder stays portable.
- Validate changes with `ghostty +validate-config`. It reports unknown keys and bad values.
- Test by reloading Ghostty and checking splits, tabs, and a colored command like `ls --color` or `git log --oneline --graph`.
- Accent pink `#ff2a6d` is reused for the cursor, split divider, titlebar text, and tab underline. Change all four together.
