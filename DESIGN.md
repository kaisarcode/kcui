# KCUI Design

## Purpose

KCUI is a minimal CSS framework for structural web layout.

It provides a small set of primitives for:

- page structure;
- horizontal layout;
- proportional columns;
- automatic grids;
- masonry-style columns;
- panels and content regions;
- basic controls;
- semantic color hooks.

KCUI is intentionally not a complete visual design system.

Its job is to establish a predictable, accessible base that remains easy
to inspect and that can be customized by themes and project-specific styles.

## Design Principle

The framework should describe structure without describing the application.

A public website and an admin interface should be able to use the same KCUI
primitives while differing only in HTML composition and custom styling.

The framework must not need to know whether an element is:

- a sidebar;
- primary content;
- a dashboard;
- navigation;
- a widget;
- a product panel;
- a marketing section.

Those meanings belong to the document and the consuming project.

## Canonical HTML First

When HTML already provides the canonical element for a basic interface role,
KCUI should style that element directly.

A `button` should look like a KCUI button without requiring `.btn`. Normal
text inputs, `select`, and `textarea` should look correct without requiring
`.ipt`. `dialog` and `code` should receive their core treatment directly.

Classes such as `.btn`, `.ipt`, `.dlg`, and `.cod` remain useful
as reusable visual aliases, but they are not requirements for canonical elements.

KCUI should not add a class merely to restate what the HTML element already means.

## Composition Before Specialization

Before adding a new component class, prefer composing existing structural primitives.

For example, a labeled form field can be expressed as:

```html
<div class="pnl">
    <label class="hdr" for="name">Name</label>
    <input class="bdy" id="name" type="text">
</div>
```

This reuses `.pnl`, `.hdr`, and `.bdy` instead of introducing a dedicated
label/input pairing abstraction.

The same principle applies to optional components. A switch can use `.hdr`
for left/right distribution while its extra stylesheet only defines the switch appearance.

## Operating Model

KCUI is used as a base stylesheet.

The normal layering model is:

1. semantic HTML;
2. `kcui.css`;
3. optional extras;
4. optional project-specific CSS;
5. optional project JavaScript.

The lower layers must remain useful without the higher layers.

Removing optional extras should not destroy document structure.

Removing JavaScript should not make core content inaccessible.

## Structural Primitives

### Grail layout

`.grl` defines a three-part vertical page structure.

The first and last direct children keep their natural height.

The middle direct child fills the remaining space and scrolls.

The behavior is positional so the direct children do not need special KCUI role classes.

This permits the same structure to support conventional pages and administrative interfaces.

## Width Wrapper

`.wrp` limits content to `--max` and centers it.

It is optional.

A header or footer may contain a `.wrp` when constrained content width is
desired, or omit it when full-width content is desired.

No other component should require `.wrp` to function correctly.

## Horizontal Layout

`.row` is the generic horizontal flex layout.

Its direct children share available width and may be constrained with `.colN`.

The default responsive behavior allows the row to collapse into
full-width children under the base breakpoint.

This makes narrow-screen behavior predictable without requiring
application-specific logic.

A consuming theme may override that behavior.

## Column Utilities

`.col`, `.col1` through `.col12` express proportional width.

They are intentionally agnostic.

The same utility may size:

- an aside;
- an article;
- navigation;
- a panel;
- any other row child.

The core does not attach semantic meaning to column sizes.

## Automatic Grid

`.grd` is an automatic equal-width CSS Grid layout.

Its defining behavior is:

- columns are created automatically;
- `--col` is the minimum track width;
- remaining width is distributed equally;
- new rows appear naturally when more tracks no longer fit.

`.grd` is not a fixed twelve-column system.

Column utilities do not change grid spans.

This separation keeps the grid predictable and prevents proportional width
utilities from interfering with automatic track sizing.

## Masonry Columns

`.mry` uses CSS multi-column layout.

`--col` defines the base column width.

Content flows vertically according to its natural height.

The masonry model is separate from both `.row` and `.grd`.

## Header and Footer Regions

`.hdr` and `.ftr` are structural grid regions.

Their direct children are distributed across equal tracks.

For N children, the region creates N equal columns.

Alignment rules are:

- first child: start;
- last child: end;
- intermediate children: center.

With a single child, that child occupies the only full-width track.

This behavior must work whether the region contains its children directly
or contains one `.wrp` whose own children are distributed the same way.

There is no core responsive collapse behavior for `.hdr` or `.ftr`.

Inside a `.pnl`, header and footer borders act as separators between regions.
If a header or footer is the only child of the panel, no internal separator
is needed because the panel already provides the outer border.

## Panels and Body Regions

`.pnl` provides a generic bordered container.

`.hdr`, `.bdy`, and `.ftr` provide reusable internal regions.

These classes may be used at page level or inside panels.

They should remain visually conservative enough that themes can redefine
their appearance without fighting structural assumptions.

A control used as a direct `.bdy` region inside `.pnl` yields its own border
to the panel so the composition does not produce a doubled border.

