### Filters and Hooks

#### Commonly Used Filters

1. `the_content`: Filters the content of the post before it is displayed.
2. `excerpt_length`: Filters the length of the excerpt (Default is 55 words).
3. `show_admin_bar`: Filters the visibility of the admin bar.
4. `pre_update_option_{option_name}`: Filters the value of an option before it is saved to the database.
5. `body_class`: Filters the classes added to the body tag.

#### Commonly Used Actions

#### Plugin Development

1. **CPTs/Taxonomies Registration**: Use the `init` action to register custom post types.
2. **Enqueue Scripts and Styles on frontend**: Use the `wp_enqueue_scripts` action to enqueue scripts and styles on the frontend.
3. **Enqueue Scripts and Styles on admin**: Use the `admin_enqueue_scripts` action to enqueue scripts and styles in the admin area.
4. **Add Meta Boxes**: Use the `add_meta_boxes` action to add meta boxes to post edit screens.
5. **Add Shortcodes**: Use the `init` action to add shortcodes.
6. **Save Post Meta**: Use the `save_post` action to save post meta data.
8. **Customize the Admin Menu**: Use the `admin_menu` action to register settings for the admin menu.
9. **Add Settings Pages**: Use the `admin_init` action to add pages or subpages to the admin menu.
10. **Show Admin Notices**: Use the `admin_notices` action to display admin notices.
11. **Ajax Requests**: Use the `wp_ajax_{action}` and `wp_ajax_nopriv_{action}` actions for handling AJAX requests (action parameter comes form the `data.action` key in the AJAX request).
12. **Custom REST API Endpoints**: Use the `rest_api_init` action to add custom REST API endpoints.
13. **Rewrite Rules**: Use the `post_type_link` to replace placeholders in the permalink structure.
14. **CRON Schedules**: Use the `cron_schedules` filter to add custom CRON schedules.

#### Theme Development

1. **Theme Setup**: Use the `after_setup_theme` action to set up theme features.
2. **Widgets Registration**: Use the `widgets_init` action to register widgets.
3. **Customizer Settings**: Use the `customize_register` action to add customizer settings.
4. **Customizer Live Preview**: Use the `customize_preview_init` action to add customizer live preview scripts.

#### Order of initialization of common hooks

#### Order of execution of common hooks in Plugin Development

1. `muplugins_loaded`: Must-use plugins are loaded.
2. `plugins_loaded`: All plugins are loaded.
3. `init`: WordPress is initialized.
4. `wp_loaded`: WordPress is fully loaded.
5. `admin_menu`: Admin menu is created.
6. `admin_init`: Before any other admin screen.
7. `admin_enqueue_scripts`: Scripts and styles are enqueued in the admin area.
8. `add_meta_boxes`: Meta boxes are added.

#### Commonly Used Functions

1. `add_filter()`: Adds a filter to a specified hook.
2. `remove_filter()`: Removes a filter from a specified hook.
3. `apply_filters()`: Calls the functions added to a filter hook.
4. `add_action()`: Adds an action to a specified hook.
5. `remove_action()`: Removes an action from a specified hook.
6. `do_action()`: Executes functions hooked on a specific action hook.