# KCUI

Minimal and responsive CSS framework distributed as a single `kcui.css` file.

![Screenshot](screenshot.png)

## Features

- Grail page layout
- Flexible rows and 12-column width utilities
- Automatic grid and masonry layouts
- Panels and reusable header/body/footer regions
- Form controls, switch, dialog, progress, and code styles
- Semantic color utilities
- CSS custom properties for theming

## Quick start

```html
<link rel="stylesheet" href="kcui.css">
```

```html
<div class="grl">
    <header class="hdr">
        <div class="wrp">Header</div>
    </header>

    <main class="bdy">
        <div class="wrp row">
            <article class="pnl col10">
                <header class="hdr">Article</header>
                <section class="bdy">Main content.</section>
            </article>

            <aside class="pnl col2">
                <header class="hdr">Aside</header>
                <section class="bdy">Aside content.</section>
            </aside>
        </div>
    </main>

    <footer class="ftr">
        <div class="wrp">Footer</div>
    </footer>
</div>
```

## Variables

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

Theme colors are also exposed as CSS custom properties, so the appearance can be changed without modifying the structural rules.

## Layout

### `.grl`

Three-part page layout. The first and last direct children stay in place while the middle child fills the remaining height and scrolls.

```html
<div class="grl">
    <header>...</header>
    <main>...</main>
    <footer>...</footer>
</div>
```

### `.row`

Flexible horizontal layout. Direct children share the available space and wrap when needed.

```html
<div class="row">
    <section>...</section>
    <section>...</section>
</div>
```

Below the responsive breakpoint, direct children become full width.

### `.col`, `.col1` ... `.col12`

Width utilities based on twelve proportional steps.

```html
<div class="row">
    <article class="col10">...</article>
    <aside class="col2">...</aside>
</div>
```

`.col` is equivalent to `.col1`. The utilities are layout-agnostic and can be used with any element.

### `.wrp`

Centers content and limits its width to `--max`.

```html
<div class="wrp">...</div>
```

### `.grd`

Automatic equal-width grid. The browser creates as many columns as fit, using `--col` as the minimum track width.

```html
<section class="grd">
    <article class="pnl">...</article>
    <article class="pnl">...</article>
    <article class="pnl">...</article>
</section>
```

### `.mry`

Automatic multi-column layout using `--col` as the base column width. Content flows vertically through the columns.

```html
<section class="mry">
    <article class="pnl">...</article>
    <article class="pnl">...</article>
    <article class="pnl">...</article>
</section>
```

## Regions and panels

`.hdr`, `.bdy`, and `.ftr` provide reusable regions with consistent spacing and theme colors.

```html
<section class="pnl">
    <header class="hdr">Header</header>
    <section class="bdy">Body</section>
    <footer class="ftr">Footer</footer>
</section>
```

A fieldset can also use panel styling:

```html
<fieldset class="pnl">
    <legend>Form</legend>
    <section class="bdy">...</section>
    <footer class="ftr">...</footer>
</fieldset>
```

## Controls

```html
<button class="btn">Button</button>

<label class="lbl" for="name">Name</label>
<input class="ipt" id="name" type="text">

<select class="ipt">
    <option>Option</option>
</select>

<textarea class="ipt"></textarea>

<label>
    <span>Enabled</span>
    <input class="swi" type="checkbox">
</label>

<dialog class="dlg">Modal content.</dialog>

<progress class="prg" value="65" max="100">65%</progress>

<code class="cod">const kcui = true;</code>
```

## Color utilities

Semantic color classes apply text, border, and background colors:

```text
.prm  Primary
.sec  Secondary
.inf  Info
.scc  Success
.wrn  Warning
.dng  Danger
.wht  White
.blk  Black
.sys  System
```

## Demo

`demo.html` contains examples of the current layout, panels, controls, grid, masonry, switch, and dialog.

## Beta Notice

This is a beta project tested only on Debian x86_64. It was created out of a personal need for these libraries, but no guarantees are provided regarding its stability or future support. You are free to test it, use it, and modify it as you please.

If you'd like to reach out, you can send an email to kaisar@kaisarcode.com. Please note that I do not accept pull requests; the goal is to avoid long-term dependency on platforms like GitHub, and I do not maintain fixed infrastructure to guarantee long-term stability for these projects.

## License

[![GPLv3](https://www.gnu.org/graphics/gplv3-127x51.png)](https://www.gnu.org/licenses/gpl-3.0.html)

This project is distributed under the **GNU General Public License version 3 (GPLv3)**.

*2025 KaisarCode*
