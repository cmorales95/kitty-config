# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a kitty terminal emulator configuration directory (`~/.config/kitty`). Kitty reads `kitty.conf` on launch; changes require reloading kitty (`ctrl+shift+f5`) or restarting.

## Files

- **kitty.conf** — Main config: font, appearance, keybindings, layouts, and color scheme
- **startup.conf** — Session layout loaded on launch (3-pane split: main, side, bottom)

## Key Architecture Decisions

- **Layout**: Uses `splits` layout exclusively (`enabled_layouts splits`), not the default tall/stack layouts
- **Color scheme**: Catppuccin Macchiato — all color values (color0–color15, tab bar, marks, cursor) follow this palette
- **Font**: JetBrainsMono Nerd Font at size 16
- **Remote control**: Enabled (`allow_remote_control yes`, `listen_on unix:/tmp/kitty`) — allows `kitty @` commands from other processes
- **Scrollback pager**: nvim (not default `less`), opened via `ctrl+shift+s`

## Keybinding Conventions

Keybindings follow a consistent modifier pattern:
- **ctrl+shift+key** — General kitty actions (splits, tabs, scrollback, hints)
- **ctrl+alt+key** — Window navigation between splits (h/j/k/l) and tab jumping (1-5); chosen to avoid conflicts with nvim
- **ctrl+shift+r>key** — Resize splits (sequential/chord binding using `>`)
- **ctrl+shift+m>key** — Marker operations (e, t, c for error/todo/clear)
- **ctrl+shift+p>key** — Hints kitten paths/hashes

## When Editing

- Kitty conf uses `setting_name value` syntax (no `=` sign, no quotes around values)
- Keybindings: `map <shortcut> <action> [args]`
- Colors are hex values without quotes: `color4 #8aadf4`
- Comments use `#`
- Multi-key sequences use `>` separator: `map ctrl+shift+r>l resize_window wider 4`
