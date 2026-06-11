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

### Loading it as a webfont instead

Miniflux 2.2.2+ can load fonts from the web: in **Settings**, set **External font hosts** to a space-separated list of hostnames (no `https://`, no paths). Miniflux adds them to its Content-Security-Policy — `font-src` for the font files, plus `style-src` so stylesheet imports work. With the field empty, the CSP allows no font sources at all, which is why an `@font-face` in custom CSS silently does nothing by default.

For a font that's on Google Fonts, allow `fonts.googleapis.com fonts.gstatic.com`, then import it on the **first line** of the custom CSS (`@import` must come before all other rules) and point `--font-family` at it:

```css
@import url("https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;600&display=swap");
```

Nerd Fonts themselves aren't on Google Fonts, so for one of those: upload the `.woff2` to any host you control (your Miniflux domain works too, but it still has to be listed — the default is to block everything), add that hostname to **External font hosts**, and declare the font anywhere in the custom CSS:

```css
@font-face {
    font-family: "JetBrainsMono Nerd Font Mono";
    src: url("https://files.example.com/fonts/JetBrainsMonoNerdFontMono-Regular.woff2") format("woff2");
    font-weight: 400;
    font-style: normal;
}
```

Built against the Miniflux v2 stylesheets (`common.css` + `dark.css`) as of June 2026.

## License

[MIT](LICENSE)
