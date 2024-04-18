### FSE (Full Site Editing) and Multisite

#### Full Site Editing (FSE)
FSE has been introduced in WordPress 5.9 and it focuses on user editabiilty of the entire site using the block editor. It allows users to create and edit templates, template parts, and block patterns.


#### Components of FSE

1. **Site Editor**: It is a new interface that allows users to edit the entire site using the block editor.
**Notables**: You can access the Site Editor by going to `Appearance > Editor`.

2. **Customizer**: It is a tool that allows users to customize the site's appearance and settings.
**Notables**:
    - You can access the Customizer by going to `Appearance > Customize`.
    - Default Panels: Site Identity, Menus, Widgets, Homepage Settings, Additional CSS.
    - You can use the `add_panel()`, `add_section()`, `add_setting()`, and `add_control()` functions to add custom panels, sections, settings, and controls using the Customizer API.

3. **Blocks**: They are the basic building blocks of the block editor.
**Notables**:
    - Default Blocks types: Text blocks, Media blocks, Design blocks, Widgets blocks, Embed blocks.
    - You can register custom blocks using the `register_block_type()` function.

4. **Patterns**: They are predefined block layouts that can be used to create complex designs.
**Notables**:
    - You can access Patterns by going to `Appearance > Patterns`.
    - You can register custom patterns using the `register_block_pattern()` function.

5. **Templates**: They are predefined layouts that can be used to create pages and posts.
**Notables**:
    - You can access Templates by going to `Appearance > Templates`.
    - The `template-parts` folder contains reusable blocks that can be used in multiple templates.

6. **Block Themes**: They are themes that are built using blocks. They allow users to customize the site's appearance and settings using the block editor.
**Notables**:
    - There are 3 types of block themes: Block themes, Classic themes and hybrid themes.

#### Multisite

Multisite is a feature of WordPress that allows users to create a network of sites on a single WordPress installation (using the same core files). It allows users to create multiple sites with a single login.

#### Subdomains vs Subdirectories

1. **Subdomains**: They are separate sites that are created as subdomains of the main site.
**Example**: `site1.example.com`, `site2.example.com`.

2. **Subdirectories**: They are separate sites that are created as subdirectories of the main site.
**Example**: `example.com/site1`, `example.com/site2`.

#### Creating a Multisite Network

1. **Enable Multisite**: Add the following code to the `wp-config.php` file to enable Multisite:
```php
define( 'WP_ALLOW_MULTISITE', true );
```

2. **Install Multisite**: Go to `Tools > Network Setup` and follow the instructions to install Multisite.

3. **Configure Multisite**: Add the specified code to the `wp-config.php` and `.htaccess` files to configure Multisite.

4. **Create Sites**: Go to `My Sites > Network Admin > Sites` to create new sites in the network.

5. **Manage Sites**: You can manage sites, users, themes, and plugins from the Network Admin dashboard.

#### Administering a Multisite Network

1. **Super Admin**: The Super Admin has control over the entire network and can manage sites, users, themes, and plugins.

2. **Site Admin**: The Site Admin has control over an individual site in the network and can manage the site's content, settings, and users.

3. **User Roles**: Users can have different roles on the network, such as Super Admin, Administrator, Editor, Author, Contributor, and Subscriber.

4. **Themes and Plugins**: Themes and plugins can be network activated or activated on individual sites.

5. **Media Library**: The Media Library is shared across all sites in the network.