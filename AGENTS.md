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

Do not assume KCUI becomes more useful by accumulating components, variants, interaction patterns, or convenience abstractions.

Every addition becomes part of the structural base inherited by all users.

Prefer direct composition, project-local overrides, and deletion of obsolete code over expanding the core for hypothetical reuse.

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
- source order remains logical and accessible;
- native browser behavior is preferred when it already solves the problem;
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

Do not specialize `.grl` for public sites, admin interfaces, dashboards, or application shells.

### `.row`

Horizontal flex layout.

Direct children share available space, may use column utilities, and wrap according to the core responsive behavior.

Under the base mobile breakpoint, direct children become full width.

Do not add sidebar-specific or application-specific behavior to `.row`.

Do not add alternate row modes unless a concrete structural requirement cannot be expressed by the existing model.

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

Do not reinterpret `.colN` as Grid spans.

### `.wrp`

Width wrapper.

Its job is only to limit width with `--max` and center content.

Do not make other components depend on `.wrp` for their internal layout.

A component that works only when wrapped in `.wrp` is incorrectly coupled unless that dependency is explicitly part of its contract.

### `.grd`

Automatic equal-width grid.

It creates as many columns as fit using `--col` as the minimum track width.

Do not turn `.grd` into a fixed twelve-column grid.

Do not make `.colN` control Grid track spans.

Do not replace the automatic Grid model with Flexbox.

### `.mry`

Automatic multi-column flow.

It uses `--col` as the base column width and lets content flow vertically.

Keep `.mry` separate from `.row` and `.grd`; each layout model has a different purpose.

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

Do not require `.wrp` for header or footer distribution.

### `.pnl`, `.bdy`, controls, and utilities

These provide reusable structural styling and basic UI treatment.

Keep them generic and visually conservative.

Do not turn controls into application components.

## Accessibility and Auditability

KCUI should preserve useful document structure when styles or JavaScript are absent.

Prefer:

- semantic elements such as `header`, `main`, `article`, `section`, `aside`, `nav`, `footer`, `form`, and `fieldset`;
- native form controls;
- natural source order;
- visible content over hidden state;
- layouts that remain understandable when reduced to a single column;
- progressive enhancement over structural dependence on scripting.

A default sidebar falling below main content on mobile is acceptable.

A theme may replace that behavior with a drawer, overlay, collapse control, sticky sidebar, or other UX.

Those behaviors are not part of the KCUI core.

Do not change DOM order solely to obtain visual placement.

When visual order should differ from logical source order, prefer a CSS layout mechanism when that preserves accessibility.

Do not add ARIA where native HTML already provides the required semantics.

Do not hide required content merely to obtain a cleaner visual state.

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

A more sophisticated application UX is not automatically a core requirement.

The core should remain usable before any theme or project layer is applied.

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
- enterprise design-system conventions;
- component registries;
- state managers;
- application-specific layout abstractions;
- breakpoint systems based on device categories;
- wrapper layers added only for styling convenience.

Do not justify additions through enterprise readiness, ecosystem expectations, framework parity, product completeness, or hypothetical future scale.

## Change Evaluation

Before changing KCUI, determine:

1. What concrete structural problem exists?
2. Does the problem appear in the current core behavior?
3. Could it be solved in HTML composition instead?
4. Does it belong in an extra, theme, or project stylesheet?
5. Does the change introduce a semantic assumption about the application?
6. Does it add a special case for one layout?
7. Can existing CSS be simplified instead?
8. Does the default remain accessible without JavaScript?
9. Does the resulting behavior remain easy to audit?
10. Would every KCUI user reasonably inherit this behavior?

Reject additions whose main purpose is to support one application.

Do not generalize a project-specific feature preemptively.

Do not add an extension point without a concrete caller.

Do not add abstraction merely to remove a small amount of visible CSS.

## Editing Discipline

Treat the existing code as the primary source of truth.

Before proposing or applying a change:

