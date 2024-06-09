### REST API and WP-CLI

#### REST API

**REST API Components**

1. **REST base URL**: `http://example.com/wp-json/`
2. **Namespace**: `wp/v2`
3. **Resource**: posts, pages, media, users, etc.
4. **Endpoint**: `http://example.com/wp-json/wp/v2/posts`
5. **Arguments**: Commonly used arguments are `per_page`, `page`, `search`, `orderby`, `order`, `status`, `slug`, `categories`, `tags`, etc.
6. **Global Parameters**: `_embed`, `_fields`, `_envelope`, `_jsonp`, `_format`, `_links` etc.
   **Notables**:
7. `_embed`: Embeds the data of the linked resources.
8. `_fields`: Limits the fields returned in the response.
9. `_envelope`: Sends the response along with the status code and headers.
10. `_jsonp`: Wraps the response in a callback function to support JSONP.
11. `_format`: Changes the response format to JSON or XML.
12. `_links`: Adds links to the response.

#### Commonly used hooks

1. `rest_api_init`: Fires when the REST API is initialized.
2. `rest_pre_serve_request`: Fires before the REST API serves a request.
3. `rest_pre_dispatch`: Used to Short-circuit the request. Fires before the REST API dispatches a request.
4. `rest_post_dispatch`: Fires after a REST API response is served.
5. `rest_url_prefix`: Filters the REST URL prefix (Default is `wp-json`).
6. `rest_authentication_errors`: Filters the authentication errors.

#### Commonly used functions

1. `register_rest_route()`: Registers a new REST API route.
2. `register_rest_field()`: Registers a new field for a REST API response.
3. `rest_do_request()`: Sends a request to the REST API.

#### Commonly used properties and methods (of Request and Response objects)

**Request Object**:

1. `get_param()`: Retrieves a parameter from the request (Both GET and POST).
2. `get_header()`: Retrieves a header from the request.
3. `get_body()`: Retrieves the request body.
4. `get_query_params()`: Retrieves the query parameters (Only GET parameters).
5. `get_json_params()`: Retrieves the json parameters (Only POST parameters).

**Response Object**:

1. `set_data()`: Sets the response data.
2. `set_status()`: Sets the response status.
3. `set_headers()`: Sets the response headers.

#### WP-CLI

#### Command Structure

```bash
wp <my_command> <req-pos-arg> [<optional-pos-arg>] --required-assoc-arg=<value> [--optional-assoc-arg=<value>]
```

**Notable**:

1. Optional arguments are enclosed in square brackets `[]`.
2. Required arguments are enclosed in angle brackets `<>`.
3. Associative arguments are preceded by `--`.

#### Commonly used commands

1. Command to create a user and update the user's password:

```bash
wp user create <user_login> <user_email> --role=<role>

wp user update <user_id> --user_pass=<password>
```

2. Command to install a plugin:

```bash
wp plugin install <plugin_name> --activate
```

3. Command to install a theme:

```bash
wp theme install <theme_name> --activate
```

4. Command to update WordPress core:

```bash
wp core update
```

5. Command to update WordPress core (to a specific version):

```bash
wp core update --version=<version>
```

#### WP-CLI format function

```bash
wp <my_command> --format=<format>
```

**Commonly used formats**:

1. `json`: Outputs the response in JSON format.
2. `yaml`: Outputs the response in YAML format.
3. `csv`: Outputs the response in CSV format.

#### WP-CLI doctor package

The doctor package diagnoses common problems in WordPress by running a series of checks.

```bash
wp doctor check
```

**Commonly used checks**:

1. `check-core-updates`: Checks for available core updates.
2. `check-plugin-updates`: Checks for available plugin updates.
3. `check-theme-updates`: Checks for available theme updates.

#### Additional information

1. **Type Juggling**: Type juggling is the automatic conversion of a value from one data type to another.
   Example:

```php
$x = "10"; // $x is a string
$y = 5;    // $y is an integer

$sum = $x + $y; // PHP implicitly converts $x from string to integer for addition
echo $sum;
```

**Note**: Unlike type casting, type juggling is done automatically by PHP.

2. **Compact (cruise) URLs**: Compact URLs are short URLs that redirect to a longer URL.
   Example:
   `http://example.com/wp-json/wp/v2/posts` can be shortened to `http://example.com/posts`.

**Note**: We can add compact URLs using custom rewrite rules in WordPress.
