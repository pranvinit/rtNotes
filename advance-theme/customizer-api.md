### Customizer API

The Customizer API allows you to add custom settings, controls, and sections to the WordPress Customizer. You can use the Customizer API to create a custom theme options panel, add custom settings for your theme, and preview changes in real-time.


#### Registering Custom Settings

To register custom settings in the Customizer, you can use the `add_setting()` method of the `WP_Customize_Manager` class. Here's an example of how to register a custom setting:

```php
function custom_theme_customizer_settings( $wp_customize ) {
    $wp_customize->add_setting( 'custom_setting', array(
        'default' => '#000000',
        'type' => 'theme_mod',
        'transport' => 'refresh',
    ) );
}
add_action( 'customize_register', 'custom_theme_customizer_settings' );
```
#### Important Parameters for `add_setting()`, `add_control()`, and `add_section()`

1. `add_setting()`:
    - `default`: The default value for the setting.
    - `type`: The type of setting (`theme_mod`, `option`, etc.).
    - `transport`: The transport method for the setting changes (`refresh`, `postMessage`, etc.).
    - `capability`: The capability required to edit the setting.
    - `sanitize_callback`: The callback function to sanitize the setting value.
    - `sanitize_js_callback`: The callback function to sanitize the setting value for JavaScript.

2. `add_control()`:
    - `type`: The type of control (`text`, `checkbox`, `radio`, etc.).
    - `label`: The label for the control.
    - `section`: The section to which the control belongs.
    - `settings`: The setting to control.
    - `priority`: The priority of the control.

3. `add_section()`:
    - `title`: The title of the section.
    - `priority`: The priority of the section.
    - `capability`: The capability required to view the section.
    - `description`: The description of the section.

### Control classes by WordPress

WordPress provides a set of control classes that you can use to create custom controls for the Customizer. Here are some commonly used control classes:

1. `WP_Customize_Color_Control`: A color picker control.
2. `WP_Customize_Image_Control`: An image upload control.
3. `WP_Customize_Media_Control`: A media library control.

### Refresh Mechanism

The `transport` parameter in the `add_setting()` method specifies how the setting changes are applied. The `refresh` transport method refreshes the page to apply the changes. You can also use the `postMessage` transport method to apply changes without refreshing the page.

### Live Preview (JS) example

```javascript
wp.customize( 'custom_setting', function( value ) {
    value.bind( function( newval ) {
        $( '#element-id' ).css( 'color', newval );
    } );
} );
```