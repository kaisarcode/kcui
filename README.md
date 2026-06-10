# KCUI - Minimal Semantic CSS UI

KCUI is a minimal, portable, semantic CSS UI. It keeps structure in HTML and
applies style through a small class grammar plus coherent element styling.

## Features

- **Panel grammar**: `.pnl`, `.hdr`, `.bdy`, `.ftr` for composable blocks.
- **Semantic defaults** for `fieldset`, `legend`, `label`, `dialog`, `progress`,
  `code`, `kbd`, `samp`, `var`, and `output`.
- **Layout helpers**: `.wrp` (full-viewport wrapper), `.col` (flex columns),
  `.row` (horizontal groups), `.mry` (multi-column), auto-grid in `.bdy`.
- **Utility classes**: `.btn`, `.ipt`, `.lbl`, `.dlg`, `.prg`, `.cod`, plus
  color utilities `.prm`, `.sec`, `.inf`, `.scc`, `.wrn`, `.dng`, `.wht`,
  `.blk`, `.sys`.
- **Dark by default** with a light theme in `theme/light.css`.
- **Holy-grail layout**: `body.wrp` is a flex column, the last `.pnl` inside
  `main` fills remaining space, borders form a continuous column.
- **Flat style**: no shadows, no rounded corners, no forced uppercase.
- **System font**, compact density (`--fsz: 13px`).
- **Keyboard accessible**: `focus-visible` outlines on all elements, accent
  highlight on inputs.
- **Motion only when preferred**: transitions inside
  `@media (prefers-reduced-motion: no-preference)`.

## Getting Started

```html
<link rel="stylesheet" href="kcui.css">
```

- Use semantic HTML with KCUI classes:

```html
<body class="wrp">
    <header class="hdr">
        <h1>App</h1>
        <nav><menu><li><a href="#">Item</a></li></menu></nav>
    </header>
    <main>
        <section class="pnl">
            <header class="hdr"><h2>Content</h2></header>
            <div class="bdy">
                <label class="lbl">Name</label>
                <input class="ipt" type="text">
            </div>
        </section>
    </main>
    <footer class="ftr">
        <p>Status bar</p>
    </footer>
</body>
```

## Themes

- **Default (dark)**: works out of the box, no extra imports.
- **Light**: add `theme/light.css` after `kcui.css`.

```html
<link rel="stylesheet" href="kcui.css">
<link rel="stylesheet" href="theme/light.css">
```

## Customization

Override any variable from `vars.css` in your own stylesheet after `kcui.css`:

```css
:root { --bg: #fff; --tx: #111; --pad: 0.5; }
```

Use `--pnl-cols` on a `.bdy` container to control auto-grid columns for nested
`.pnl` blocks.

## File Structure

| File | Description |
| ---- | ----------- |
| `vars.css` | Design tokens (spacing, palette, semantic colors). |
| `reset.css` | Base reset imported by `kcui.css`. |
| `kcui.css` | Main library: panel grammar, layout, controls, utilities. |
| `theme/light.css` | Optional light theme override. |
| `demo.html` | Reference markup using the KCUI class grammar. |

---

## Beta Notice

This is a beta project. It was created out of a personal need for these libraries,
but no guarantees are provided regarding its stability or future support.
You are free to test it, use it, and modify it as you please.

If you'd like to reach out, you can send an email to kaisar@kaisarcode.com.
Please note that I do not accept pull requests; the goal is to avoid long-term
dependency on platforms like GitHub, and I do not maintain fixed infrastructure
to guarantee long-term stability for these projects.

---

## License

[![GPLv3](https://www.gnu.org/graphics/gplv3-127x51.png)](https://www.gnu.org/licenses/gpl-3.0.html)

This project is distributed under the **GNU General Public License version 3 (GPLv3)**.
