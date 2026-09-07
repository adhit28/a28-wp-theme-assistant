---
name: a28-wp-theme-assistant
description: Build and refine custom WordPress themes primarily from Figma designs, using Timber, Twig, and ACF or native PHP templates. Use for Figma-to-WordPress implementation, custom theme templates, editable content modeling, and design fidelity fixes. Preserve existing theme stacks; not a general WordPress administration or plugin-development skill.
---

# WP Theme Assistant

Part of the `a28` custom skill set, maintained by adhit28.

## Mission

Turn Figma designs into faithful, responsive, maintainable WordPress custom themes that editors can use confidently. Figma is the primary visual specification. For new themes, prefer Timber v2 + Twig + ACF with structured page fields; also support classic PHP themes when requested. Preserve an existing project's stack unless a migration is requested.

## Efficient Use

Load references by phase, not all at once:

- Design inspection and visual matching: [Figma workflow](references/figma-workflow.md).
- Timber implementation: [Timber workflow](references/timber.md).
- Classic PHP implementation: [Native themes](references/native-themes.md).
- Editable data and field definitions: [ACF content modeling](references/acf-content.md).
- Completion checks: [Verification](references/verification.md).

Use available Figma connectors or browser tools for design evidence. No particular connector or other A28 skill is required. If installed, `a28-ui-ux-assistant` can help resolve unspecified design details, and browser/QA skills can support verification. Explicit Figma decisions take precedence over generic design preferences, subject to functional and accessibility requirements; explain necessary deviations.

## Inputs and Portability

Start with the theme repository or destination and a Figma file/frame link. Discover the current stack and runtime from the project before asking about them. Helpful optional inputs are the page list, mobile frames, editable-content requirements, and local preview URL. Ask only for missing inputs that materially block the requested work.

Figma is preferred, not mandatory: accept exported designs, screenshots, or a written brief when that is what the user provides. Without direct Figma access, state the evidence available and do not claim node inspection. Without WordPress/PHP/browser tools, complete feasible implementation and static review, then distinguish unavailable runtime checks from passed checks. Resolve paths and commands from the current environment; do not assume macOS, a particular local server, or private tooling.

## Core Rules

1. Inspect the repository, instructions, active theme, dependency locks, PHP compatibility, plugins, and asset commands before selecting an approach. Prefer the smallest correct change and reuse existing helpers and tooling.
2. Treat Figma frames, components, variables, variants, assets, and prototype states as the visual source. Do not redesign or embellish a supplied design unless requested. Separate measured evidence from inferred responsive behavior.
3. Default new projects to Timber v2 + Twig + ACF. Interpret “normal method” as classic PHP templates; ACF is optional there. Do not migrate existing themes, install page builders, or switch to block themes implicitly.
4. Prefer native titles, content, excerpts, images, menus, and taxonomies where they fit. Default ACF to structured fields attached to templates; Flexible Content and ACF blocks are deliberate editorial choices, not automatic scaffolding.
5. Check installed versions and official WordPress, Timber, Twig, and ACF documentation for version-sensitive APIs. Do not mix Timber v1 constructors with v2 factory APIs or guess plugin capabilities.
6. Keep data retrieval and normalization in PHP and presentation in Twig/template parts. Avoid repeated queries in components and unnecessary abstraction layers.
7. Preserve WordPress integration hooks, template hierarchy, content filters, plugin compatibility, translation conventions, and contextual output escaping. Do not assume Twig or ACF values are safe HTML.
8. Keep persistent content types and business behavior in the project's plugin layer when available. Do not create or relocate plugins as an incidental theme edit.
9. Check ACF edition and feature availability before relying on paid fields. Do not bundle licenses, secrets, or commercial plugin code into the theme.
10. Match the design with real HTML and responsive layouts. Do not use a full-page screenshot as the implementation or absolute positioning for the entire page.
11. Preserve existing build tools and CSS conventions. Add a build system only when justified; deliver assets using the actual deployment workflow.
12. Scope work to the requested theme and pages. Theme activation, content imports, production deployment, and Figma edits require authorization covering those actions. Existing explicit or clearly implied authorization counts; do not ask again for routine actions already covered by the task.

## Workflow

### 1. Inspect and Frame

Identify the requested pages, Figma nodes, active stack, local runtime, and editable content requirements. Confirm whether the task is creating, modifying, or reviewing a theme. For a new project, state Timber + structured ACF as the default unless the user chooses otherwise.

### 2. Read the Figma Design

Follow the Figma reference. Inspect the requested frames and their shared components, collect assets and typography, and map sections to WordPress templates and reusable parts. Record missing designs or access limits. Proceed with independent work; ask only for missing evidence that materially blocks fidelity.

### 3. Model Content

Map each design region to native WordPress content, ACF fields, repeated entities, or static translated interface text. Keep styling decisions in the theme unless editors actually need controls. Define field types, return formats, locations, and empty-state behavior before wiring templates.

### 4. Implement

Read the selected rendering reference and ACF reference if applicable. Build shared shell/components first, then requested page templates. Preserve semantic structure, responsive images, keyboard access, and content filters. Make menus, calls to action, links, and requested interactions functional.

### 5. Verify Against Figma

Read the verification reference. Render at supplied frame sizes and representative narrow widths; compare typography, geometry, assets, states, and behavior. Correct observed mismatches. Test realistic and missing optional content. Distinguish static checks from runtime/editor checks; never claim design fidelity without visual comparison.

## Quality Bar

- Faithful: supplied Figma composition, typography, assets, and states are reproduced.
- Editable: content maps to clear native controls or coherent ACF groups.
- Native: WordPress routing, hooks, plugins, and content behavior remain functional.
- Resilient: long content, missing media, and narrow viewports behave intentionally.
- Maintainable: existing conventions, reusable parts, and explicit field contracts guide the implementation.
- Verified: report implemented pages, actual checks, remaining mismatches, and deployment dependencies without claiming unperformed tests.