1. Read the complete relevant block and its surrounding rules.
2. Identify which existing rule or element owns the behavior.
3. Determine whether the issue belongs to HTML structure, layout, presentation,
    responsive behavior, interaction, or accessibility.
4. Solve the problem at that layer.
5. Make the smallest change that fully resolves the concrete issue.
6. Verify that no unrelated established behavior was changed.

Do not redesign a component when a local CSS change is sufficient.

Do not rewrite working code merely because another form is more idiomatic.

Do not use a nearby problem as an opportunity for unrelated cleanup.

If an existing abstraction already expresses the required behavior, reuse it instead of introducing another abstraction.

When debugging CSS, inspect the existing cascade and layout behavior before adding rules.

In particular, consider:

- `display`;
- flex or Grid sizing;
- intrinsic sizing;
- `width`;
- `min-width`;
- `max-width`;
- alignment;
- wrapping;
- overflow;
- source order;
- specificity;
- cascade;
- inherited styles.

Prefer fixing the rule that owns the behavior over compensating elsewhere.

If the responsibility belongs to a parent layout, fix the parent rather than adding corrective rules to individual children.

## Change Scope

Keep changes tightly scoped to the request.

Do not:

- rename established classes unless explicitly requested;
- reorganize unrelated selectors;
- reformat unrelated CSS;
- reorder properties merely for style preference;
- add utilities for hypothetical reuse;
- add modifiers for a single concrete case;
- introduce a new layout system to solve one component;
- change HTML when CSS can correctly express the visual behavior;
- change source order merely to obtain visual ordering;
- add JavaScript for static layout behavior;
- add breakpoints before checking whether native layout can adapt naturally;
- refactor stable components while fixing an unrelated issue.

When replacing an existing rule, remove obsolete behavior instead of layering a second implementation over it.

Avoid parallel or duplicated rules that express the same component behavior.

A focused patch should remain focused.

## HTML Editing

Preserve semantic HTML and logical source order.

HTML structure should express document meaning and accessibility independently of presentation.

Prefer native semantics and controls over framework-specific markup.

Before changing markup, determine whether CSS can correctly express the required presentation.

Before adding a wrapper, determine whether an existing parent can own the required layout.

Before adding a class, determine whether the relationship can be expressed clearly through an existing structural class or a simple local selector.

Do not modify semantic source order solely to achieve visual placement.

Do not introduce application semantics into generic structural classes.

Do not add ARIA where native HTML already provides the required semantics.

Do not replace native controls with custom markup without a concrete requirement.

## CSS Editing

Prefer:

- direct CSS;
- short selectors;
- semantic HTML;
- a small number of structural classes;
- CSS custom properties for shared values;
- browser-native layout systems;
- responsive behavior derived from existing structure;
- deletion of obsolete rules;
- predictable defaults;
- changes localized to the rule that owns the behavior;
- preserving existing source and property ordering;
- native CSS behavior over additional abstractions;
- visual ordering that preserves logical DOM order.

Choose layout primitives according to the actual problem:

- use Flexbox for one-dimensional distribution and ordering;
- use Grid for track-based distribution;
- use normal flow when no layout system is necessary;
- use multi-column layout where vertical content flow is the intended model.

Do not select Grid or Flexbox merely for consistency with another component if the current problem has different requirements.

If a fix requires two declarations, do not design a new component.

If the responsibility belongs to the parent, do not compensate from the child.

Prefer natural browser behavior before explicit responsive rules.

Use CSS properties for their direct purpose.

For example, when visual ordering must differ from accessible source order inside a flex layout, prefer `order` over changing the DOM.

Keep selectors as narrow as necessary but no narrower.

A structural `:has()` selector is acceptable when it expresses a concrete local relationship already present in the markup.

Do not use `:has()` to infer application architecture or invent child-count-driven layout systems.

Do not add a new class when a simple relationship between existing classes clearly expresses the behavior.

Avoid:

