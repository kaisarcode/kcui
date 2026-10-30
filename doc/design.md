# Design principles

KCUI is a structural CSS foundation. Its purpose is to make common layouts and native controls composable without encoding the structure of a particular website or application.

## Structure before appearance

The document carries meaning through semantic HTML. KCUI adds a small vocabulary for layout: a page has regions, a row lays out direct children, a grid distributes cards, and a panel groups content with a common border.

KCUI does not need to identify a page as a dashboard, a storefront, a mobile app, or a blog. Those categories belong to the consuming project. A `.pnl` can contain a form, article, navigation, or another panel without changing its contract.

## Composition over special components

Instead of requiring a dedicated form-field component, KCUI composes a panel, label, and input from the existing `.pnl`, `.hdr`, and `.bdy` roles. The same regions also work for an article or a drawer.

Composition has a structural consequence: parent-child relationships matter. A `.row` distributes its direct children. The first, middle, and last children of `.grl` determine page behavior. Region classes belong on the elements that actually own those roles.

Moving a wrapper or attaching a class to a different level can change the layout even when the visible content remains identical.

## Optional features stay optional

A plain KCUI document needs only the core stylesheet. Tabs, switches, drawers, and dialog transitions are separate modules. Themes and palettes are separate layers again.

The core must remain understandable without requiring a specific module, theme, scripting library, or application runtime. Where interaction requires JavaScript, the consuming page provides it. CSS modules own presentation and CSS states, not application state machines.

This separation allows a project to adopt one capability without adopting the others.

## The browser remains responsible

Native HTML controls preserve keyboard behavior, form semantics, and browser capabilities. A button is normally a `button`, an input remains an `input`, and a modal dialog uses `dialog` when actual modal behavior is needed.

KCUI styles existing semantics rather than hiding them inside an invented component hierarchy. Alias classes are available for visual reuse, not as substitutes for choosing the appropriate element.

## Boundaries and tradeoffs

KCUI does not attempt to be a complete design system. It does not include a JavaScript component framework, an application router, centralized state, or a universal set of specialized input widgets.

It also does not guarantee that every layout is suitable for every product. A compact core gives consumers predictable primitives; a theme or application can then choose more specific typography, spacing, navigation, and responsive behavior.

The default appearance is dark-first, but color is deliberately expressed through semantic variables so independent palettes can provide other looks where useful.

## Next step

Use the [layout guide](layout.md) for concrete markup, or the [theming guide](theming.md) for the appearance layers.
