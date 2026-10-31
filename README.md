# OpenIcon

452 icons for interfaces and terminals, packed as an [OpenIcon](https://logicsrc.com/openicon) set. Each icon is an SVG, a set of PNGs, and three terminal glyphs (Nerd Font, Unicode, ASCII).

- **261 drawn icons** on a 24x24 grid: 2px strokes, round caps and joins, 2 units of padding, `currentColor`. They cover actions, navigation, communication, media, files, status, time, commerce, developer tools, devices and the editor.
- **191 brand logos**, including 111 external brands and all 80 Profullstack properties, from GitHub, X, Bluesky, Mastodon, Discord, Slack, Signal and WhatsApp to npm, Stripe, Bitcoin and Profullstack services.
- **Terminal glyphs for every icon.** `mail` is 󰇰 in a Nerd Font, ✉ in a plain UTF-8 terminal, and `@` anywhere else. [hqtui](https://hqtui.com) ships this set as its default icon pack.

## What is here

```
openicon.json          the descriptor: every icon, its names, files and terminal glyphs
svg/<key>.svg          24x24; UI icons use currentColor, brand marks keep their source artwork
png/<size>/<key>.png   16, 20, 24, 32, 48, 64, 128 and 256 px, drawn in #111
sprite.svg             every icon as <symbol id="oi-<key>">
index.html             the whole set on one page
```

## One drawing, five styles

**Simple** is the line set above for UI icons: monochrome, `currentColor`, and the default. Brand logos keep their published mark and color. The other four are colour styles for UI icons.

| Style | Material | Good for |
|---|---|---|
| `hq` | Glass and enamel under a warm key light, at the finish of the [OpenEmoji](https://logicsrc.com/openemoji) set | Sitting beside the emoji; anywhere the 2000s gloss is the point |
| `agentic-matte` | Flat tonal planes with hard boundaries and one cool edge-light | The general-purpose colour style: holds at 20px on light and dark |
| `agentic-machined` | Milled anodized aluminium, hairline chamfers, one anodized accent | Hardware and rack UIs, shown large |
| `agentic-emissive` | Near-black body with the working part lit | Dark terminals; it disappears on a light ground |

Every style lays its files out the same way, under its own directory (`hq/`, `styles/agentic-matte/`, …):

```
<style>/png/<size>/<key>.png    16 to 256 px, every icon
<style>/webp/<size>/<key>.webp  64 and 128 px
<style>/svg/<key>.svg           brands only: the logo in its owner's colour
<style>/style.txt               the art direction every icon in it was drawn under
```

- **The UI icons were drawn by `gpt-image-2`, once per style** (`random` and `vote`, added later, by `gpt-image-2.5-flare`: `gpt-image-2` no longer takes a transparent background). Each drawing starts from the icon's own simple glyph, so the silhouette and meaning stay the same. HQ also used OpenEmoji artwork (laptop, gem, light bulb) as a style reference; the agentic styles use none, because that reference is where the gloss comes from. Colour is set per category in every style, and meaning overrides it: green for add and check, red for delete and errors, gold for warnings and stars.
- **The brand marks keep their published geometry and owner colour in every style.** The 80 Profullstack service marks come from each property's published logo or favicon; when a property has not published a separate mark, the Profullstack house mark is used. Each source URL is recorded in `openicon.json`.
- **In `openicon.json`,** the top-level `styles` lists them and `style_info` describes each one; every icon carries a `styles` map keyed by the same ids. The first HQ release's `hq` blocks are still written, as the same objects under their older name.

`agentic` on its own means `agentic-matte`.

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
- **External brand logos:** fetched from [Simple Icons](https://simpleicons.org) 16.32.0. Nine brands asked Simple Icons to remove their logos; those come from [Font Awesome Free](https://fontawesome.com) 7.3.1. Each brand entry records its source and licence.
- **Profullstack service logos:** taken from all 80 properties on the Profullstack site list. Published SVGs stay vector; PNG app icons are embedded in the generated SVG when a property has no SVG logo. Each source URL is recorded in the descriptor.
- **Nerd Font codepoints:** resolved by name from [Nerd Fonts](https://www.nerdfonts.com) 3.4.0.

## Licence

| Part | Licence |
|---|---|
| Drawn icons | MIT |
| Simple Icons logos | CC0 1.0 |
| Font Awesome logos | CC BY 4.0: credit "Font Awesome Free by Fonticons, Inc." |
| Profullstack property marks | Profullstack, Inc. service marks; no additional license is granted |

Every brand logo is a trademark of its owner. Use it to refer to that product or service, not to imply endorsement.
