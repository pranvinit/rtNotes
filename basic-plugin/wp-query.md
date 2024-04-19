### WP Query in WordPress

In WordPress, the `WP_Query` class is used to query the database for posts. It allows you to retrieve posts based on various parameters such as post type, category, tag, author, date, and more.

#### Basic Usage

Here is an example of how to use `WP_Query` to retrieve posts:

```php
<?php
$args = array(
    'post_type' => 'post',
    'posts_per_page' => 5,
    'category_name' => 'news',
);

$query = new WP_Query($args);

if ($query->have_posts()) {
    while ($query->have_posts()) {
        $query->the_post();
        // Display post content
    }
}

wp_reset_postdata();
?>
```

#### Commonly Used Parameters

1. `post_type`: Specifies the post type to retrieve. Default is 'post'.
2. `post_status`: Specifies the post status to retrieve. Default is 'publish'.
3. `posts_per_page`: Specifies the number of posts to retrieve. Default is 10.
4. `paged`: Specifies the page number of the query.
5. `orderby`: Specifies the order in which posts should be retrieved.
6. `order`: Specifies the order of posts (ASC or DESC).
7. `post__in`: Specifies an array of post IDs to retrieve.

**Note**: You can also filter by category, tag, author, date, and more using additional parameters.

#### Commonly Used Properties and Methods of `WP_Query` results

1. `have_posts()`: Checks if there are posts available in the query.
2. `the_post()`: Sets up the current post in the loop (increments the post index).
3. `found_posts`: Returns the total number of posts found by the query.
4. `posts`: Returns an array of post objects.
5. `is_wp_error()`: Checks if the query result is a WP_Error object.

Example:

```php
$args = array(
    'post_type' => 'post',
    'post_status' => 'publish',
    'posts_per_page' => 5,
    'paged' => 1,
    'orderby' => 'date',
    'order' => 'DESC',
    'post__in' => array(1, 2, 3),
);
```

#### Taxonomy Query

You can also query posts based on taxonomy terms using the `tax_query` parameter. Here is an example:

```php
$args = array(
    'post_type' => 'post',
    'posts_per_page' => 5,
    'tax_query' => array(
        array(
            'taxonomy' => 'category',
            'field' => 'slug', // Can be 'term_id', 'name' or 'slug'.
            'terms' => array('news', 'events'), // Array of term slugs.
        ),
    ),
);
```

#### Meta Query

You can query posts based on custom field values using the `meta_query` parameter. Here is an example:

```php
$args = array(
    'post_type' => 'post',
    'posts_per_page' => 5,
    'meta_query' => array(
        'relation' => 'AND',
        array(
            'key' => 'featured',
            'value' => '1',
            'compare' => '=', // Can be '=', '!=', '>', '>=', '<', '<=', 'LIKE', 'NOT LIKE', 'IN', 'NOT IN', EXISTS', 'NOT EXISTS'
            'type' => 'NUMERIC', // Can be 'NUMERIC', 'BINARY', 'CHAR', 'DATE', 'DATETIME', 'DECIMAL', 'SIGNED'
        ),
        array(
            'key' => 'last_updated',
            'compare' => 'NOT EXISTS',
        )
    ),
);
```