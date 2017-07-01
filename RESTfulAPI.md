# Content

* [Standardizing Errors and Status Codes](#standardizing-errors-and-status-codes)
* [Authentication](#authentication)

## Features

* Uses HTTP verbs to manage resources
* Can use any type of message format
* There must be no session state stored on the server side
* Session state must be handled entirely by the client

Why stateless?
Each request from client to server must contain all of the information necessary to understand the request, and cannot take advantage of any stored context on the server. Session state is therefore kept entirely on the client.

## Standardizing Errors and Status Codes

**401 for Unauthorized requests**
when a request requires authentication but it isn't provided.

**403 for Forbidden requests**
When a request my be valid but the user doesn't have permissions to perform the action

**404 for Not Found requests**
When a resource can't be found to fulfill the request

**422 for Validation Errors**
For validation errors that need to be sent back to the client, we'll use status code 422.

## Authentication

### Making authorized requests
If you are accessing protected resources that require authentication, every request must contain all necessary data to be properly authenticated/authorized.

The Authorization header field allows a user agent to authenticate itself with an origin server. Its value consists of credentials containing the authentication information of the user agent for the realm of the resource being requested.

Any time you're interacting with endpoints that require knowledge of the current user, you'll need to pass along an authorization header:
***Authorization: Token jwt.token.here***

## [cURL](https://www.ethanmick.com/getting-started-with-curl/)

```
// cURL makes requests to URL, by default, it makes an HTTP GET request
curl www.google.com
```

```
// Save response in file
curl -o google.html www.google.com
```

cURL is a great way for quickly testing JSON endpoint or what that API actually returns.

```
// Add auth header field
curl https://api.cloudmine.me/v1/app/928a78ffd73e4ff78383d1d4c06dd5a7/text \  
-H X-CloudMine-ApiKey:e90ef1aeaadd48de93b45038ed592a06 -i
```

```
  HTTP/1.1 200 OK  
  Date: Sat, 20 Dec 2014 17:31:10 GMT  
  Content-Type: application/json; charset=utf-8  
  Transfer-Encoding: chunked  
  Status: 200 OK  
  X-Request-Id: a9fbdaec-3b3c-4b11-92d8-5af2e9f01e8e  
  Cache-Control: max-age=0, private, must-revalidate  
  X-Runtime: 0.020247  
  X-Rack-Cache: miss  
  Access-Control-Allow-Origin: *  
  Access-Control-Expose-Headers: X-Request-Id

  {"success":{},"errors":{}}
```

```
// Create a post request
curl -X POST https://api.cloudmine.me/v1/app/928a78ffd73e4ff78383d1d4c06dd5a7/text \  
-d '{"myrandomkey":{"name":"ethan"}}' \
-H X-CloudMine-ApiKey:e90ef1aeaadd48de93b45038ed592a06 \
-H "content-type:application/json"
```
