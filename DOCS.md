<!-- KxHTTP DOCS file -->
<!-- VER 1.0 -->

# KxHTTP <span class="text-orange">Docs</span>
<span class="badge bg-dark">v1.0</span>
<br>

## Installation

You can always download and install the latest binaries for your platform at
<a class="link-kxh" href="https://kxhttp.org/downloads">kxhttp.org/downloads</a>. If you want to build 
directly from the source, view the brief guide on how to do that 
<a class="link-kxh" href="https://github.com/kiduswb/kxhttp/blob/master/README.md" target="_blank">here</a>.

## Usage Guide

The general syntax for executing requests is:

`[HTTP_METHOD] [URL] [Options...]`

## HTTP Methods

KxHTTP has the following HTTP methods available for use:

**GET**

Retrieve data from a specified resource.

**POST**

Submit data to be processed to a specified resource.

**PUT**

Update a resource or create a new resource if it does not exist.

**DELETE**

Request the removal of a resource from the server.

**PATCH**

Apply partial modifications to a resource.

**HEAD**

Similar to GET but only requests the headers of a resource.

**OPTIONS**

Retrieve information about the communication options for the target resource.

## Options

**Query Parameters**

If you'd like to include URL parameters in your requests, simply include them in the URL
string. KxHTTP will automatically parse and send them. Here's an example:

`$kxh GET http://example.com/files.php?key=123&download=true`

**Headers**

You can send headers along with your request by utilizing the `-H` or `--header`
switches. You can also specify multiple headers by adding more than one `-H` or `--header` 
option on your request.

The syntax is:

`$ kxh [HTTP_METHOD] [URL] --headers "Header: someValue" -- headers "AnotherHeader: anotherValue"...`

*Example:*

```sh
$ kxh POST https://api.example.com/register \
--header "Authorization: Bearer YOUR_ACCESS_TOKEN" \
--header "Content-Type: application/json" \
--json "/json-files/userData.json"
```

**Authentication**

For basic authentication via a username and a password, you can use the `-a` or `--auth` option.
Here's an example:

```sh
$ kxh GET http://example.org/locked-resource --auth-basic "username:passwd"
```

You can use bearer token authentication, by using the `--auth-token` option as well. Here's an example:

```sh
$ kxh GET http://example.org/locked-resource --auth-token "[ACCESS_TOKEN_HERE]"
```

For users who want to use digest authentication, they can do so by using the `--auth-digest` option like this:

```sh
$ kxh GET http://example.org/locked-resource --auth-digest "username:passwd"
```

And last but not least, you utilize custom headers for authentication purposes.

**Forms and File Uploads**

To send form data to a server, you can simple utilize the `-f` or `--form` options. You can
add multiple form inputs by using multiple `-f` or `--form` options.

It's quick and easy:

```sh
$ kxh POST http://api.example.org/upload --form somefield=somevalue anotherfield=anothervalue ...
```

```sh
$ kxh POST http://api.example.org/upload --form "somefield=somevalue" \
--form "field2=value2"
```

To upload files, you can utilize the `--form-file` option. If you'd like to upload multiple files,
you can use this option multiple times. Here's an example:

```sh
$ kxh POST http://api.example.org/upload --form "photo_name=photoname.png" \
--form-file "file=/path/file.txt"
```

**JSON Data**

To send JSON data in the request body, you can utilize the `-j` or `--json` options.
Here's an example:

```sh
$ kxh POST http://example.com/api/endpoint -j '{\"key\": \"value\"}'
```

If you'd like to read from a JSON file instead, use the `--json-file` option:

```sh
$ kxh POST http://example.com/api/endpoint --json-file "path-to/file.json"
```

**Cookies**

To send cookies in a request, you can use the `--cookie` option followed by a cookie in the `"name=value"` format.
You can use multiple `--cookie` options.

**Output**

To save KxHTTP's output in a file, you can use the `-o` or `--output` option. Here's an example
to download a file:

```sh
$ kxh GET https://download.com/file.jpg -o "downloads/file.jpg"
```
