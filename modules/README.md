# Optional modules

KCUI modules add presentation and interactive states without changing the core layout model. Load only the modules a page uses, after `kcui.css`. Each module consumes the core's semantic color and geometry variables.

```html
<link rel="stylesheet" href="kcui.css">
<link rel="stylesheet" href="modules/kcui-switch.css">
<link rel="stylesheet" href="modules/kcui-tabs.css">
```

The CSS modules do not provide JavaScript controllers. Native elements retain native behavior; tab selection and drawer state changes belong to the consuming page.

## Switch

`kcui-switch.css` presents a native checkbox or radio as a switch using `.swi`.

```html
<label>
    <span>Notifications</span>
    <input class="swi" type="checkbox" checked>
</label>
```

The label and switch align as one row. The switch takes its track and thumb colors from the active palette. The Mobile UI theme increases its dimensions while preserving the label's overall height. Radio switches still follow normal radio-group behavior.

## Tabs

`kcui-tabs.css` styles a group of buttons and related panels. The tablist is the first direct child of `.tabs`; the tabpanels follow it.

```html
<div class="tabs">
    <div role="tablist" aria-label="Examples">
        <button type="button" role="tab" id="tab-one"
            aria-controls="panel-one" aria-selected="true" tabindex="0">First</button>
        <button type="button" role="tab" id="tab-two"
            aria-controls="panel-two" aria-selected="false" tabindex="-1">Second</button>
    </div>
    <section class="pnl" role="tabpanel" id="panel-one" aria-labelledby="tab-one">
        <header class="hdr"><h2>First panel</h2></header>
        <div class="bdy">First content.</div>
    </section>
    <section class="pnl" role="tabpanel" id="panel-two" aria-labelledby="tab-two" hidden>
        <header class="hdr"><h2>Second panel</h2></header>
        <div class="bdy">Second content.</div>
    </section>
</div>
```

The selected tab has normal button dimensions. Inactive tabs are slightly lower; hovering or keyboard focusing one raises it to the selected tab's height without changing its color. The panels' upper corners are square where they meet the tabs.

The page must update `aria-selected`, `tabindex`, and the panels' `hidden` attributes when selection changes. For full keyboard tab behavior, handle arrow keys and Home/End as in [the demo](../demo.html). CSS alone does not manage selection or keyboard focus.

## Drawer

`kcui-drawer.css` moves a `.drw` element between open and closed positions using its `open` attribute. It can also be combined with `.pnl` for the standard bordered header, body, and footer.

```html
<aside id="drawer" class="drw pnl" aria-labelledby="drawer-title" inert>
    <header class="hdr"><h2 id="drawer-title">Drawer</h2></header>
    <div class="bdy">Drawer content.</div>
</aside>
<button type="button" id="toggle-drawer">Toggle drawer</button>
```

```js
const drawer = document.querySelector("#drawer");
const toggle = document.querySelector("#toggle-drawer");

toggle.addEventListener("click", () => {
    const open = !drawer.hasAttribute("open");
    drawer.toggleAttribute("open", open);
    drawer.inert = !open;
});
```

The drawer defaults to a fixed left-side position and `--drw-width: 20rem`. Configuration properties include `--drw-position`, `--drw-open`, `--drw-closed`, and the closed-width and clipping variables. When a drawer is a panel, the module clips the inner content to its rounded outer boundary.

The page owns state, focus management, and dismissal. A drawer is not automatically a modal. Use `dialog` when modal dialog semantics are required.

## Dialog

`kcui-dialog.css` adds visual open/closed transitions to the native `dialog` element. Native `showModal()` and `close()` own the modal lifecycle.

```html
<dialog id="message" class="dlg">
    <div class="pnl">
        <div class="bdy">
            <p>Message content.</p>
            <button type="button" id="close-message">Close</button>
        </div>
    </div>
</dialog>
<button type="button" id="open-message">Open dialog</button>
```

```js
const message = document.querySelector("#message");
document.querySelector("#open-message").addEventListener("click", () => message.showModal());
document.querySelector("#close-message").addEventListener("click", () => message.close());
```

The module uses the core palette for backdrop color and respects reduced-motion preferences. The `.dlg` class is a visual alias; the `dialog` element supplies actual dialog semantics.

## Further reading

- [Getting started](../doc/getting-started.md) explains how to load KCUI.
- [Layouts and panels](../doc/layout.md) explains the region contract used by modules.
- [Themes and palettes](../doc/theming.md) explains which variables modules consume.
