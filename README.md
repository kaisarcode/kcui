# KCUI

KCUI is a minimal and responsive CSS framework by KaisarCode.

The framework is built around a small set of structural classes, semantic color utilities, and native HTML elements. The current build is distributed as a single `kcui.css` file containing variables, base element styles, layout rules, controls, utilities, and responsive behavior.

## Features

- Minimal CSS structure
- Responsive page layout
- Header, body, and footer regions
- Panels
- Width wrapper
- Automatic columns
- Masonry columns
- Horizontal article + aside layout
- Form controls
- Checkbox switch
- Dialog, progress, and code styles
- Semantic color utilities
- CSS custom properties for theme creation

## Quick start

Add KCUI to your page:

```html
<link rel="stylesheet" href="kcui.css">
```

Basic application structure:

```html
<div class="app">
    <header class="hdr">
        <div class="wrp">
            <h1>KCUI</h1>
            <nav>
                <a href="#">Item</a>
            </nav>
        </div>
    </header>

    <main class="bdy">
        <div class="wrp row">
            <article class="pnl">
                <header class="hdr">
                    <h2>Article</h2>
                </header>

                <section class="bdy">
                    Main content.
                </section>
            </article>

            <aside class="pnl">
                <header class="hdr">
                    <h2>Aside</h2>
                </header>

                <section class="bdy">
                    Aside content.
                </section>
            </aside>
        </div>
    </main>

    <footer class="ftr">
        <div class="wrp">
            Footer
        </div>
    </footer>
</div>
```

## Variables

KCUI uses CSS custom properties as its theme layer.

```css
:root {
    --fsz: 13px;
    --pad: 0.625rem;
    --bdw: 1px;
    --rad: 0;
    --min: 360px;
    --max: 1024px;
    --col: 12rem;
}
```

The default theme also defines text, background, and border colors for system, code, header, body, footer, panel, primary, secondary, info, success, warning, danger, white, and black.

A new theme can be created by overriding these variables without changing the structural rules.

## Layout

### `.app`

Main application container. It fills the viewport and keeps the page header and footer visible while the central body scrolls.

### `.wrp`

Width wrapper.

```html
<div class="wrp">...</div>
```

It uses `--max` as its maximum width and centers itself horizontally.

### `.pnl`

Panel container.

```html
<section class="pnl">
    <header class="hdr">...</header>
    <section class="bdy">...</section>
    <footer class="ftr">...</footer>
</section>
```

Panels use the default panel colors, border, radius, and vertical spacing.

### `.hdr`, `.bdy`, `.ftr`

Reusable page and panel regions.

All three use `--pad` for consistent spacing.

### `.row`

Horizontal layout intended for a main content area and a secondary column.

```html
<div class="row">
    <article>...</article>
    <aside>...</aside>
</div>
```

The first child grows as the main region. The last child uses `--col` as its secondary-column width.

### `.col`

Automatic responsive columns.

```html
<section class="col">
    <article class="pnl">...</article>
    <article class="pnl">...</article>
    <article class="pnl">...</article>
</section>
```

Columns are generated with `--col` as the minimum column width.

### `.mry`

CSS multi-column masonry layout.

```html
<section class="mry">
    <article class="pnl">...</article>
    <article class="pnl">...</article>
</section>
```

## Controls

### Button

```html
<button class="btn">Button</button>
<a class="btn" href="#">Link button</a>
```

### Input

```html
<input class="ipt" type="text">

<select class="ipt">
    <option>Option</option>
</select>

<textarea class="ipt"></textarea>
```

### Label + input

A `.lbl` immediately followed by `.ipt` is visually joined as one control.

```html
<label class="lbl" for="name">Name</label>
<input class="ipt" id="name" type="text">
```

### Switch

```html
<label>
    <span>Enabled</span>
    <input class="swi" type="checkbox">
</label>
```

### Dialog

```html
<dialog class="dlg">
    Modal content.
</dialog>
```

### Progress

```html
<progress class="prg" value="65" max="100">65%</progress>
```

### Code

```html
<code class="cod">const kcui = true;</code>
```

Block code:

```html
<pre><code class="cod">.pnl {
    display: flex;
}</code></pre>
```

## Fieldsets

A fieldset can use panel styling:

```html
<fieldset class="pnl">
    <legend>Form</legend>

    <section class="bdy">
        ...
    </section>

    <footer class="ftr">
        ...
    </footer>
</fieldset>
```

The legend acts as the fieldset header and uses the same spacing and header theme variables.

## Color utilities

Semantic color classes apply text, background, and border colors.

```html
<button class="btn prm">Primary</button>
<button class="btn sec">Secondary</button>
<button class="btn inf">Info</button>
<button class="btn scc">Success</button>
<button class="btn wrn">Warning</button>
<button class="btn dng">Danger</button>
```

Available utilities:

```text
.prm
.sec
.inf
.scc
.wrn
.dng
.wht
.blk
.sys
```

## Responsive behavior

The current stylesheet includes a breakpoint at `540px`.

At that width, the secondary child of `.row` can expand to the full available width.

## Demo

`demo.html` shows the current KCUI structure, including:

- application header and footer
- article + aside layout
- form controls
- switch
- dialog
- multi-panel column layout

---

## Beta Notice

This is a beta project tested only on Debian x86_64. It was created out of a personal need for these libraries, but no guarantees are provided regarding its stability or future support. You are free to test it, use it, and modify it as you please.

If you'd like to reach out, you can send an email to kaisar@kaisarcode.com. Please note that I do not accept pull requests; the goal is to avoid long-term dependency on platforms like GitHub, and I do not maintain fixed infrastructure to guarantee long-term stability for these projects.

---

## License

[![GPLv3](https://www.gnu.org/graphics/gplv3-127x51.png)](https://www.gnu.org/licenses/gpl-3.0.html)

This project is distributed under the **GNU General Public License version 3 (GPLv3)**.

*2026 KaisarCode*