## Core Controls

KCUI styles common canonical controls directly.

The core control model includes:

- buttons;
- normal text-like inputs;
- `select`;
- `textarea`;
- checkbox;
- radio;
- `dialog`;
- `code` and related inline code elements.

Visual alias classes remain available where reuse is useful.

Specialized controls such as file, range, color, and date/time inputs are
outside the core control model. They may remain native or be handled by
a theme, project stylesheet, or optional component.

## Extras

`extra/` contains optional extensions that build on KCUI without expanding
the structural contract of the core.

Extras may provide additional presentation, behavior, themes, components,
or other functionality outside the core.

Extras should build on existing KCUI structure where appropriate instead
of duplicating structural behavior already provided by the core.

The absence of extras must not make the underlying document structure
inaccessible or meaningless.

## Accessibility Model

KCUI should improve presentation without becoming necessary for document meaning.

A page should remain understandable when CSS is removed.

A page should remain navigable when optional JavaScript is removed.

The intended model relies on:

- semantic HTML;
- natural source order;
- visible content;
- predictable one-column fallback behavior;
- limited dependence on stateful UI.

For example, an admin sidebar may fall below the main content on mobile.

That behavior preserves content availability and source order.

A custom theme may later override it with a collapsible sidebar, drawer, or overlay.

## Theme Model

Themes own appearance.

They may redefine:

- colors;
- typography;
- border radius;
- spacing density;
- shadows;
- branding;
- visual hierarchy;
- control appearance;
- navigation presentation.

Themes may also implement higher-level layout behavior when the behavior
is specific to a product or visual system.

Examples include:

- collapsible sidebars;
- off-canvas navigation;
- sticky admin regions;
- overlay drawers;
- animated navigation;
- application-specific responsive transitions;
- specialized form controls.

These are not core KCUI concerns.

## Project CSS

Project styles own local behavior and exceptions.

If only one application needs a rule, that rule normally belongs in that application.

KCUI should not accumulate special cases merely because multiple HTML
structures can be imagined.

## JavaScript Boundary

KCUI does not require JavaScript for structural layout.

Stateful behavior such as:

- sidebar collapse;
- drawer state;
- persistent navigation state;
- modal orchestration beyond native behavior;
- application menus;
- dynamic layout switching;

belongs to the consuming project.

The structural HTML should still remain valid and usable if such behavior is unavailable.

## Responsive Philosophy

Responsive behavior should be minimal and predictable.

The core currently uses three different natural models:

- `.row` wraps and collapses direct children to full width at the base breakpoint;
- `.grd` adapts automatically from available width and `--col`;
- `.mry` adapts automatically from available width and `--col`.

`.hdr` and `.ftr` retain equal-track distribution and do not gain a separate mobile model.

More specialized responsive behavior belongs to themes or project CSS.

## Inspectability

KCUI should remain small enough that one person can read the stylesheet
and understand how a document is laid out.

The path from HTML to layout should remain direct.

New architecture must not obscure that path through:

- large utility taxonomies;
- generated class systems;
- framework adapters;
- role-specific layout abstractions;
- selector indirection;
- theme behavior embedded in the structural core.

## Non-Goals

KCUI is not intended to provide:

- an enterprise admin theme;
- a complete design system;
- a component framework;
- an application shell;
- a sidebar framework;
- a navigation framework;
- a drawer or overlay system;
- a JavaScript widget library;
- a utility-first CSS replacement;
- a theme marketplace;
- a build pipeline;
- runtime theming infrastructure;
- application state management;
- framework-specific adapters;
- styling for every specialized HTML control.

These omissions are intentional.

The expectation is that KCUI users will customize and extend the structural base.

## Change Criteria

A proposed core change should answer:

1. What structural problem exists in KCUI itself?
2. Is the problem shared by ordinary documents rather than one application?
3. Can HTML composition solve it without new CSS?
4. Does an existing canonical HTML element already express the role?
5. Can existing KCUI primitives compose the required structure?
6. Does the behavior belong in an extra or project stylesheet?
7. Does the change preserve semantic HTML?
8. Does it preserve usable behavior without JavaScript?
9. Does it keep layout roles agnostic?
10. Does it simplify or complicate the existing mental model?
11. Does every KCUI user reasonably benefit from inheriting it?
12. Can one person still audit the resulting stylesheet easily?

Changes justified mainly by enterprise completeness, framework parity,
application-specific UX, or hypothetical future requirements should be rejected.

## Core Invariants

The following properties define KCUI:

- structural rather than thematic;
- canonical HTML first;
- composition before specialization;
- semantic HTML first;
- accessible fallback behavior;
- no required JavaScript;
- agnostic layout utilities;
- optional extras and project overrides;
- predictable responsive defaults;
- automatic grid and masonry behavior;
- proportional row columns;
- wrapper-independent header and footer layout;
- no application-specific shell in the core;
- small, direct, auditable CSS.

KCUI should make common structures easy without deciding what the final product should look like.

That final layer belongs to the user.
