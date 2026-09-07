# Native PHP themes

Use this mode when requested or already present. ACF is optional; do not install Timber for this mode.

Follow the [WordPress classic template hierarchy](https://developer.wordpress.org/themes/classic-themes/basics/template-hierarchy/). Keep a valid theme stylesheet header and index fallback. Add templates for requested content types rather than generating every possible template. Distinguish `front-page.php` from the posts index `home.php`.

Use the Loop, template tags, and `get_template_part()` with explicit arguments where supported. Keep shared setup/helpers in existing locations; avoid a monolithic functions file or a custom rendering framework. Restore global post state after secondary loops that modify it.

Register theme support and menus using appropriate hooks. Enqueue assets through WordPress with correct URLs, dependencies, and the existing versioning/build convention. Include `wp_head()`, `wp_body_open()`, and `wp_footer()`, language attributes, body classes, and normal content filtering.

Escape late by output context: HTML text, attributes, URLs, and allowed rich HTML require different handling. Translate interface strings using the theme text domain. Use attachment APIs for responsive media, and WordPress permalink/menu APIs instead of hardcoded local URLs or content IDs.

Use the shared Figma, ACF, and verification workflows as applicable. Preserve child-theme behavior if this is a child theme. Do not introduce block-theme templates or remove editor support solely because rendering uses PHP.
