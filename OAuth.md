## Cookie Based Authentication
![img](img/cookie-token-auth.png)

* Cookie based authentication is stateful.
* This means that an authentication record or session must be kept both server and client-side.
* The server needs to keep track of active sessions in a database,
* while on the front-end a cookie is created that holds a session identifier,

## Token Based Authentication
* Token-based authentication is stateless.
* The server does not keep a record of which users are logged in or which JWTs have been issued.
* Instead, every request to the server is accompanied by a token which the server uses to verify the authenticity of the request.
* The token is generally sent as an addition Authorization header in form of Bearer {JWT}
* But can additionally be sent in the body of a POST request or even as a query parameter.

## Advantages of Token-Based Authentication
* The back-end does not need to keep a record of tokens.
* The server's only job becomes to sign tokens on a successful login request and verify that incoming tokens are valid.
* Cookies work well with singular domains and sub-domains, but when it comes to managing cookies across different domains, it can get hairy.
* In contrast, a token-based approach with CORS enabled makes it trivial to expose APIs to different services and domains.
* JWT's on the other hand allow you to store any type of metadata, as long as it's valid JSON.
* When using the cookie based authentication, the back-end has to do a lookup, whether that be a traditional SQL database or a NoSQL alternative, and the roundtrip is likely to take longer compared to decoding a token.
* Native mobile platforms and cookies do not mix well.

## Where to Store Tokens?
Commonly, the JWT is placed in the browsers local storage and this works well for most use cases.
Unlike cookies, local storage is sandboxed to a specific domain and its data cannot be accessed by any other domain including sub-domains.

## Tokens Are Signed, Not Encrypted
A JSON Web Token is comprised of three parts: the header, payload, and signature.
The format of a JWT is header.payload.signature
Sensitive data, such as passwords, should never be stored in the payload.

[Guide](https://goo.gl/wCw22N)
