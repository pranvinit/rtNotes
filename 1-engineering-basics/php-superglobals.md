### Superglobals in PHP

Superglobals are built-in variables in PHP that are always accessible, regardless of scope. They are used to access information about the server, request, and environment. 

### PHP Superglobals

1. **$GLOBALS**: It contains a reference to all variables which are currently defined in the global scope of the script.
**Notables**:
    - $GLOBALS does not include superglobals like $_POST, $_GET, $_FILES, $_COOKIE, $_SESSION, or $_SERVER.
    - Write / Read-Write access to the entire $GLOBALS array is not supported.

2. **$_SERVER**: It is an array containing information such as headers, paths, and script locations. The entries in this array are created by the web server.
**Notables**:
    - $_SERVER['PHP_SELF'] returns the filename of the currently executing script.
    - $_SERVER['SERVER_NAME'] returns the name of the server host under which the current script is executing.
    - $_SERVER['HTTP_USER_AGENT'] returns the user-agent of the current request.
    - $_SERVER['REMOTE_ADDR'] returns the IP address of the user from which the current request was made.
    - $_SERVER['REQUEST_METHOD'] returns the request method used to access the page (e.g., 'GET', 'POST', 'HEAD', 'PUT').
    - $_SERVER['HTTP_HOST'] returns the hostname of the client using DNS lookup.
    - $_SERVER['HTTP_REFERER'] returns the hostname part of the URL referring the current page.
    - 
**Note**: 'HTTP_HOST' and 'HTTP_REFERER' can be used interchangeably to get the hostname of the client.

3. **$_REQUEST**: It is an associative array of variables containing the contents of $_GET, $_POST, and $_COOKIE.

4. **$_POST**: It is an associative array of variables passed to the current script via the HTTP POST method.

5. **$_GET**: It is an associative array of variables passed to the current script via the URL parameters.

6. **$_FILES**: It is an associative array of items uploaded to the current scipt using multipart/form-data POST request.
**Notables**:
    - $_FILES['file']['name'] returns the original name of the uploaded file.
    - $_FILES['file']['type'] returns the MIME type of the uploaded file.
    - $_FILES['file']['size'] returns the size of the uploaded file in bytes.
  
7. **$_COOKIE**: It is an associative array of variables passed to the current script via HTTP Cookies.
**Notables**:
    - $_COOKIE['name'] returns the value of the cookie with the specified name.
    - $_COOKIE['name'] is used to set a cookie with the specified name and value.
**functions**:
    - setcookie('name', 'value', time() + 3600) sets a cookie with the specified name, value, and expiration time.
    - unset($_COOKIE['name']) deletes a cookie with the specified name.

8. **$_SESSION**: It is an associative array containing session variables available to the current script.
**Notables**:
    - $_SESSION['name'] returns the value of the session variable with the specified name.
    - $_SESSION['name'] is used to set a session variable with the specified name and value.

9. **$_ENV**: It is an associative array of variables passed to the current script via the environment method.
**Notables**:
    - $_ENV['name'] returns the value of the environment variable with the specified name.
    - $_ENV['name'] is used to set an environment variable with the specified name and value.
**functions**:
    - getenv('name') returns the value of the environment variable with the specified name.
    - putenv('name=value') sets an environment variable with the specified name and value.