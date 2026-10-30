# Layouts and panels

KCUI supplies a small set of independent structural classes. The relationship between elements, especially direct parent-child relationships, is part of the layout contract.

## Page regions

`.grl` is a three-part, vertical page layout. Its first and last direct children occupy their content height. The middle child consumes the remaining height and scrolls.

```html
<div class="grl">
    <header class="hdr">Header</header>
    <main class="bdy">Content</main>
    <footer class="ftr">Footer</footer>
</div>
```

The first, middle, and last positions control the behavior. The semantic element and region class describe what each part represents. Use `.wrp` inside regions when content should be centered and limited to `--max`.

## Choose a layout

Use `.row` for a horizontal, wrapping flex layout. Its direct children share available space; `.col1` through `.col12` express fractional widths based on twelve steps.

```html
<div class="row">
    <article class="col10">Main article</article>
    <aside class="col2">Related content</aside>
</div>
```

The `.col` alias means `.col1`. Width utilities are proportions, not grid-track spans. The base stylesheet makes direct row children full-width at its narrow-screen breakpoint.

Use `.grd` for an automatic grid of equal-width tracks:

```html
<section class="grd">
    <article class="pnl"><div class="bdy">First</div></article>
    <article class="pnl"><div class="bdy">Second</div></article>
</section>
```

The `--col` variable controls the minimum grid track width. The browser decides how many tracks fit.

Use `.mry` for multi-column flow when content should fill vertically from one column into the next. It also uses `--col`, but it does not create a grid.

## Panels and regions

A panel groups content under one border and corner radius. Its direct `.hdr`, `.bdy`, and `.ftr` regions provide consistent backgrounds, padding, and separators.

```html
<article class="pnl">
    <header class="hdr"><h2>Title</h2></header>
    <div class="bdy"><p>Content</p></div>
    <footer class="ftr">Actions</footer>
</article>
```

The panel clips its children to its outer rounded shape. It is also the boundary responsible for the border between this component and its surroundings.

`.hdr` and `.ftr` are reusable Grid regions, not classes reserved for HTML `header` and `footer`. Their direct children occupy equal tracks, with the first aligned to the start and the last to the end. `.bdy` supplies a scrollable content region.

Nested panels work without a second layout abstraction. Use an existing region's `.grd` or `.row` class to arrange their children where needed.

## Compose form fields

Native controls are styled directly. A labeled field can use the same panel and region model:

```html
<div class="pnl">
    <label class="hdr" for="name">Name</label>
    <input class="bdy" id="name" type="text">
</div>
```

A direct `input.bdy`, `select.bdy`, or `textarea.bdy` inside a panel has no independent border or corner rounding. The panel supplies the outer border and radius. Standalone controls retain their normal borders and radii.

A fieldset can also use `.pnl`, with its native `legend` followed by the body and, optionally, a footer:

```html
<fieldset class="pnl">
    <legend>Preferences</legend>
    <div class="bdy">
        <label for="color">Color</label>
        <input id="color" type="text">
    </div>
</fieldset>
```

Labels, legends, headings, buttons, header regions, and navigation use bold text by default. Links inside headings inherit the heading color; navigation links inherit their region color until hover or focus, when they use the palette's primary color.

## Controls and semantic colors

KCUI styles common buttons, inputs, selects, textareas, checkboxes, radio controls, and code elements. Visual aliases such as `.btn`, `.ipt`, and `.cod` let a different element reuse the corresponding presentation.

Semantic classes `.prm`, `.sec`, `.inf`, `.scc`, `.wrn`, `.dng`, `.wht`, `.blk`, and `.sys` set the related foreground, border, and background variables. Use them when the state has a concrete meaning, not as a replacement for the document's structure.

## Next step

Read [Themes and palettes](theming.md) to change appearance without changing the markup.
