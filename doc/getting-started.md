# Getting started

KCUI styles ordinary HTML without a build step or a JavaScript framework. This guide creates a page with a fixed header and footer, scrollable content, a panel, and a labeled input.

## Load KCUI

Place `kcui.css` alongside your HTML file and load it in the document head:

```html
<link rel="stylesheet" href="kcui.css">
```

Use the relative path that matches where you store the stylesheet. No compilation, package manager, or JavaScript is required for this example.

## Create a page

Save this example as `index.html` next to `kcui.css`:

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <title>KCUI Example</title>
        <link rel="stylesheet" href="kcui.css">
    </head>
    <body>
        <div class="grl">
            <header class="hdr">
                <div class="wrp">
                    <h1>Example</h1>
                    <nav><a href="#content">Content</a></nav>
                </div>
            </header>
            <main class="bdy" id="content">
                <div class="wrp">
                    <article class="pnl">
                        <header class="hdr"><h2>Contact</h2></header>
                        <div class="bdy">
                            <div class="pnl">
                                <label class="hdr" for="name">Name</label>
                                <input class="bdy" id="name" type="text">
                            </div>
                        </div>
                    </article>
                </div>
            </main>
            <footer class="ftr">
                <div class="wrp">Footer</div>
            </footer>
        </div>
    </body>
</html>
```

Open `index.html` in a browser. The middle page region scrolls, while the first and last regions remain visible. The input shares the panel's outer border instead of drawing a second border.

The HTML elements retain their meaning without KCUI. The classes add layout and presentation.

## Add optional capabilities

Load an optional module after the core stylesheet:

```html
<link rel="stylesheet" href="kcui.css">
<link rel="stylesheet" href="modules/kcui-switch.css">
```

Then use the module on an ordinary checkbox:

```html
<label>
    <span>Notifications</span>
    <input class="swi" type="checkbox">
</label>
```

The checkbox remains a native form control. Other modules provide tabs, drawers, and dialog presentation. See the [module guide](../modules/README.md) for their markup and interaction requirements.

## Next step

Read [Layouts and panels](layout.md) to compose page regions, rows, grids, and controls.
