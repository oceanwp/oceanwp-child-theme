# OceanWP Child Theme - Features Documentation

Complete documentation of all features available in OceanWP Child Theme.

---

## Table of Contents

1. [Theme Overview](#theme-overview)
2. [License & Availability](#license--availability)
3. [Parent Stylesheet Loading](#parent-stylesheet-loading)
4. [Customizing and Overriding the Parent](#customizing-and-overriding-the-parent)
5. [Renaming (White Labeling)](#renaming-white-labeling)
6. [Display & Developer API](#display--developer-api)

---

## Theme Overview

**OceanWP Child Theme** is a ready-to-use starter child theme for the OceanWP theme. It gives site owners a safe place for custom CSS, PHP and template changes that survive OceanWP updates.

| Property | Value |
|----------|-------|
| Version | 1.0 |
| Parent theme | `oceanwp` (`Template: oceanwp`) |
| Text Domain | `oceanwp` (declared in `functions.php`) |
| Main function | `oceanwp_child_enqueue_parent_style()` |
| Requires | OceanWP theme |
| Distribution | Free download from GitHub (github.com/oceanwp/oceanwp-child-theme), linked from the OceanWP readme |

### Key Capabilities

- Loads its own `style.css` after the OceanWP stylesheet
- Lets you override OceanWP functions and templates without editing the parent theme
- Can be renamed by editing the `style.css` header

---

## License & Availability

Free. There is no license key, no Freemius code and no premium version. The child theme declares no license of its own.

---

## Parent Stylesheet Loading

`functions.php` hooks `oceanwp_child_enqueue_parent_style()` to `wp_enqueue_scripts`. It enqueues the child `style.css` with:

| Property | Value |
|----------|-------|
| Handle | `child-style` |
| Dependency | `oceanwp-style` (the parent's main stylesheet), so child CSS loads after it |
| Version | The parent OceanWP version, read with `wp_get_theme( 'OceanWP' )`, so browsers refetch the file after a parent update |

The child `style.css` must not `@import` the parent stylesheet. OceanWP itself enqueues its CSS.

---

## Customizing and Overriding the Parent

| What | How |
|------|-----|
| CSS | Add rules to the child `style.css` |
| PHP functions | Define any OceanWP function that is wrapped in `function_exists()` in the child `functions.php`. WordPress loads the child `functions.php` before the parent's, so your version is used |
| Hooks | Add actions and filters (for example the `ocean_*` hooks) in the child `functions.php` |
| Templates | Copy a parent template file (for example from `partials/` or `woocommerce/`) into the same path in the child theme |

Customizer settings are stored per theme, so switching from OceanWP to the child theme starts with the child theme's own (empty) theme mods.

---

## Renaming (White Labeling)

Change "Theme Name" and the other fields at the top of `style.css`. Keep `Template: oceanwp`, or WordPress will not treat it as an OceanWP child theme. The zip file (`oceanwp-child-theme-master.zip`) can also be renamed.

Install by uploading the zip under **Appearance > Themes > Add New**, or by copying the folder into `wp-content/themes/`.

---

## Display & Developer API

The child theme adds no shortcodes, blocks, widgets, settings, admin pages, AJAX actions, REST routes or database entries.

| Hook | Callback | Description |
|------|----------|-------------|
| `wp_enqueue_scripts` | `oceanwp_child_enqueue_parent_style` | Enqueues the child stylesheet |

### Uninstall

Nothing is removed, and the child theme stores nothing of its own. Its theme mods stay in the database after it is deleted.

---

*OceanWP Child Theme - Starter child theme for customizing OceanWP safely*
