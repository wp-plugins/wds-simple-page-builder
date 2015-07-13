=== WDS Simple Page Builder ===
Contributors: jazzs3quence, webdevstudios
Tags: page builder, template parts, theme
Requires at least: 3.0
Tested up to: 4.2.2
Stable tag: 1.4.2

Uses existing template parts in the currently-active theme to build a customized page with rearrangeable elements.

== Description ==

Uses existing template parts in the theme to dynamically build a custom page layout, *per page*. An options page allows you to define your template part directory (if you wanted to keep these template parts separate from other template parts) and the template part prefix you are using.

[Check out the wiki for full documentation!](https://github.com/WebDevStudios/WDS-Simple-Page-Builder/wiki)

= Usage =

To use this plugin, your theme template files must have the following `do_action` wherever you want the template parts to load:

`<?php do_action( 'wds_page_builder_load_parts' ); ?>`

This will take care of loading the correct template parts in the order you specified. You can also specify a specific saved layout by passing the layout name to the `do_action` as a second parameter, like this:

`<?php do_action( 'wds_page_builder_load_parts', 'my-saved-layout' ); ?>`

**Note:** With saved layouts, the name you pass to the do_action must match *exactly* the way it is saved on the options page. So, if your layout was instead named "my saved layout", you would need to pass it to the `do_action` with the spaces intact.

= Page vs Global Parts vs Saved Layouts =

The page builder will, by default, use the template parts that were set on the page when you set them on the Edit page screen. However, if no template parts were defined on the individual page, you can also set Global Template Parts that will load on all pages that don't have their own, individual template parts defined.

You can leave the Global setting to "- No Template Parts -" to not define any global template parts if individual page-specific template parts weren't set.

Saved layouts are used when there is no layout set for that page (or post) with Global layouts used as a generic fallback. You can set a saved layout to be the default layout for all posts of a type *or* you can call them specifically when you add the `do_action` to your theme template files.

== Installation ==

1. Upload the `wds-simple-page-builder` directory to the \`/wp-content/plugins/\` directory or install via the Plugin Installer
1. Activate the plugin through the 'Plugins' menu in WordPress
1. Place `<?php do_action( 'wds_page_builder_load_parts' ); ?>` in your templates

== Frequently Asked Questions ==

**How do I use this thing?**
[Check out our Wiki!](https://github.com/WebDevStudios/WDS-Simple-Page-Builder/wiki)

**Why is there an empty "- No Template Parts -" (or multiple) template in the saved layouts after I save the options?**
It's a [CMB2](https://wordpress.org/plugins/CMB2)-related bug in having a repeatable field within a repeatable group. It will be fixed. [Follow the issue on Github](https://github.com/WebDevStudios/WDS-Simple-Page-Builder/issues/5)

**I can't remove a saved layout after I've created one.**
Another [CMB2](https://wordpress.org/plugins/CMB2) issue which will also be fixed soon. [Follow *this* issue on Github](https://github.com/WebDevStudios/WDS-Simple-Page-Builder/issues/3)


== Screenshots ==

1. Dynamically add template parts within the Edit Page screen and reorder those components.
2. The results are saved to post meta on the page and visible as soon as you save the page.
3. Options page

== Changelog ==

= 1.4.2 =
* added `saved_page_builder_layout_exists` function

= 1.4.1 =
* fixed empty templates showing up after options save in Saved Layouts ([fixes #5](https://github.com/WebDevStudios/WDS-Simple-Page-Builder/issues/5))

= 1.4 =
* added actions and filters for plugin developers to hook into. See [Hooks documentation](https://github.com/WebDevStudios/WDS-Simple-Page-Builder/wiki/Hooks)
* removed some unused functions
* deprecated `wds_template_part_prefix` and `wds_template_parts_dir` and replaced them with `wds_page_builder_template_part_prefix` and `wds_page_builder_template_parts_dir`, respectively
* added `unregister_page_builder_layout` to unregister a single registered layout (or all of them if `'all'` is passed)

= 1.3 =
* added new template tags -- `wds_page_builder_load_parts` for loading an array of specific template parts and `wds_page_builder_load_part` for loading a single template part
* added new feature to programmatically register a new layout

= 1.2 =
* added saved layouts feature. Now you can save layouts and set those saved layouts as the defaults for post types. Or you can define a specific layout in the `do_action`, e.g. `do_action( 'wds_page_builder_load_parts', 'my named layout' )`
* added a check for the existence of a template part before loading it -- prevents accidental blowing up of the page if parts are changed and not found

= 1.1 =
* added post type support beyond just pages. Options page now allows you to check which post types you want to use the page builder on, and the page builder metabox will appear on the Add New/Edit page for those post types.

= 1.0.1 =
* switched to using get_queried_object instead of get_the_ID to get a post id when checking the existence of post meta for cases when a loop is not being used or the action is fired outside the loop.

= 1.0.0 =
* Initial release

== Upgrade Notice ==

