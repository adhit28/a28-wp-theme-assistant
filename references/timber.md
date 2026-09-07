# Timber and Twig

## Version and structure

Inspect Composer configuration and lockfiles first. Use Timber v2 for new projects subject to the actual PHP/WordPress compatibility requirements. Follow the project's autoloader/bootstrap; do not duplicate initialization. Confirm installation and API details in [Timber v2 documentation](https://timber.github.io/docs/v2/).

Use WordPress PHP hierarchy entrypoints to prepare context and select Twig views. Typical v2 APIs include `Timber::context()`, `Timber::get_post()`, `Timber::get_posts()`, and `Timber::render()`; verify signatures for the installed release. Do not introduce legacy `new Timber\Post()` or `new Timber\PostQuery()` recipes into v2 code.

Reuse the current views directory. For a new theme, a small base layout, shared partials, and page-specific views are sufficient. Avoid building a custom routing or view-model framework. Keep query preparation in PHP and presentation logic in Twig.

## Data and rendering

Respect the main query and pagination when rendering archives/search. Scope secondary queries and avoid fetching all posts to display a small subset. Normalize ACF image/link/relationship return formats at a clear boundary. Use documented Timber ACF integration where available; do not assume raw IDs are already image or post objects.

Consult the [Timber ACF integration](https://timber.github.io/docs/v2/integrations/advanced-custom-fields/) for formatted metadata and object conversion. Prefer `post.meta('field_name')` for ACF-aware metadata access where appropriate; check conversion behavior before manually wrapping a value. Avoid applying content formatting twice to already formatted WYSIWYG fields.

Use shared context hooks for genuinely global data, such as registered menus, without loading unrelated page data on every request. Account for absent menus and media. Build images with attachment metadata, useful alt text, intrinsic dimensions, and responsive sources; avoid unnecessarily lazy-loading the primary above-fold image.

Inspect actual Twig escaping configuration. Apply escaping for HTML text, attributes, URLs, and script data as appropriate; use WordPress URL validation/escaping where needed. Reserve raw markup for explicitly trusted or appropriately sanitized HTML, including intentionally filtered WordPress content. Do not blanket-apply `raw`, and do not double-escape safe rendered fragments indiscriminately.

Include WordPress head, body-open, and footer hooks in the shell using the documented project integration. Preserve body classes, language attributes, title support, content filters, and plugin assets.

## Dependencies and shipping

Handle missing autoloaders/Timber with the project's actionable dependency check before calling unavailable classes. Do not silently switch renderers. ACF dependency behavior must distinguish essential and optional fields. Check production build instructions: Composer vendor files and compiled assets must either be packaged or installed by the deployment pipeline. Do not assume the host runs Composer or Node.
