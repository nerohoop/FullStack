# Content

## Request Example
```
  GET /docs/index.html HTTP/1.1
  Host: www.nowhere123.com
  Accept: image/gif, image/jpeg, */*
  Accept-Language: en-us
  Accept-Encoding: gzip, deflate
  User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.1)
  (blank line)
  // Body
```

## Response Example
```
HTTP/1.1 200 OK
Date: Sun, 18 Oct 2009 08:56:53 GMT
Server: Apache/2.2.14 (Win32)
Last-Modified: Sat, 20 Nov 2004 07:16:26 GMT
ETag: "10000000565a5-2c-3e94b66c2e680"
Accept-Ranges: bytes
Content-Length: 44
Connection: close
Content-Type: text/html
X-Pad: avoid browser bug

<html><body><h1>It works!</h1></body></html>
```

## Verbs

## Response Headers

**Content-Length**
Must be contained in every response and tells the browser the size of the body in the reponse. This way the browser knows how many bytes it can expect to receive after the header section and can show you a meaningful progress bar when downloading a file

**Content-Type**
Non-optional and tells you what type the document has. This way the browser knows which parsing engine to spin up.

**Last-Modified**
When the document was last changed. It turned out that the Last-Modified date is not very reliable when trying to figure out if a document has been changed.

To accommodate this, most servers also send an ETag. ETag stand for entity tag, and is a unique identifier that changes solely depending on the content of the file. Most servers actually use a hash function to calculate the ETag.

**Cache-Control**
It allows the server to control how and for how long the client will cache the response.

**If-Modified-Since**
Permits the server to skip sending the actual content of the document if it hasn’t been changed since the date provided in that header.

## Default port
Port 80 is the default port for HTTP connections.

## Performance
Head-of-line Blocking

## Keep Alive

**Connection: keep-alive**

## Proxy

## HTTPS
HTTP + Transport Layer Security

Public Key
Private Key

Hashing + Encryption

Hashing function SHA

Certificate Authority Signatures

## TSL Handshake

## [Mixed Content](https://developer.mozilla.org/en-US/docs/Web/Security/Mixed_content)
