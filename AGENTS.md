# AGENTS.md

## Project Context

KCUI is a small, structural CSS framework.

Its purpose is to provide a compact, accessible, auditable base for ordinary web layouts without imposing a product theme or application architecture.

Read `README.md` for the effective interface and `DESIGN.md` for architectural boundaries before modifying the project.

## Required Mindset

Treat KCUI as a structural layer, not as a finished visual system.

Do not optimize it toward:

- enterprise dashboards;
- design-system completeness;
- application-specific navigation;
- sidebar state management;
- theme-specific behavior;
- component ecosystems;
- framework-style abstraction;
- generic extensibility;
- product-specific UX;
- speculative future layouts.

The user of KCUI is expected to customize appearance and higher-level behavior in separate theme or project CSS.

JavaScript behavior belongs to the consuming project unless it is essential to the structural contract of KCUI itself.

## Core Invariants

Preserve these properties unless the project owner explicitly instructs otherwise:

- HTML remains meaningful without KCUI;
- layout behavior remains understandable by inspecting the HTML and CSS;
- KCUI provides structure rather than product identity;
- the framework remains usable without JavaScript;
- the default structure degrades predictably on narrow screens;
- semantic HTML is preferred over framework-specific wrappers;
- layout utilities remain agnostic to element type and application role;
- themes may override appearance and advanced responsive behavior;
- project-specific features stay outside the core;
- the complete stylesheet remains small enough for one person to inspect.

## Structural Model

KCUI currently provides a small set of layout primitives.

### `.grl`

Three-part page structure.

Its direct children represent:

1. top region;
2. main region;
3. bottom region.

The middle region uses the remaining height and scrolls.

Do not make `.grl` depend on specific semantic classes such as `.hdr`, `.bdy`, or `.ftr`.

### `.row`

Horizontal flex layout.

Direct children share available space, may use column utilities, and wrap according to the core responsive behavior.

Under the base mobile breakpoint, direct children become full width.

Do not add sidebar-specific or application-specific behavior to `.row`.

### `.col`, `.col1` ... `.col12`

Proportional width utilities.

They express layout proportion only.

They must not assume that an element is:

- a sidebar;
- main content;
- navigation;
- a dashboard region;
- a widget;
- a card.

### `.wrp`

Width wrapper.

Its job is only to limit width with `--max` and center content.

Do not make other components depend on `.wrp` for their internal layout.

### `.grd`

Automatic equal-width grid.

It creates as many columns as fit using `--col` as the minimum track width.

Do not turn `.grd` into a fixed twelve-column grid.

Do not make `.colN` control grid track spans.

### `.mry`

Automatic multi-column flow.

It uses `--col` as the base column width and lets content flow vertically.

### `.hdr` and `.ftr`

Grid-based structural regions.

Their direct children are distributed evenly:

- one child: one full-width track;
- two children: two equal tracks;
- three children: three equal tracks;
- and so on.

The first child aligns to the start, the last child to the end, and intermediate children to the center.

This behavior must work with or without a nested `.wrp`.

Do not add responsive collapse rules to `.hdr` or `.ftr` in the core.

### `.pnl`, `.bdy`, controls, and utilities

These provide reusable structural styling and basic UI treatment.

Keep them generic and visually conservative.

## Accessibility and Auditability

KCUI should preserve useful document structure when styles or JavaScript are absent.

Prefer:

- semantic elements such as `header`, `main`, `article`, `section`, `aside`, `nav`, `footer`, `form`, and `fieldset`;
- natural source order;
- visible content over hidden state;
- layouts that remain understandable when reduced to a single column.

A default sidebar falling below main content on mobile is acceptable.

A theme may replace that behavior with a drawer, overlay, collapse control, sticky sidebar, or other UX.

Those behaviors are not part of the KCUI core.

## Theme Boundary

Themes and project CSS may define:

- colors;
- typography;
- radius and spacing adjustments;
- shadows;
- branding;
- navigation appearance;
- sidebar collapse behavior;
- overlays and drawers;
- sticky or fixed regions;
- animations;
- application-specific breakpoints;
- stateful interactions;
- product-specific component variants.

Do not add these to `kcui.css` merely because one demo or application needs them.

## Forbidden Default Recommendations

Do not recommend or implement these without explicit instruction:

- `.admin` layout classes;
- `.sidebar` behavior classes;
- dashboard-specific components;
- collapsible navigation;
- drawer systems;
- off-canvas panels;
- application shells;
- theme packs inside the core stylesheet;
- utility-class expansion for hypothetical needs;
- JavaScript dependencies;
- icon systems;
- CSS-in-JS integration;
- build-time CSS pipelines;
- component-framework adapters;
- enterprise design-system conventions.

Do not justify additions through enterprise readiness, ecosystem expectations, framework parity, or hypothetical future scale.

## Change Evaluation

Before changing KCUI, determine:

1. What concrete structural problem exists?
2. Does the problem appear in the current core behavior?
3. Could it be solved in HTML composition instead?
4. Does it belong in a theme or project stylesheet?
5. Does the change introduce a semantic assumption about the application?
6. Does it add a special case for one layout?
7. Can existing CSS be simplified instead?
8. Does the default remain accessible without JavaScript?
9. Does the resulting behavior remain easy to audit?
10. Would every KCUI user reasonably inherit this behavior?

Reject additions whose main purpose is to support one application.

Do not generalize a project-specific feature preemptively.

## Implementation Preferences

Prefer:

- direct CSS;
- short selectors;
- semantic HTML;
- a small number of structural classes;
- CSS custom properties for shared values;
- browser-native layout systems;
- responsive behavior derived from existing structure;
- deletion of obsolete rules;
- predictable defaults.

Avoid:

- selector magic tied to child count beyond established structural behavior;
- role-specific layout names;
- deeply nested selectors;
- duplicated layout systems;
- arbitrary breakpoint layers;
- hidden coupling between unrelated classes;
- framework-specific markup when semantic HTML is sufficient;
- abstractions whose only purpose is future flexibility.

## Responsive Behavior

The core responsive model must remain simple.

`.row` may collapse direct children to full width under the base breakpoint.

`.grd` adapts automatically through its minimum column width.

`.mry` adapts through its column width.

`.hdr` and `.ftr` remain equal-track grids and do not gain special mobile behavior in the core.

If a project needs different responsive behavior, override it in theme or project CSS.

## Documentation

Keep documentation operational and concise.

Use:

- `README.md` for public usage and examples;
- `DESIGN.md` for architecture, boundaries, invariants, and non-goals;
- `AGENTS.md` for implementation constraints and agent behavior.

Do not turn documentation into a product roadmap.

Do not describe missing application-level features as framework deficiencies.

## Completion Standard

A change is complete when:

- the concrete structural requirement is met;
- existing layouts still behave correctly;
- no application-specific semantics were introduced;
- accessibility and source-order behavior remain intact;
- the default remains useful without JavaScript;
- documentation matches actual behavior;
- obsolete rules are removed when replaced;
- no unrelated theme or enterprise machinery was added;
- the stylesheet remains small, direct, and auditable.

The goal is not to make KCUI capable of every interface pattern.

The goal is to provide a sharp structural base that users can theme and extend themselves.
