# miniflux-selfhst-theme

A dark theme (custom CSS) for [Miniflux v2](https://github.com/miniflux/v2), based loosely on the current design of the [selfh.st](https://selfh.st) website: bright letters on a near-black background, blue accents, rounded cards, pill buttons, and 20px left/right page gutters.

## Usage

1. In Miniflux, go to **Settings** and set **Theme** to *Dark - Sans serif* (recommended base).
2. Copy the contents of [miniflux-selfhst-dark.css](miniflux-selfhst-dark.css) into **Settings → Custom CSS**.
3. Save and reload.

## What it changes

- Dark `#1a1a1a` background with bright `#e6e6e6` text; secondary text in `#6e7281`, icons in `#676767`, and read items dim to gray
- Blue `#4c60d0` accents for hovers, primary buttons, the keyboard-navigation highlight, in-article links, and blockquote bars
- Article list items become solid `#212121` rounded cards instead of dotted outlines; buttons are pill-shaped; inputs get rounded corners and a soft blue focus ring
- 20px left/right page gutters on `<body>`, with the padding on `main` (and Miniflux's other stock offsets) removed so edges align
- Overrides every theme variable from Miniflux's `dark.css`, plus the colors hardcoded in `common.css` for the light theme (item-meta hover, entry title hover, `#ddd` borders, etc.), so it renders correctly on top of any base theme

The whole palette is defined once as `--sh-*` custom properties at the top of the file, so recoloring the theme means editing those few lines.

## Palette

| Role | Color |
| --- | --- |
| Page background | `#1a1a1a` |
| Cards / panels / inputs | `#212121` |
| Primary text | `#e6e6e6` |
| Secondary text | `#6e7281` |
| Icons | `#676767` |
| Accent (links, buttons, highlights) | `#4c60d0` |
| Hairlines / borders | `#2e2e2e` |

## Using a Nerd Font (or any custom font)

The simplest way is to use a font installed on the device you read Miniflux from — no webfont hosting needed:

1. Download and install a [Nerd Font](https://www.nerdfonts.com/font-downloads) on your computer/phone, e.g. JetBrainsMono Nerd Font. The "Mono" variants (`JetBrainsMono Nerd Font Mono`) keep the icon glyphs at single-cell width, which is what you want for reading.
2. In the custom CSS, change the `--font-family` line near the top of the `:root` block to put your font first, exactly as your OS lists its family name:

   ```css
   --font-family: "JetBrainsMono Nerd Font Mono", ui-monospace, monospace;
   ```

   `--entry-content-font-family` and `--entry-content-quote-font-family` already follow `--font-family`, so article text picks it up too. Devices without the font installed fall back to the next font in the list.

Loading the font as a webfont (`@font-face`) only works if the font file is served from the **same origin** as Miniflux (for example a `/fonts/` path on the reverse proxy in front of it): Miniflux sends a `Content-Security-Policy` of `default-src 'self'`, which blocks fonts loaded from CDNs, Google Fonts, or `data:` URLs.

Built against the Miniflux v2 stylesheets (`common.css` + `dark.css`) as of June 2026.

## License

[MIT](LICENSE)
