HTTP Client 0.1
===============

Author
------

André Ravazzi @ University of Tennessee, Knoxville
UTID: 000437123

What is it?
-----------

This is a simple HTTP/1.1 client based on RFC 2616[https://www.ietf.org/rfc/rfc2616.txt] developed
as an assignment of the subject COSC566 - Web Security. It supports
redirections and chunked data. It was developed in Java
version 1.8.0_71.

Usage
-----

Unzip or clone the repo and enter its directory

```
$   cd HTTPClient

$   make

$   java -jar HTTPClient.jar <METHOD> <URL>
```

Documentation
-------------

It is available as <METHOD> arguments:

  HEAD: make a GET request. It returns the header response
        of the request.

  GET: make a GET request. It returns the header plus
       the body of the request.

  POST: make a POST request to the server. The parameters
        must be written on the <URL>.

  PUT: make a PUT request. It returns the header with the
       server response.

  DELETE: make a DELETE request. It returns the header with the
       server response.

  TRACE: make a TRACE request. It returns the header with the
       server response plus the TRACE result.


If the request receives a 4xx or 5xx response, the application
will throw an exception as the body of the response (see example 1)

Examples
--------

Example 1

Request:

```
  $   java -jar HTTPClient.jar PUT http://sefcom.asu.edu/
```

Response:

```
  HTTP/1.1 403 Forbidden

  Date : Wed, 27 Jan 2016 04:15:53 GMT

  Server : Apache/2

  Content-Length : 387

  Keep-Alive : timeout=1, max=100

  Connection : Keep-Alive

  Content-Type : text/html; charset=iso-8859-1


  java.io.IOException: Server returned HTTP response code: 403 for
  URL: http://sefcom.asu.edu/
```

Example 2

Request:

```
  $   java -jar HTTPClient.jar TRACE http://utk.edu/
```

Response:

```
  HTTP/1.1 200 OK

  Date : Wed, 27 Jan 2016 04:18:41 GMT


  Server : Apache/2.2.27 (Unix) PHP/5.2.8 DAV/2 mod_ssl/2.2.27
  OpenSSL/0.9.8za

  Keep-Alive : timeout=5, max=100

  Connection : Keep-Alive

  Transfer-Encoding : chunked

  Content-Type : message/http


  TRACE / HTTP/1.1User-Agent: JavaHost:
  utk.eduAccept: text/html, image/gif, image/jpeg, *;
  q=.2, */*; q=.2Connection: keep-alive
```


Example 3

Request:

```
  $   java -jar HTTPClient.jar GET http://www.msftncsi.com/ncsi.txt
```

Response:

```
  HTTP/1.1 200 OK

  Content-Length : 14

  Date : Wed, 27 Jan 2016 04:21:35 GMT

  Connection : keep-alive

  Content-Type : text/plain

  Cache-Control : max-age=30, must-revalidate


  Microsoft NCSI
```

Github
------

The source code is also available at
https://github.com/amravazzi/HTTPClient

Fork me :)

License
-------

Project under The MIT License (MIT)

Read the LICENSE file for more information.
