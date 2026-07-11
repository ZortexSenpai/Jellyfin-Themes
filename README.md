# Jellyfin-Themes

A collection of custom CSS themes (skins) for the [Jellyfin](https://jellyfin.org/) web client.

| Theme | Description | Flavors |
|---|---|---|
| [**Plexifin**](Plexifin/) | A Plex-style skin — one flat background plane, dark lavender accent | Catppuccin: Latte, Frappé, Macchiato, Mocha · Dark: OLED, Material, Midnight, Graphite, Plex Amber |
| [**Shellyfin**](Shellyfin/) | A terminal (CLI) skin — monospace type, phosphor glow, CRT scanlines | Amber (VT220), Violet, Ice, Mono |
| [**Samurai**](Samurai/) | A feudal-Japan skin — sumi-ink lacquer, vermillion accent, gold trim, mincho serif type | Aiiro (indigo), Sakura, Matcha, Kogane (gold) |
| [**Sakura**](Sakura/) | A night cherry-blossom skin — plum-dark sky, blossom-pink accent, falling petal silhouettes, rounded webfonts, blossom icons | Seasonal flowers: Ume, Fuji, Ajisai, Momiji |

Tested against the Jellyfin **10.10 / 10.11** web client. Set your display theme to **Dark** in Jellyfin (Settings → Display) for best results.

## How to use

Jellyfin lets you load custom CSS in two places:

- **Server-wide (all users):** Dashboard → **General** → **Custom CSS**
- **Per-user:** Settings → **Display** → **Custom CSS** (enable "Disable server-provided custom CSS code" if you want it to replace the server theme)

Paste an `@import` that pulls the theme from this repo via the [jsDelivr](https://www.jsdelivr.com/) CDN — you'll automatically get updates whenever the theme changes.

### Plexifin

```css
@import url("https://cdn.jsdelivr.net/gh/ZortexSenpai/Jellyfin-Themes@main/Plexifin/theme.css");
```

### Shellyfin

```css
@import url("https://cdn.jsdelivr.net/gh/ZortexSenpai/Jellyfin-Themes@main/Shellyfin/theme.css");
```

### Samurai

```css
@import url("https://cdn.jsdelivr.net/gh/ZortexSenpai/Jellyfin-Themes@main/Samurai/theme.css");
```

### Sakura

```css
@import url("https://cdn.jsdelivr.net/gh/ZortexSenpai/Jellyfin-Themes@main/Sakura/theme.css");
```

## Flavors

Each theme ships optional color flavors in its `flavors/` folder. A flavor only re-points the color tokens, so it must be loaded **after** the base theme — base first, flavor second:

```css
/* Plexifin + Catppuccin Mocha */
@import url("https://cdn.jsdelivr.net/gh/ZortexSenpai/Jellyfin-Themes@main/Plexifin/theme.css");
@import url("https://cdn.jsdelivr.net/gh/ZortexSenpai/Jellyfin-Themes@main/Plexifin/flavors/catppuccin-mocha.css");
```

```css
/* Shellyfin + amber (VT220) phosphor */
@import url("https://cdn.jsdelivr.net/gh/ZortexSenpai/Jellyfin-Themes@main/Shellyfin/theme.css");
@import url("https://cdn.jsdelivr.net/gh/ZortexSenpai/Jellyfin-Themes@main/Shellyfin/flavors/amber.css");
```

### Available flavors

**Plexifin** (`Plexifin/flavors/`)

| Flavor | Import path |
|---|---|
| Catppuccin Latte (light) | `Plexifin/flavors/catppuccin-latte.css` |
| Catppuccin Frappé | `Plexifin/flavors/catppuccin-frappe.css` |
| Catppuccin Macchiato | `Plexifin/flavors/catppuccin-macchiato.css` |
| Catppuccin Mocha | `Plexifin/flavors/catppuccin-mocha.css` |
| OLED — true black, for OLED screens | `Plexifin/flavors/oled.css` |
| Material — brighter OLED: Grey 900 + Deep Purple | `Plexifin/flavors/material.css` |
| Midnight — deep blue-black, steel accent | `Plexifin/flavors/midnight.css` |
| Graphite — neutral dark gray, silver accent | `Plexifin/flavors/graphite.css` |
| Plex Amber — charcoal + Plex's gold accent | `Plexifin/flavors/plex-amber.css` |

**Shellyfin** (`Shellyfin/flavors/`)

| Flavor | Import path |
|---|---|
| Amber (VT220) | `Shellyfin/flavors/amber.css` |
| Violet | `Shellyfin/flavors/violet.css` |
| Ice | `Shellyfin/flavors/ice.css` |
| Mono | `Shellyfin/flavors/mono.css` |

**Samurai** (`Samurai/flavors/`)

| Flavor | Import path |
|---|---|
| Aiiro — indigo, silver trim | `Samurai/flavors/aiiro.css` |
| Sakura — cherry-blossom pink | `Samurai/flavors/sakura.css` |
| Matcha — tea green | `Samurai/flavors/matcha.css` |
| Kogane — gold on black lacquer | `Samurai/flavors/kogane.css` |

**Sakura** (`Sakura/flavors/`) — the seasons of blossom viewing

| Flavor | Import path |
|---|---|
| Ume — plum blossom, late winter | `Sakura/flavors/ume.css` |
| Fuji — wisteria, early summer | `Sakura/flavors/fuji.css` |
| Ajisai — hydrangea, rainy season | `Sakura/flavors/ajisai.css` |
| Momiji — maple, autumn | `Sakura/flavors/momiji.css` |

## Alternative: paste the CSS directly

Prefer not to depend on a CDN? Open the theme's `theme.css`, copy the whole file, and paste it into the Custom CSS box instead. To add a flavor, paste its contents **below** the base theme.

## Customizing

All colors live in the `:root` block at the top of each `theme.css` — accent, background, text and shape tokens are documented inline. Fork the repo, tweak the variables, and point the `@import` at your fork.

Shellyfin quick dials: set `--scanline-opacity: 0` to disable the CRT scanline effect, and `--glow: none` to disable the phosphor text glow.

Samurai quick dials: set `--pattern-opacity: 0` to disable the seigaiha wave overlay, and `--seal` to change the character stamped on the login scroll (default `"侍"`; `""` removes it).

Sakura quick dials: set `--petal-opacity: 0` to disable the falling petals (all decorative animation also pauses automatically for users who prefer reduced motion, and the petals hide during video playback). Fonts (Zen Maru Gothic body, Shippori Mincho titles) load from Google Fonts — offline servers silently fall back to system fonts.

## Note on caching

jsDelivr caches the `@main` branch for up to 12 hours, so updates may take a while to show up. To pin an exact version, replace `@main` with a commit hash:

```css
@import url("https://cdn.jsdelivr.net/gh/ZortexSenpai/Jellyfin-Themes@<commit-hash>/Plexifin/theme.css");
```
