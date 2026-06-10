# KCUI - Minimal Semantic CSS UI

KCUI is a small CSS layer for semantic HTML interfaces. It provides a compact
set of layout, panel, form, table, and color classes without JavaScript or build
steps.

## Use

```html
<link rel="stylesheet" href="kcui.css">
```

`kcui.css` imports `vars.css` and `reset.css`.

Themes are loaded after `kcui.css`:

```html
<link rel="stylesheet" href="kcui.css">
<link rel="stylesheet" href="theme/native/auto.css">
```

## Structure

KCUI uses a small panel grammar:

```html
<body class="wrp">
    <header class="hdr">
        <h1>App</h1>
    </header>
    <main>
        <section class="pnl">
            <header class="hdr">
                <h2>Content</h2>
            </header>
            <section class="bdy">
                <label class="lbl">Name</label>
                <input class="ipt" type="text">
            </section>
            <footer class="ftr">
                <button>Submit</button>
            </footer>
        </section>
    </main>
    <footer class="ftr">
        <p>Status</p>
    </footer>
</body>
```

## Classes

- `.wrp`: width wrapper; on `body`, creates a full-height app layout.
- `.pnl`: panel container.
- `.hdr`, `.bdy`, `.ftr`: panel, page, and section regions.
- `.col`: wrapping flex columns.
- `.row`: horizontal flex row.
- `.mry`: CSS multi-column layout.
- `.btn`, `.ipt`, `.lbl`, `.dlg`, `.prg`, `.cod`: control aliases.
- `.prm`, `.sec`, `.inf`, `.scc`, `.wrn`, `.dng`, `.wht`, `.blk`, `.sys`: color
  utility classes.

KCUI also styles common semantic elements directly, including `fieldset`,
`legend`, `label`, `dialog`, `progress`, `table`, `code`, `kbd`, `samp`, `var`,
and `output`.

## Variables

Theme values live in `vars.css`. Override them after `kcui.css`:

```css
:root {
    --bg: #ffffff;
    --tx: #111111;
    --pad: 0.5;
}
```

Use `--pnl-cols` on a `.bdy` container to control auto-grid columns for child
`.pnl` blocks.

## Themes

The `theme/native/` themes are for desktop applications rendered through a
WebView. They use CSS system colors such as `Canvas`, `ButtonFace`, `Field`,
and `Highlight` so controls follow the host system where supported.

- `theme/native/auto.css`: follows the system light/dark mode.
- `theme/native/light.css`: forces native light mode.
- `theme/native/dark.css`: forces native dark mode.

## Files

| File | Description |
| ---- | ----------- |
| `vars.css` | CSS variables for spacing, colors, and sizing. |
| `reset.css` | Base reset and semantic element normalization. |
| `kcui.css` | Main stylesheet. |
| `theme/native/auto.css` | System-color theme for desktop WebView applications. |
| `theme/native/light.css` | Light system-color theme for desktop WebView applications. |
| `theme/native/dark.css` | Dark system-color theme for desktop WebView applications. |
| `demo.html` | Reference markup. |
| `LICENSE` | GPLv3 license text. |

## Status

This is a beta project. No stability or support guarantees are provided.

## License

KCUI is distributed under the GNU General Public License version 3.
