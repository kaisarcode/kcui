# KCUI Extras

Optional extensions that build on KCUI's structural core.

Extras belong to layer 3 in the KCUI model:

1. semantic HTML
2. `kcui.css`
3. **extras** ← this layer
4. project CSS
5. project JS

Removing extras must not break document structure.

## Components

### Dialog (`kcui-dialog.css`)

Transitions and positional behavior for standard HTML `<dialog>` elements.

```html
<dialog class="dlg" open>
    <p>Dialog content</p>
</dialog>
```

### Drawer (`kcui-drawer.css`)

Collapsible panel using `.drw` with `[open]` attribute control.

```html
<dialog class="drw" open>
    <p>Drawer content</p>
</dialog>

<button onclick="document.querySelector('.drw').toggleAttribute('open')">
    Toggle
</button>
```

CSS custom properties:

- `--drw-width` (default: `20rem`)
- `--drw-position` (default: `fixed`)
- `--drw-closed` / `--drw-open` (transform values)

### Switch (`kcui-switch.css`)

Transform checkboxes and radios into toggle switches using `.swi`.

```html
<label>
    <input type="checkbox" class="swi">
    Notifications
</label>

<label>
    <input type="radio" name="theme" class="swi" checked>
    Dark
</label>

<label>
    <input type="radio" name="theme" class="swi">
    Light
</label>
```

Requires CSS custom properties from core: `--bd-sys`, `--tx-sys`, `--bg-prm`, `--bdw`, `--pad`.

### Tabs (`kcui-tabs.css`)

Accessible tab interface using ARIA roles inside `.tabs` container.

```html
<div class="tabs">
    <div role="tablist">
        <button role="tab" aria-selected="true" aria-controls="p1" id="t1">First</button>
        <button role="tab" aria-selected="false" aria-controls="p2" id="t2">Second</button>
    </div>
    <div role="tabpanel" id="p1" aria-labelledby="t1">
        <p>First panel content.</p>
    </div>
    <div role="tabpanel" id="p2" aria-labelledby="t2" hidden>
        <p>Second panel content.</p>
    </div>
</div>
```

Tab switching requires minimal JavaScript to toggle `aria-selected` and `hidden`.

## Colors

Color palettes that override KCUI's color variables without changing structure or providing a finished visual design.

| Color palette | File |
|---------------|------|
| Dracula | `colors/dracula.css` |
| Gruvbox | `colors/gruvbox.css` |
| Monokai | `colors/monokai.css` |
| Noir | `colors/noir.css` |
| Nord | `colors/nord.css` |
| One Dark | `colors/one-dark.css` |
| Solarized Dark | `colors/solarized-dark.css` |
| Tokyo Night | `colors/tokyo-night.css` |
| Vibrant Ink | `colors/vibrant-ink.css` |

Usage:

```html
<link rel="stylesheet" href="kcui.css">
<link rel="stylesheet" href="extra/colors/nord.css">
```
