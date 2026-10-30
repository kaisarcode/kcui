# KCUI

**Minimal, composable CSS for semantic HTML**

KCUI is a compact CSS framework for building responsive pages with native HTML elements. It provides page layouts, panels, flexible regions, common controls, and semantic color variables. Applications can add independent modules, UI themes, and palettes without changing their markup.

The framework starts with structure rather than a predefined application design. It does not require a build process or JavaScript.

## Example

Load the core stylesheet and compose an ordinary page:

```html
<link rel="stylesheet" href="kcui.css">
```

```html
<div class="grl">
    <header class="hdr">
        <div class="wrp"><h1>My page</h1></div>
    </header>
    <main class="bdy">
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
```

The header and footer stay visible while the middle page region scrolls. The input shares the border and corners of its panel. Open [Getting started](doc/getting-started.md) for a complete standalone HTML page.

## Documentation

- [Getting started](doc/getting-started.md) - load KCUI and build a first page.
- [Layouts and panels](doc/layout.md) - compose the page regions, rows, grids, panels, and controls.
- [Themes and palettes](doc/theming.md) - customize appearance, modes, and semantic color variables.
- [Optional modules](modules/README.md) - use switches, tabs, drawers, and dialogs.
- [Design principles](doc/design.md) - understand KCUI's structural model and architectural boundaries.

The [interactive demo](demo.html) shows the same controls and modules with independent selectors for UI theme, color palette, and dark/light mode.

## Notice

KCUI is provided without guarantees of stability or future support. You may test, use, and modify it.

Questions can be sent to [kaisar@kaisarcode.com](mailto:kaisar@kaisarcode.com). Pull requests are not accepted; the project avoids depending on GitHub as long-term infrastructure.

## License

[![LGPLv3](https://www.gnu.org/graphics/lgplv3-147x51.png)](https://www.gnu.org/licenses/lgpl-3.0.html)

This project is distributed under the **GNU Lesser General Public License version 3 (LGPLv3)**.
