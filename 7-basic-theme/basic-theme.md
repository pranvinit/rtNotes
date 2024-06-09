### Basic Theme Development

#### Types of Themes

1. **Parent Theme**: The main theme that contains all the required files and functionalities.
   **Notables**:

- It can have multiple child themes.
- It requires both `style.css` and `index.php` files.
- It can be a standalone theme.

2. **Child Theme**: A theme that inherits the styles and functionalities of a parent theme.
   **Notables**:

- It requires a `style.css` file.
- It can override the parent theme's styles and functionalities.
- It can have its own styles and functionalities.

#### Theme Files (Commonly Used)

1. **style.css**: Contains the theme's metadata and styles.
2. **functions.php**: Contains the theme's functions and hooks.
3. **index.php**: The main template file used as a fallback for other templates.
4. **header.php**: Contains the header section of the theme.
5. **footer.php**: Contains the footer section of the theme.
6. **sidebar.php**: Contains the sidebar section of the theme.
7. **single.php**: Contains the template for single posts.
8. **page.php**: Contains the template for single pages.
9. **archive.php**: Contains the template for archive pages.
10. **404.php**: Contains the template for 404 pages.
11. **search.php**: Contains the template for search results.
12. **comments.php**: Contains the template for comments.
13. **front-page.php**: Contains the template for the front page.
14. **home.php**: Contains the template for the blog page.

### Nav Menus and Widgets (Commonly Used Functions)

1. `register_nav_menus()`: Registers navigation menus.

   - `$locations`: An array of menu locations.

2. `has_nav_menu()`: Checks if a menu exists.

   - `$location`: The menu location.

3. `wp_nav_menu()`: Displays a navigation menu.

4. `register_sidebar()`: Registers a sidebar.

   - `$args`: An array of sidebar arguments.

5. `is_active_sidebar()`: Checks if a sidebar is active.

   - `$index`: The sidebar index.

6. `dynamic_sidebar()`: Displays a sidebar.
   - `$index`: The sidebar index.

### Block template syntax

#### Default blocks

```html
<!-- wp:paragraph -->
<p>This is a paragraph block.</p>
<!-- /wp:paragraph -->
```

#### Custom blocks

```html
<!-- wp:custom-block-name -->
<p>This is a custom block.</p>
<!-- /wp:custom-block-name -->
```

### Conditional Tags and Template Tags

#### Conditional Tags (Commonly Used)

1. `is_home()`: Checks if the current page is the blog page.
2. `is_front_page()`: Checks if the current page is the front page.
3. `is_page()`: Checks if the current page is a page.
4. `is_single()`: Checks if the current page is a single post.
5. `is_archive()`: Checks if the current page is an archive page.

#### Template Tags (Commonly Used)

1. `bloginfo()`: Displays information about the blog.
2. `the_title()`: Displays the post title.
3. `the_content()`: Displays the post content.
4. `the_excerpt()`: Displays the post excerpt.
5. `the_permalink()`: Displays the post permalink.