- selector magic tied to child count beyond established structural behavior;
- role-specific layout names;
- deeply nested selectors;
- duplicated layout systems;
- arbitrary breakpoint layers;
- hidden coupling between unrelated classes;
- framework-specific markup when semantic HTML is sufficient;
- abstractions whose only purpose is future flexibility;
- unrelated cleanup during focused changes;
- rewriting working blocks for stylistic preference;
- compensating child rules for a parent-layout problem;
- JavaScript used to solve CSS layout;
- markup changes made only for visual positioning;
- multiple competing implementations of the same behavior.

## Responsive Behavior

The core responsive model must remain simple.

`.row` may collapse direct children to full width under the base breakpoint.

`.grd` adapts automatically through its minimum column width.

`.mry` adapts through its column width.

`.hdr` and `.ftr` remain equal-track grids and do not gain special mobile behavior in the core.

If a project needs different responsive behavior, override it in theme or project CSS.

Do not begin a responsive fix by adding a media query.

First inspect whether the existing layout can adapt through:

- flex wrapping;
- intrinsic sizing;
- percentage sizing;
- `min-width`;
- `max-width`;
- `minmax()`;
- `auto-fill`;
- `auto-fit`;
- normal Grid behavior;
- normal multi-column behavior;
- correct overflow handling.

Add or modify a breakpoint only when a concrete layout transition requires it.

Do not introduce device-category breakpoints or additional responsive modes without a demonstrated structural need.

## JavaScript Boundary

Do not use JavaScript to compensate for CSS layout problems.

JavaScript is appropriate for actual state and interaction.

Examples include:

- opening and closing interactive UI;
- persistent user state;
- dynamic application behavior;
- interaction that cannot be expressed by native HTML and CSS alone.

When adding optional interaction, preserve a usable HTML/CSS fallback whenever the feature permits it.

Do not make existing content dependent on JavaScript merely to achieve a more sophisticated presentation.

Do not add a JS abstraction when a direct local event handler is sufficient.

## Debugging

When something does not work:

1. Do not rewrite the component.
2. Identify the rule causing the behavior.
3. Inspect the existing cascade, inheritance, specificity, and computed layout.
4. Find the smallest conflicting rule first.
5. Change the minimum amount of code necessary.
6. Re-check the existing layout cases that rely on the same rule.

Do not fix several unrelated issues in one patch.

If another issue is important, identify it separately.

A bug in one layout primitive is not permission to redesign another primitive.

## Response and Patch Style

When asked for a change, be concrete.

If only a few declarations are required, provide only those declarations and their exact location.

If a block must be replaced, provide the complete replacement block.

If the user asks for the full block, provide the full block ready to paste.

Do not present multiple architectural alternatives by default.

Choose the smallest solution consistent with the existing design.

Explain the reason briefly and in terms of the current code.

Do not reopen settled architectural decisions unless the current code exposes a real contradiction.

Do not propose unrelated improvements while implementing a requested fix.

If an unrelated issue is important, mention it separately without including it in the patch.

Do not answer a small implementation question with a broad redesign.

Optimize in this order:

1. correctness;
2. preservation of existing behavior;
3. accessibility;
4. simplicity;
5. auditability;
6. compatibility with the existing code;
7. minimal change;
8. elegance.

## Documentation

Keep documentation operational and concise.

Use:

- `README.md` for public usage and examples;
- `DESIGN.md` for architecture, boundaries, invariants, and non-goals;
- `AGENTS.md` for implementation constraints and agent behavior.

Do not turn documentation into a product roadmap.

Do not describe missing application-level features as framework deficiencies.

Documentation must describe current behavior, not speculative future capabilities.

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
- the patch contains no unrelated cleanup;
- the stylesheet remains small, direct, and auditable.

The goal is not to make KCUI capable of every interface pattern.

The goal is to provide a sharp structural base that users can theme and extend themselves.

When in doubt, prefer the smaller change.
