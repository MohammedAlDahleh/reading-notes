## Things I want to know more about

* What is JSON Web Token?
- JSON Web Token (JWT) is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.

* What is the JSON Web Token structure?
- In its compact form, JSON Web Tokens consist of three parts separated by dots (.)
 1. Header
 2. Payload
 3. Signature

* Therefore, a JWT typically looks like the following.
 (xxxxx.yyyyy.zzzzz)

 - Header
 - The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.

  For example:
---
{
  "alg": "HS256",
  "typ": "JWT"
}
---
 - Payload
 Registered claims:  These are a set of predefined claims which are not mandatory but recommended.

 Public claims: These can be defined at will by those using JWTs. But to avoid collisions they should be defined in the IANA JSON Web Token Registry or be defined as a URI that contains a collision resistant namespace.

 Private claims: These are the custom claims created to share information between parties that agree on using them and are neither registered or public claims.

 * An example payload could be:
---
{
  "sub": "1234567890",
  "name": "John Doe",
  "admin": true
---

- Signature:

To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.

For example if you want to use the HMAC SHA256 algorithm, the signature will be created in the following way:

HMACSHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
  secret)

[JWTs Explained](https://www.youtube.com/watch?v=926mknSW9Lo)
[Intro to JWT](https://jwt.io/introduction/)
[Are JWTs Secure](https://stackoverflow.com/questions/27301557/if-you-can-decode-jwt-how-are-they-secure)

[npm jsonwebtoken docs](https://www.npmjs.com/package/jsonwebtoken)