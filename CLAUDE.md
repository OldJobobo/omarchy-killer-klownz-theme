# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

An Omarchy desktop theme. No build system, no tests. Work is editing config files and propagating color values across them. Read `DESIGN.md` before making any color decisions — it defines the "Cotton Candy Cosmos" concept and which components intentionally break the dark-theme convention.

## How themes are applied


 not reload theme, the user will reload the theme.

## Color architecture

`colors.toml` is the canonical palette. Every other file is a consumer of those values — but each file uses its own syntax and variable names, so changes must be made per-file manually. There is no templating system.

Each app has its own file:

| File | App | Color syntax |
|------|-----|-------------|
| `alacritty.toml` | Alacritty terminal | TOML `[colors.*]` sections |
| `kitty.conf` | Kitty terminal | `color0`–`color15` key/value |
| `ghostty.conf` | Ghostty terminal | `palette = N=hex` |
| `warp.yaml` | Warp terminal | YAML |
| `walker.css` | App launcher | GTK CSS `@define-color` |
| `swayosd.css` | Volume/brightness OSD | GTK CSS `@define-color` |
| `mako.ini` | Notifications | INI `key=hex` |
| `hyprlock.conf` | Lock screen | `$var = rgba(...)` |
| `hyprland.conf` | Window borders only (included by main config) | `$var = rgb(...)` |
| `gtk.css` | GTK3/GTK4 apps | Adwaita `@define-color` overrides |
| `neovim.lua` | Neovim via aether.nvim | Lua `colors = {}` table |
| `btop.theme` | btop resource monitor | INI |
| `chromium.theme` | Chromium browser | JSON |
| `vencord.theme.css` | Discord/Vencord | CSS variables |
| `aether.override.css` | Aether neovim CSS override | CSS |
| `aether.zed.json` | Zed editor | JSON |
| `wofi.css` | Wofi (legacy, lower priority than walker) | CSS |

## Design intent — do not normalize

The Cotton Candy Cosmos concept deliberately uses mismatched backgrounds per component. Do not "fix" these to match each other:

- Walker bg is **light pink** (`#f5c2e7`) — intentional, it's the centerpiece rule-break
- SwayOSD bg is **dark green** (`#001a0d`) — not the same dark as windows
- Mako bg is **cream white** (`#fffaf0`) — fully inverted notification
- Windows/terminals stay **space black** (`#0b0a10`)

Waybar is not included in this theme.

## Icons and wallpapers

- `icons.theme` — single line pointing to the icon pack name (`Yaru-purple`)
- `backgrounds/` — wallpaper files; Omarchy picks from these randomly or by config
