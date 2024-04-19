### Networking in PHP

#### XML Parser Functions

**SimpleXML**: Loads an XML file into an object.

```php
<?php
$xml = simplexml_load_file("note.xml") or die("Error: Cannot create object");
echo $xml->to . "<br>";
echo $xml->from . "<br>";
echo $xml->heading . "<br>";
echo $xml->body;
?>
```
**Note**: `simplexml_load_string()` is yet another function that can be used to load an XML string.

### DNS and SSL

**DNS**: Domain Name System (DNS) is a hierarchical and decentralized naming system for computers, services, or other resources connected to the Internet or a private network.

**Parts of a URL**: http://rtcamp.example.com:80/path/to/file.html

- **http**: Protocol
- **rtcamp**: Subdomain
- **example**: Domain
- **com**: Top-level domain
- **80**: Port
- **path/to/file.html**: Path
- **http://rtcamp.example.com**: Host

**SSL**: Secure Sockets Layer (SSL) is a standard security protocol for establishing encrypted links between a web server and a browser in an online communication.

**How SSL Works**:
1. A browser requests a secure page (https://).
2. The web server sends its public key with its certificate.
3. The browser checks the certificate root against a list of trusted CAs.
4. The browser checks if the certificate is expired, has a matching hostname, and is used for the correct purpose.
5. The browser then uses the public key to encrypt a random symmetric encryption key and sends it to the server with the encrypted URL required as well as other encrypted HTTP data.
6. The web server decrypts the symmetric encryption key using its private key and uses the symmetric key to decrypt the URL and HTTP data.
7. The web server sends back the requested HTML document and HTTP data encrypted with the symmetric key.
8. The browser decrypts the HTTP data and HTML document using the symmetric key and displays the information.
9. The symmetric key is discarded.
10. If the browser requests another secure page, the process is repeated. If the symmetric key is intercepted, the data is secure.

**Gist**: SSL uses public-private key pair to encrypt and decrypt symmetric key sent by the browser, which is then used to encrypt and decrypt the data.

### cURL

**cURL**: cURL is a command-line tool that can be used to test APIs and web services.

**cURL Options**:
- **X**: Specifies a proxy server through which the request should be routed
- **H**: Specifies an extra header to include in the request when sending HTTP to a server.
- **d**: Sends the specified data in a POST request to the HTTP server.
- **u**: Specifies the user name and password to use for server authentication.
- **k**: Allows cURL to perform "insecure" SSL connections and transfers.

**Example**:
```bash
curl -X POST -H "Content-Type: application/json" -d '{"key": "value"}' https://example.com -u username:password -k
```