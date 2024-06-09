### WordPress Remote API

#### Functions

1. `wp_remote_get()`: Sends a GET request to a remote server.
   Example:

```php
$headers = array(
    'Authorization' => 'Bearer ' . $access_token,
);

$response = wp_remote_get( 'https://api.example.com/data', array(
    'headers' => $headers,
    'cookies' => $_COOKIE,
    'timeout' => 60, // Default is 5 seconds
) );
```

2. `wp_remote_post()`: Sends a POST request to a remote server.
   Example:

```php
$headers = array(
    'Authorization' => 'Bearer ' . $access_token,
    'Content-Type' => 'application/json',
);

$body = array(
    'key' => 'value',
);

$response = wp_remote_post( 'https://api.example.com/data', array(
    'headers' => $headers,
    'body' => json_encode( $body ),
    'cookies' => $_COOKIE,
    'timeout' => 60,
) );
```

3. `wp_remote_request()`: Sends a request to a remote server.
   Example:

```php
$response = wp_remote_request( 'https://api.example.com/data', array(
    'method' => 'GET',
    'timeout' => 60,
) );
```

### XML-RPC in WordPress

To make XML-RPC requests in using the wp_remote_get/post/request functions, you can use the 'Content-Type' header with the value 'application/xml'.

Example:

```php
$headers = array(
    'Authorization' => 'Bearer ' . $access_token,
    'Content-Type' => 'application/xml',
);

$response = wp_remote_post( 'https://api.example.com/xml-rpc', array(
    'headers' => $headers,
    'body' => $xml_data,
    'cookies' => $_COOKIE,
    'timeout' => 60,
) );
```

**Note**: Then we can process the XML response using the `simplexml_load_string()` function.

#### Commonly Used WordPress Remote API Functions

1. `wp_remote_retrieve_body()`: Retrieves the body of the response.
2. `wp_remote_retrieve_header()`: Retrieves a header from the response.
3. `wp_remote_retrieve_headers()`: Retrieves all headers from the response.

#### Commonly Used User Meta Data

1. User ID (meta key: ID)
2. Username (meta key: user_login)
3. Email address (meta key: user_email)
4. Role (meta key: wp_capabilities)
5. Authentication tokens or keys (for OAuth)
6. Last login time (custom meta key)

#### Intercepting HTTP Requests

To intercept HTTP requests and responses, you can use the `pre_http_request` http_request_args`and`http_response` filters.

Example:

```php

add_filter( 'pre_http_request', 'intercept_pre_http_request', 10, 3 );

function intercept_pre_http_request( $preempt, $request, $url ) {
    // Modify the request arguments here
    return $preempt;
}

add_filter( 'http_request_args', 'intercept_http_request', 10, 2 );

function intercept_http_request( $args, $url ) {
    // Modify the request arguments here
    return $args;
}

add_filter( 'http_response', 'intercept_http_response', 10, 3 );

function intercept_http_response( $response, $args, $url ) {
    // Modify the response here
    return $response;
}
```

**Note**: You can use the `pre_http_request` to implement site-wide transients or caching for remote requests.

#### WP Mail

To send emails in WordPress, you can use the `wp_mail()` function. It is a wrapper for the PHP `mail()` function.

#### Common hooks

1. `wp_mail_succeeded` - Fires after a successful email is sent.
2. `wp_mail_failed` - Fires after a failed email is sent.
