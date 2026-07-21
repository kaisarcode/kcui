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
WebView. They use compact spacing and fixed light/dark palettes.

- `theme/native/auto.css`: follows the system light/dark mode.
- `theme/native/light.css`: forces native light mode.
- `theme/native/dark.css`: forces native dark mode.

The `theme/mobile/` themes are for mobile WebView applications. They use larger
spacing, larger input targets, and fixed light/dark palettes.

- `theme/mobile/auto.css`: follows the system light/dark mode.
- `theme/mobile/light.css`: forces mobile light mode.
- `theme/mobile/dark.css`: forces mobile dark mode.

## Files

| File | Description |
| ---- | ----------- |
| `vars.css` | CSS variables for spacing, colors, and sizing. |
| `reset.css` | Base reset and semantic element normalization. |
| `kcui.css` | Main stylesheet. |
| `theme/native/auto.css` | Desktop theme for WebView applications. |
| `theme/native/light.css` | Light desktop theme for WebView applications. |
| `theme/native/dark.css` | Dark desktop theme for WebView applications. |
| `theme/mobile/auto.css` | Touch-oriented theme for mobile WebView applications. |
| `theme/mobile/light.css` | Light touch-oriented theme for mobile WebView applications. |
| `theme/mobile/dark.css` | Dark touch-oriented theme for mobile WebView applications. |
| `demo.html` | Reference markup. |
| `LICENSE` | GPLv3 license text. |

---

## Beta Notice

This is a beta project created for personal needs, no guarantees are provided regarding its stability or future support. You are free to test it, use it, and modify it as you please.

If you'd like to reach out, you can send an email to kaisar@kaisarcode.com. Please note that I do not accept pull requests; the goal is to avoid long-term dependency on platforms like GitHub, and I do not maintain fixed infrastructure to guarantee long-term stability for these projects.

---

## License

[![GPLv3](https://www.gnu.org/graphics/gplv3-127x51.png)](https://www.gnu.org/licenses/gpl-3.0.html)

This project is distributed under the **GNU General Public License version 3 (GPLv3)**.
