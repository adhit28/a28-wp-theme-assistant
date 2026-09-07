# ACF content modeling

Default to structured fields attached to page templates. Preserve existing content definitions. Prefer native WordPress title/content/excerpt/media/menu data when suitable; do not duplicate it in custom fields without an editorial reason.

For each region decide: data owner, field name/type, return format, requiredness, editor instructions, and empty behavior. Use clear labels, stable keys, and location rules tied to the intended templates/entities. Avoid IDs that only work in one database. Hide optional empty sections intentionally while retaining valid values such as zero.

Use repeated fields only for actual editable lists; query posts for independently managed records. Check the installed ACF edition before using Repeater, Flexible Content, Gallery, options pages, or ACF Blocks. If unavailable, select a suitable supported/native model or explain the required dependency; do not silently simulate a paid feature with an elaborate workaround.

Version field definitions using the project's existing approach. For new projects prefer [ACF Local JSON](https://www.advancedcustomfields.com/resources/local-json/) in `acf-json`; it stores definitions, not content. Keep keys stable and inspect sync conflicts rather than overwriting them. Preserve existing load paths when adding custom paths. Check the project's editing versus read-only deployment workflow before expecting runtime writes. Existing PHP registration can remain authoritative; do not duplicate the same definitions in multiple competing sources.

Treat return format as a contract. Normalize image IDs/arrays, links, and relationship values before rendering; verify the installed Timber integration rather than guessing object conversion. Provide helpful field instructions and preview realistic missing/long values. Keep rich text sanitization distinct from plain text escaping.

If essential ACF support is missing, provide an actionable dependency notice through the project pattern; optional fields should not cause fatal calls. Do not report a successful editor workflow without testing an actual save and preview when authorized and available.

Custom form handlers require validation, sanitization, nonce checks and appropriate capability/ownership checks. A nonce alone is not authorization. Do not add frontend editing, content imports, or options pages without a task need.
