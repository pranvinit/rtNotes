### CPT, Meta Box, Shortcode, Settings API

### Custom Post Type (CPT)

To create a custom post type, use the `register_post_type()` function. The function accepts two parameters: the post type name and an array of arguments.

```php
<?php
function create_post_type() {
    register_post_type('book',
        array(
            'labels' => array(
                'name' => __('Books'),
                'singular_name' => __('Book')
            ),
            'public' => true,
            'has_archive' => true,
        )
    );
}

add_action('init', 'create_post_type');
?>
```

**Note**: We can use WP CLI scaffold command to create a custom post type. For example, `wp scaffold post-type book`

**Commonly Used Functions**:

1. `is_singular()`: It takes a post type name as an argument and returns true if the current post is of the specified post type.
2. `get_post_type()`: It returns the post type of the current post.

### Registering Custom Taxonomies

To register a custom taxonomy, use the `register_taxonomy()` function. The function accepts three parameters: the taxonomy name, the post type to which the taxonomy should be attached, and an array of arguments.

```php
<?php
function create_taxonomy() {
    register_taxonomy('genre', 'book',
        array(
            'label' => __('Genre'),
            'hierarchical' => true,
        )
    );
}

add_action('init', 'create_taxonomy');
?>
```

**Note**: We can use WP CLI scaffold command to create a custom taxonomy. For example, `wp scaffold taxonomy genre`

**Commonly Used Functions**:

1. `get_the_terms()`: It returns the terms of a specified taxonomy associated with the current post.
2. `wp_get_post_terms()`: It returns the terms of a specified taxonomy associated with a specified post.
3. `wp_get_object_terms()`: It returns the terms of a specified taxonomy associated with a specified post or term.

### Meta Box

To create a meta box, use the `add_meta_box()` function. The function accepts five parameters: the meta box ID, the title of the meta box, the callback function to display the meta box, the post type to which the meta box should be attached, and the context in which the meta box should be displayed.

```php
<?php
function add_book_meta_box() {
    add_meta_box(
        'book_meta_box',
        'Book Details',
        'display_book_meta_box',
        array('book', 'post'),
        'side',
        'high'
    );
}

add_action('add_meta_boxes', 'add_book_meta_box');

function display_book_meta_box($post) {
    // Display meta box content
}

?>
```

**Commonly Used Functions**:

1. `get_post_meta()`: It returns the value of a specified meta key for a specified post.
2. `add_post_meta()`: It adds a meta key and value to a specified post. If the meta key already exists (and the `$unique` parameter is set to false), it will add another entry in the database with the same name.
3. `update_post_meta()`: It updates the value of a specified meta key for a specified post. If the meta key does not exist, it will be added.
4. `delete_post_meta()`: It deletes the value of a specified meta key for a specified post.
5. `add_metadata

### Shortcode

To create a shortcode, use the `add_shortcode()` function. The function accepts two parameters: the shortcode name and the callback function to display the content of the shortcode.

```php
<?php
function book_shortcode($atts) {
    // Process shortcode attributes
    return 'Book shortcode content';
}

// This should be called on the init hook
add_shortcode('book', 'book_shortcode');
?>
```

**Commonly Used Functions**:

1. `shortcode_atts()`: It parses the shortcode attributes and merges them with default values.
   Example: `$atts = shortcode_atts(array('title' => 'Default Title'), $atts, <name>);`

2. `do_shortcode()`: It processes the content and replaces any shortcode tags with the appropriate callback function output.

### Settings API

The Settings API allows you to create settings pages for your plugin or theme. It provides functions to create settings sections, fields, and pages.

**Steps to Create a Settings Page**:

1. Register a settings page using `add_options_page()` or `add_menu_page()`.
   **Note**: `add_options_page()` is used for settings pages under the "Settings" menu, while `add_menu_page()` is used for top-level menu pages.
2. Add settings sections using `add_settings_section()`.
3. Add settings fields (to sections of settings) using `add_settings_field()`.
4. Save settings using `register_setting()`.

**Notables**:

1. `register_setting()` takes the option group name, the option name, and a callback function to sanitize the input. It adds the option to the database.
2. **Commonly Used Functions**:
   - `get_option()`: It retrieves the value of a specified option from the database.
   - `update_option()`: It updates the value of a specified option in the database.
   - `delete_option()`: It deletes a specified option from the database.
   - `do_settings_sections()`: It outputs the settings sections.
   - `do_settings_fields()`: It outputs the settings fields.
