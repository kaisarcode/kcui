# Themes and palettes

KCUI keeps structure, component geometry, and color values separate. A UI theme can change dimensions and presentation while a palette defines semantic colors. Neither requires rewriting the HTML.

## Styling layers

The intended order is:

1. Semantic HTML defines meaning and source order.
2. `kcui.css` provides the structural layout, native controls, and default variables.
3. Optional modules add features such as tabs, switches, drawers, and dialog transitions.
4. A UI theme changes geometry, typography, spacing, and interaction presentation.
5. A color palette supplies semantic color values.
6. Application CSS and JavaScript define product-specific presentation and behavior.

The layers are optional beyond the core. A theme should not define its own hardcoded color scheme when a palette can supply the values. Modules should consume the same palette variables as the core.

## UI themes

The repository includes `themes/kcui-mobile.css`, a touch-oriented theme activated by a class on the document root.

```html
<link rel="stylesheet" href="kcui.css">
<link rel="stylesheet" href="themes/kcui-mobile.css">
```

```html
<html lang="en" class="theme-mobile">
```

The mobile theme increases typical control touch targets, spacing, and corner radii. It does not replace the structural classes or the document order. Without the root class, KCUI uses its base presentation.

## Color palettes

The core stylesheet contains KCUI's default dark colors. Additional palettes live under `palettes/`. For example:

```html
<link rel="stylesheet" href="kcui.css">
<link rel="stylesheet" href="palettes/color-monokai.css">
```

```html
<html lang="en" class="color-monokai">
```

The provided example palettes are Default, Amber, Matrix, Monokai, and Tokyo. Default colors are built into `kcui.css`; `color-default.css` supplies the optional Default Light mode. Amber and Matrix are dark-only. Monokai and Tokyo provide dark and light variants.

The default design direction is dark-first. Light is optional for an individual palette rather than a requirement for every theme.

## System color preference and overrides

Where a palette supports both modes, the absent mode class follows the browser's `prefers-color-scheme` preference. An explicit `mode-light` or `mode-dark` class overrides that preference.

```html
<html lang="en" class="color-tokyo mode-light">
```

To return to automatic selection, remove the mode class. For a dark-only palette, the palette remains dark regardless of the system's preference. Do not force a light mode on palettes that do not provide one.

The demo includes independent selectors for the UI theme, palette, and color mode. The selector code is an example of application behavior, not a dependency of KCUI.

## Semantic variables

The core owns a semantic set of CSS custom properties. The same suffix identifies a related surface, border, and text role:

- `--bg`, `--bd`, and `--tx` for the root.
- `--bg-sys`, `--bd-sys`, and `--tx-sys` for controls.
- `--bg-hdr`, `--bd-hdr`, and `--tx-hdr` for headers.
- `--bg-bdy`, `--bd-bdy`, and `--tx-bdy` for bodies.
- `--bg-ftr`, `--bd-ftr`, and `--tx-ftr` for footers.
- `--bg-pnl`, `--bd-pnl`, and `--tx-pnl` for panels.
- `--bg-cod`, `--bd-cod`, and `--tx-cod` for code.
- `--bg-prm`, `--bd-prm`, `--tx-prm`, and equivalent groups for `sec`, `inf`, `scc`, `wrn`, `dng`, `wht`, and `blk`.
- `--tx-lnk` and `--tx-lnk-hover` for ordinary links and their interaction state.

Nav links use the containing text color normally and `--bg-prm` on hover or keyboard focus. Links in headings retain the heading color during interaction. Buttons styled by semantic state classes use their state text and background variables.

A palette must provide legible combinations, not merely familiar accent colors. Check text on the actual background where it renders: panels, headers, bodies, inputs, code, and semantic buttons. Preserve meaningful visual separation between nearby surfaces and borders.

## Geometry variables

KCUI also exposes `--fsz` for font size, `--pad` for spacing, `--bdw` for border width, `--rad` for corner radius, `--min` and `--max` for width constraints, and `--col` for automatic layout track width.

These variables are separate from the color system. A theme can change them without becoming a palette, and a palette can change color values without changing component dimensions.

## Next step

Read the [optional modules guide](../modules/README.md) for interactive components and their responsibilities.
