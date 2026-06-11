# miniflux-selfhst-theme

A dark theme (custom CSS) for [Miniflux v2](https://github.com/miniflux/v2), based loosely on the current design of the [selfh.st](https://selfh.st) website: bright letters on a near-black background, blue accents, rounded cards, pill buttons, and 20px left/right page gutters.

## Usage

1. In Miniflux, go to **Settings** and set **Theme** to *Dark - Sans serif* (recommended base).
2. Copy the contents of [`miniflux-selfhst-dark.css`](miniflux-selfhst-dark.css) into **Settings → Custom CSS**.
3. Save and reload.

## What it changes

- Near-black `#0e0e0e` background with bright `#f2f2f2` text and bold white article titles; read items dim to gray
- Blue accents (`#3b82f6` / `#60a5fa`) for hovers, primary buttons, the keyboard-navigation highlight, in-article links, and blockquote bars
- Article list items become solid rounded cards instead of dotted outlines; buttons are pill-shaped; inputs get rounded corners and a soft blue focus ring
- 20px left/right page gutters on `main` and the header, with Miniflux's small stock offsets zeroed so edges align
- Overrides every theme variable from Miniflux's `dark.css`, plus the colors hardcoded in `common.css` for the light theme (item-meta hover, entry title hover, `#ddd` borders, etc.), so it renders correctly on top of any base theme

## Palette

| Role | Color |
| --- | --- |
| Page background | `#0e0e0e` |
| Cards / panels | `#151515` / `#161616` |
| Primary text | `#f2f2f2` (titles `#ffffff`) |
| Secondary text | `#9ca3af` |
| Accent | `#3b82f6` (hover `#60a5fa`) |
| Hairlines / borders | `#1f1f1f` / `#262626` |

Built against the Miniflux v2 stylesheets (`common.css` + `dark.css`) as of June 2026.
