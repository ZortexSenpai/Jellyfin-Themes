# Jellyfin-Themes

A collection of custom CSS themes (skins) for the [Jellyfin](https://jellyfin.org/) web client.

| Theme | Description | Flavors |
|---|---|---|
| [**Plexifin**](Plexifin/) | A Plex-style skin — one flat background plane, dark lavender accent | Catppuccin: Latte, Frappé, Macchiato, Mocha |
| [**Shellyfin**](Shellyfin/) | A terminal (CLI) skin — monospace type, phosphor glow, CRT scanlines | Amber (VT220), Violet, Ice, Mono |

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

**Shellyfin** (`Shellyfin/flavors/`)

| Flavor | Import path |
|---|---|
| Amber (VT220) | `Shellyfin/flavors/amber.css` |
| Violet | `Shellyfin/flavors/violet.css` |
| Ice | `Shellyfin/flavors/ice.css` |
| Mono | `Shellyfin/flavors/mono.css` |

## Alternative: paste the CSS directly

Prefer not to depend on a CDN? Open the theme's `theme.css`, copy the whole file, and paste it into the Custom CSS box instead. To add a flavor, paste its contents **below** the base theme.

## Customizing

All colors live in the `:root` block at the top of each `theme.css` — accent, background, text and shape tokens are documented inline. Fork the repo, tweak the variables, and point the `@import` at your fork.

Shellyfin quick dials: set `--scanline-opacity: 0` to disable the CRT scanline effect, and `--glow: none` to disable the phosphor text glow.

## Note on caching

jsDelivr caches the `@main` branch for up to 12 hours, so updates may take a while to show up. To pin an exact version, replace `@main` with a commit hash:

```css
@import url("https://cdn.jsdelivr.net/gh/ZortexSenpai/Jellyfin-Themes@<commit-hash>/Plexifin/theme.css");
```
