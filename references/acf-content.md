# ACF content modeling

Default to structured fields attached to page templates. Preserve existing content definitions. Prefer native WordPress title/content/excerpt/media/menu data when suitable; do not duplicate it in custom fields without an editorial reason.

For each region decide: data owner, field name/type, return format, requiredness, editor instructions, and empty behavior. Use clear labels, stable keys, and location rules tied to the intended templates/entities. Avoid IDs that only work in one database. Hide optional empty sections intentionally while retaining valid values such as zero.

Use repeated fields only for actual editable lists; query posts for independently managed records. Check the installed ACF edition before using Repeater, Flexible Content, Gallery, options pages, or ACF Blocks. If unavailable, select a suitable supported/native model or explain the required dependency; do not silently simulate a paid feature with an elaborate workaround.

Version field definitions using the project's existing approach. For new projects prefer [ACF Local JSON](https://www.advancedcustomfields.com/resources/local-json/) in `acf-json`; it stores definitions, not content. Keep keys stable and inspect sync conflicts rather than overwriting them. Preserve existing load paths when adding custom paths. Check the project's editing versus read-only deployment workflow before expecting runtime writes. Existing PHP registration can remain authoritative; do not duplicate the same definitions in multiple competing sources.

Treat return format as a contract. Normalize image IDs/arrays, links, and relationship values before rendering; verify the installed Timber integration rather than guessing object conversion. Provide helpful field instructions and preview realistic missing/long values. Keep rich text sanitization distinct from plain text escaping.

If essential ACF support is missing, provide an actionable dependency notice through the project pattern; optional fields should not cause fatal calls. Do not report a successful editor workflow without testing an actual save and preview when authorized and available.

## Editor layout and large field groups

Design the WordPress editing screen as a task-oriented form, not a dump of every frontend value. Order sections to match the rendered page and keep the most frequently edited fields easy to reach. For long template-driven pages, use ACF [Tabs](https://www.advancedcustomfields.com/resources/tab/) or [Accordions](https://www.advancedcustomfields.com/resources/accordion/) to divide sections; choose one navigation pattern per field group and close it with an endpoint when later fields must sit outside it. Do not add layout fields merely to decorate a short form.

Use field labels and instructions to explain editorial meaning rather than implementation names. For media, state its placement, recommended crop or aspect ratio, and whether a mobile override is optional. For links, state the expected destination and whether the title is rendered. Use the narrowest field type that matches the rendering contract; do not use a Link field if only a label is consumed. Use wrapper widths only to place short, related controls on one row, and confirm the layout remains usable in a narrow admin viewport.

Configure Repeaters for scanning and safe growth:

- Set a descriptive button label and a `collapsed` summary field such as a title, region name, or question.
- Use table layout for a few short uniform values; use row or block layout for media, rich copy, conditional controls, or nested structures.
- Set meaningful minimum and maximum rows when the design or business rule has a real limit. Do not cap an organically growing list solely because the current mockup shows a fixed sample.
- For a large top-level Repeater in ACF 6.0+, consider admin pagination and an appropriate rows-per-page value. Pagination reduces the rows rendered during editing, but does not change template or REST results. It is not supported for Repeaters nested in another Repeater or Flexible Content field, frontend forms, or ACF Blocks; do not rely on it in those contexts.
- Keep nested Repeaters for genuinely parent-owned subitems with small bounded counts. If nested items need independent editing, reuse, search, status, or permissions, model them as content records instead.

Use [conditional logic](https://www.advancedcustomfields.com/resources/conditional-logic/) to reveal genuine alternatives or optional overrides, not to conceal the form's basic structure. Keep the controlling field before the dependent fields, give the control a clear label, and check for contradictory rules. Conditional logic affects fields within the field group; field-group visibility remains the responsibility of location rules.

Define what an empty value means before implementation. If blank means “use the theme fallback,” editors cannot intentionally remove that value. For production editing, prefer one of these explicit contracts: seed the approved defaults into content once; add a clearly labeled “Use default” control; add a “Show this section” control; or treat blank as intentionally blank. Do not make demo or Figma fallback content silently reappear after an editor clears a saved value.

## Page-owned rows versus independently published content

Use an ACF Group or Repeater when the content exists only as part of one parent page and has no independent lifecycle. Good examples include a homepage logo strip, a small ordered statistic list, a page-specific image sequence, or hotel links owned by one destination. These rows inherit the parent Page's publish status, permissions, revision history, and URL.

Use native Posts, Pages, taxonomy terms, or a custom post type when an item needs one or more of the following:

- its own permalink, preview, draft/publish state, scheduling, author, revisions, or editorial permissions;
- reuse across multiple pages or channels without duplicating values;
- search, archives, pagination, feeds, taxonomy filtering, SEO metadata, or independent indexing;
- a growing catalogue that editors must locate and update independently;
- references from other records or integrations as a stable content entity.

Persistent public content types and their business behavior belong in the project's plugin layer when available, not only in a theme. Register only the capabilities, rewrite behavior, archives, REST exposure, and editor support the content actually needs; an internal reusable record does not automatically require a public archive or public queryability.

For a hybrid section, keep section-level presentation controls on the Page and source the items from independent records:

- Query records when the section should automatically show all or the latest matching published items.
- Use an ACF [Relationship field](https://www.advancedcustomfields.com/resources/relationship/) when editors need a curated subset, manual ordering, search, or taxonomy/post-type filtering.
- Use Post Object for a single selection or a simpler selector when its UX fits better.
- Filter selectable post types and statuses, set real minimum/maximum selections, and choose Post IDs or objects as an explicit return-format contract.
- Do not copy record titles, images, and descriptions into the parent Page merely to render the selected records; keep one authoritative owner for each value.

Use ACF [bidirectional relationships](https://www.advancedcustomfields.com/resources/bidirectional-relationships/) only when the reverse connection is itself needed for querying or editing. On supported ACF versions this is available for Relationship, Post Object, User, and Taxonomy fields. Treat it as a data-model decision, not a convenience toggle: target fields must be compatible, current native support only updates top-level targets, updates do not chain, and option pages or block contexts do not provide the same post/user/term identity behavior. A normal one-way relationship is sufficient when only the parent needs to know its selected items.

When replacing a Repeater with independent records, plan migration and ordering explicitly. Preserve stable IDs, publication state, relationships, and URLs; avoid creating duplicate live records during rollout. Verify both record editing and the parent Page's selection/query workflow before removing the old field data.

Custom form handlers require validation, sanitization, nonce checks and appropriate capability/ownership checks. A nonce alone is not authorization. Do not add frontend editing, content imports, or options pages without a task need.
