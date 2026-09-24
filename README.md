# OpenIcon

370 icons for interfaces and terminals, packed as an [OpenIcon](https://logicsrc.com/openicon) set. Each icon is an SVG, a set of PNGs, and three terminal glyphs (Nerd Font, Unicode, ASCII).

- **259 drawn icons** on a 24x24 grid: 2px strokes, round caps and joins, 2 units of padding, `currentColor`. They cover actions, navigation, communication, media, files, status, time, commerce, developer tools, devices and the editor.
- **111 brand logos**, from GitHub, X, Bluesky, Mastodon, Discord, Slack, Signal and WhatsApp to npm, Stripe and Bitcoin.
- **Terminal glyphs for every icon.** `mail` is 󰇰 in a Nerd Font, ✉ in a plain UTF-8 terminal, and `@` anywhere else. [hqtui](https://hqtui.com) ships this set as its default icon pack.

## What is here

```
openicon.json          the descriptor: every icon, its names, files and terminal glyphs
svg/<key>.svg          24x24, currentColor
png/<size>/<key>.png   16, 20, 24, 32, 48, 64, 128 and 256 px, drawn in #111
sprite.svg             every icon as <symbol id="oi-<key>">
index.html             the whole set on one page
```

## Use it

Inline an SVG, or reference the sprite:

```html
<svg width="20" height="20"><use href="sprite.svg#oi-mail"/></svg>
```

The icons inherit `color` from the surrounding text. In a terminal, read `tui` from `openicon.json`:

```json
{ "key": "mail", "aliases": ["email", "envelope"],
  "tui": { "nerd": "󰇰", "nerd_code": "f01f0", "nerd_name": "md-email_outline", "unicode": "✉", "ascii": "@" } }
```

Use `nerd` when the terminal font is a Nerd Font, otherwise `unicode`, and fall back to `ascii`.

## How it was made

Everything is built by [`icon`](https://github.com/profullstack/cli-tools#icon) in profullstack/cli-tools, from `src/icon-set.ts` and `src/icon-brands.ts`.

- **Drawn icons:** hand-authored as SVG by Claude (`made_by: ai`). Plain shapes such as arrows, the plus sign and the check mark share their geometry with every other line icon set.
- **Brand logos:** not drawn. They are fetched from [Simple Icons](https://simpleicons.org) 16.32.0. Nine brands asked Simple Icons to remove their logos; those come from [Font Awesome Free](https://fontawesome.com) 7.3.1. Each brand entry records its source and licence.
- **Nerd Font codepoints:** resolved by name from [Nerd Fonts](https://www.nerdfonts.com) 3.4.0.

## Licence

| Part | Licence |
|---|---|
| Drawn icons | MIT |
| Simple Icons logos | CC0 1.0 |
| Font Awesome logos | CC BY 4.0: credit "Font Awesome Free by Fonticons, Inc." |

Every brand logo is a trademark of its owner. Use it to refer to that product or service, not to imply endorsement.
