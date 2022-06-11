## Things I want to know more about

<h1>Securing Passwords</h1>

* The benefit of hashing is that if someone steals the database with hashed passwords, they only make off with the hashes and not the actual plaintext passwords. But why do we always hear about passwords being cracked? There are some weaknesses in cryptographic hash algorithm that allows an attacker to calculate the original value of a hashed password, as explained below:

* PROBLEMS WITH CRYPTOGRAPHIC HASH ALGORITHM
Brute Force attack: Hashes can't be reversed, so instead of reversing the hash of the password, an attacker can simply keep trying different inputs until he does not find the right now that generates the same hash value, called brute force attack

* General-purpose hash function designed for speed,because they are often used to calculate checksum values for large data sets and files, to check for data integrity. Using a modern computer one can crack a 16 Character Strong password in less than an hour, thanks to GPU.

* Hash Collision attack: Hash functions have infinite input length and a predefined output length, so there is inevitably going to be the possibility of two different inputs that produce the same output hash. MD5, SHA1, SHA2 are vulnerable to Hash Collision Attack i.e. two input strings of a hash function that produce the same hash result.

* BCrypt, IT's SLOW AND STRONG AS HELL

* To overcome such issues, we need algorithms which can make the brute force attacks slower and minimize the impact. Such algorithms are PBKDF2 and BCrypt, both of these algorithms use a technique called Key Stretching.

* This work factor value determines how slow the hash function will be, means different work factor will generate different hash values in different time span, which makes it extremely resistant to brute force attacks. When computers become faster next year we can increase the work factor to balance it out i.e. to make the attack slower.

* This hashing algorithm is implemented in a number programming languages like PHP, Java, Ruby, C#, C etc. If you are a PHP developer, you can simply use the crypt() function with a Blowfish required salt.
---
<?php
// Generate a password using a random salt
password_hash($password, PASSWORD_BCRYPT);
// Generate a password with a known salt
password_hash($password, PASSWORD_BCRYPT, array("salt" => $salt));
// This will cause crypt to generate a bcrypt hash
$salt = '$2y$10$' . mcrypt_create_iv(22);
$salted_password = crypt($password, $salt)
---


<h1>Basic access authentication</h1>

Server side
When the server wants the user agent to authenticate itself towards the server after receiving an unauthenticated request, it must send a response with a HTTP 401 Unauthorized status line[7] and a WWW-Authenticate header field.[8]

The WWW-Authenticate header field for basic authentication is constructed as following:

WWW-Authenticate: Basic realm="User Visible Realm"

The server may choose to include the charset parameter from RFC 7617:[3]

WWW-Authenticate: Basic realm="User Visible Realm", charset="UTF-8"

This parameter indicates that the server expects the client to use UTF-8 for encoding username and password (see below).

Client side
When the user agent wants to send authentication credentials to the server, it may use the Authorization header field.

The Authorization header field is constructed as follows:[9]

The username and password are combined with a single colon (:). This means that the username itself cannot contain a colon.
The resulting string is encoded into an octet sequence. The character set to use for this encoding is by default unspecified, as long as it is compatible with US-ASCII, but the server may suggest use of UTF-8 by sending the charset parameter.[9]
The resulting string is encoded using a variant of Base64 (+/ and with padding).
The authorization method and a space (e.g. "Basic ") is then prepended to the encoded string.
For example, if the browser uses Aladdin as the username and open sesame as the password, then the field's value is the Base64 encoding of Aladdin:open sesame, or QWxhZGRpbjpvcGVuIHNlc2FtZQ==. Then the Authorization header field will appear as:

Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==