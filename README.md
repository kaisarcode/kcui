# KCUI - Minimal and responsive CSS framework.

The framework is built around a small set of structural classes, common
components, color utilities, and responsive behavior. The current build
is distributed as a single lightweight `kcui.css`.

![Screenshot](screenshot.png)

## Features

- Minimal CSS structure
- Grail layout
- Horizontal row layout
- Column size utilities from `.col1` to `.col12`
- Header, body, and footer regions
- Panels
- Width wrapper
- Automatic grid
- Masonry columns
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

Basic layout structure:

```html
<div class="grl">
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

            <aside class="pnl col2">
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

The default theme also defines text, background, and border colors for system,
code, header, body, footer, panel, primary, secondary, info, success, warning,
danger, white, and black.

A new theme can be created by overriding these variables without changing the
structural rules.

## Layout

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

### `.grl`

Holy Grail layout container.

It fills the available height, keeps the first and last direct children in
place, and lets the middle child use the remaining space with its own
scrolling.

```html
<div class="grl">
    <header>...</header>
    <main>...</main>
    <footer>...</footer>
</div>
```

The three direct children do not need to use `.hdr`, `.bdy`, or `.ftr`. The
layout is based on their position inside `.grl`.

### `.row`

Horizontal layout for distributing direct children across the available width.

Direct children are flexible by default and share the available space.

```html
<div class="row">
    <section>...</section>
    <section>...</section>
    <section>...</section>
</div>
```

Column utilities can be applied to any direct child when a constrained width
is needed.

```html
<div class="row">
    <aside class="col2">...</aside>
    <article>...</article>
</div>
```

### `.wrp`

Width wrapper.

```html
<div class="wrp">...</div>
```

It uses `--max` as its maximum width and centers itself horizontally.

### `.col`, `.col1` ... `.col12`

Column size utilities based on `--col`.

`.col` and `.col1` represent one column. `.col2` through `.col12` represent
multiples of the base column size, including the gaps between columns.

Inside `.row`, column utilities constrain the width of an element.

```html
<div class="row">
    <aside class="col2">...</aside>
    <article>...</article>
</div>
```

They are agnostic to element type and semantic role. A column can be used for
a sidebar, content area, panel, navigation block, or any other direct child of
a `.row`.

```html
<div class="row">
    <section class="col3">...</section>
    <section>...</section>
    <section class="col2">...</section>
</div>
```

Inside `.grd`, the same utilities define how many grid tracks an element
spans.

```html
<div class="grd">
    <section>...</section>
    <section class="col2">...</section>
    <section>...</section>
</div>
```

Available sizes:

```text
.col
.col1
.col2
.col3
.col4
.col5
.col6
.col7
.col8
.col9
.col10
.col11
.col12
```

### `.grd`

Automatic responsive grid layout.

```html
<section class="grd">
    <article class="pnl">...</article>
    <article class="pnl">...</article>
    <article class="pnl">...</article>
</section>
```

Columns are generated automatically using `--col` as the minimum track width.

By default, each child occupies one grid track. Use `.col1` through `.col12`
to make individual children span multiple tracks.

```html
<section class="grd">
    <article class="pnl">...</article>
    <article class="pnl col2">...</article>
    <article class="pnl">...</article>
</section>
```

The number of available tracks depends on the width of the grid container, so
a column span is resolved within the current automatic grid.

### `.mry`

Multi-column masonry layout.

```html
<section class="mry">
    <article class="pnl">...</article>
    <article class="pnl">...</article>
    <article class="pnl">...</article>
</section>
```

Columns use `--col` as their base width, and children flow vertically according
to their content.

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

The legend acts as the fieldset header and uses the same spacing and header
theme variables.

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

`.row` distributes its direct children horizontally and can use `.col1` through
`.col12` to constrain individual elements.

`.grd` creates automatic columns according to the available width and `--col`,
and the same column utilities can be used to span multiple grid tracks.

`.mry` uses a multi-column flow and adapts vertically to the height of its
content.

## Demo

`demo.html` shows the current KCUI structure, including:

- Grail layout with header and footer
- Flexible row layout
- Column size utilities
- Automatic grid
- Masonry layout
- Panels
- Form controls
- Switch
- Dialog

---

## Beta Notice

This is a beta project tested only on Debian x86_64. It was created out
of a personal need for these libraries, but no guarantees are provided
regarding its stability or future support. You are free to test it, use
it, and modify it as you please.

If you'd like to reach out, you can send an email to kaisar@kaisarcode.com.
Please note that I do not accept pull requests; the goal is to avoid
long-term dependency on platforms like GitHub, and I do not maintain fixed
infrastructure to guarantee long-term stability for these projects.

---

## License

[![GPLv3](https://www.gnu.org/graphics/gplv3-127x51.png)](https://www.gnu.org/licenses/gpl-3.0.html)

This project is distributed under the **GNU General Public License version 3 (GPLv3)**.

*2025 KaisarCode*
