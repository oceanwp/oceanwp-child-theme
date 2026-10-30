# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

A starter child theme for the OceanWP parent theme (`Template: oceanwp` in `style.css`). It has no build step, no dependencies, no linting config and no tests. Users install it as a zip under Appearance > Themes or copy it to `wp-content/themes/`.

- `style.css` holds only the theme header. It must not `@import` the parent stylesheet.
- `functions.php` enqueues the child `style.css` as `child-style`, depending on the parent's `oceanwp-style` handle so it loads after it. The version string comes from the parent theme (`wp_get_theme( 'OceanWP' )`) for cache busting.
- WordPress loads the child `functions.php` before the parent's, so any parent function wrapped in `function_exists()` (most of the parent's `inc/helpers.php`) can be overridden by defining it here first.
- Renaming or whitelabeling is done by editing the `style.css` header (Theme Name and the rest). Keep `Template: oceanwp`.
