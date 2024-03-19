**CONTENTS**
- [Intro](#intro)
- [Structure](#structure)
  - [1.Header](#1header)
  - [2.Payload](#2payload)
    - [1.Registered claims (Optional)](#1registered-claims-optional)
    - [2.Public claims](#2public-claims)
      - [Characteristics](#characteristics)
      - [Usage Guidelines](#usage-guidelines)
    - [3.Private claims](#3private-claims)
      - [Characteristics](#characteristics-1)
      - [Usage Guidelines](#usage-guidelines-1)
      - [Examples](#examples)
  - [3.Signature](#3signature)
- [How JWT Works](#how-jwt-works)
- [Use Cases](#use-cases)
  - [Authentication](#authentication)
  - [Information Exchange](#information-exchange)
- [Advantages and Disadvantages](#advantages-and-disadvantages)
  - [Advantages](#advantages)
  - [Disadvantages](#disadvantages)
- [Security Considerations](#security-considerations)
  - [Creating \& Validating](#creating--validating)
    - [Creating](#creating)
    - [Validating](#validating)
  - [References](#references)

# Intro 
- **Open standard** (RFC 7519)
- Define a **compact** and **self-contained** way for securely transmitting information as a **JSON object**.
- **Verified and Trusted** (is digitally signe)
  - JWTs can be signed using a **secret** ( HMAC algorithm) or a **public/private key pair** using RSA or ECDSA.

# Structure 
- JWTs consist of 3 parts, separated by dots (.), and the whole JSON obj is encode with ```base64Url``` , typically looks like **`xxxxx.yyyyy.zzzzz`**
  - **Header**
  - **Payload**
  - **Signatur**
- JWTs are **Encoded** but **Not Encrypted** : Secret data should not be stored in the ```HEADER``` and ```PAYLOAD```.
  - <img width="1110" alt="Screenshot 2024-03-19 at 00 33 14" src="https://github.com/jeyu54217/Notes/assets/73396926/f60bdff0-9786-4348-a94c-eb17aa7a72a0">
  (source: [securitum](https://research.securitum.com/jwt-json-web-token-security/))

  
## 1.Header
- contains 2 parts:
  1. "typ" (type of the token) : JWT
  2. ["alg" (Signature Encryption Algorithm)](https://pyjwt.readthedocs.io/en/stable/algorithms.html#digital-signature-algorithms) : **HS256**, HMAC, SHA256, RSA

## 2.Payload
- The payload contains the claims. 
- JWT claims are statements about an entity (typically, the user) and additional data. 
- 3 types of claims: 
  - registered claims
  - public claims
  - private claims
  
### 1.Registered claims (Optional)
- Commom used claims:
  | Claim | Description |
  |-------|-------------|
  | iss (Issuer) | Identifies the principal that issued the JWT. |
  | sub (Subject) | Identifies the principal that is the subject of the JWT. |
  | aud (Audience) | Identifies the recipients that the JWT is intended for. |
  | exp (Expiration Time) | Identifies the expiration time on or after which the JWT must not be accepted for processing. |
  | nbf (Not Before) | Identifies the time before which the JWT must not be accepted for processing. |
  | iat (Issued At) | Identifies the time at which the JWT was issued. |
  | jti (JWT ID) | Provides a unique identifier for the JWT. |
- See also : [JSON Web Token Claims](https://www.iana.org/assignments/jwt/jwt.xhtml)

### 2.Public claims
- Public claims are those that have been predefined and are not directly related to the basic structure of a JWT but provide a means of sharing information between parties. 
- These claims are not registered in the IANA JSON Web Token Claims registry but are designed to be collision-resistant.
  
#### Characteristics
- **Universally Unique**: To ensure they are collision-resistant, public claims should either be defined in the IANA JSON Web Token Claims registry or be a URI that contains a collision-resistant namespace.
- **Customizable**: Unlike registered claims, public claims allow the parties involved to convey specific information relevant to their context that is not covered by the standard registered claims.

#### Usage Guidelines
- **Avoiding Collisions**: When defining public claims, it's crucial to ensure they are unique to prevent conflicts with other claims. Using a URI as a claim name is a common practice to achieve this.
- **Interoperability**: Even though public claims offer flexibility, it's important to use them in a way that does not hinder interoperability between different systems that might use the JWT.

### 3.Private claims
- Private claims are custom claims created to convey information between parties that agree on using them. 
- These claims offer the most flexibility as they are tailored to the specific requirements of the application or context in which the JWT is used.
#### Characteristics
- **Flexibility**: Private claims can be anything agreed upon by the parties using them, making them extremely versatile for conveying application-specific information.
- **Agreement Required**: Unlike public and registered claims, private claims require that all parties involved in the JWT exchange understand the meaning of these claims.

#### Usage Guidelines
- **Clear Definitions**: Since private claims are specific to the context in which they are used, it's essential for all parties involved to have a clear understanding of what each claim represents.
- **Security Considerations**: When using private claims to convey sensitive information, ensure that the JWT is encrypted (JWE) to prevent unauthorized access to the data.

#### Examples
- **User Roles**: A private claim could be used to indicate the roles of the user within an application, allowing for role-based access control.
- **Custom Identifiers**: Applications could use private claims to include custom identifiers relevant to the application domain, such as an internal user ID or transaction ID.


## 3.Signature
- To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.
  - Encryption Algorithm
  - HEADER(base64Url encoded) : For integrality, to make sure the HEADER is not changed.
  - PAYLOAD(base64Url encoded) : For integrality, to make sure the PAYLOAD is not changed.
  - server-side Private Key : The decryption key is only stored on the server side.

# How JWT Works
- When a user logs in using their credentials, a JWT is returned.
- Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema.
- The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources.
- <img width="664" alt="Screenshot 2024-03-19 at 00 19 06" src="https://github.com/jeyu54217/Notes/assets/73396926/128d07bb-a626-4340-874e-b048eeac79c9"> (source: [ByteByteGo](https://blog.bytebytego.com/p/ep69-explaining-json-web-token-jwt))

# Use Cases
## Authentication
- Single Sign On (SSO) : It's easily used across different domains.

## Information Exchange
- JWTs are a good way of securely transmitting information between parties because they can be signed, which means you can be sure that the senders are who they say they are.
- public/private key pairs 
- signature : It is calculated using the header and the payload  =  Could verify that the content hasn't been tampered with.
  
# Advantages and Disadvantages
## Advantages
- Compact: Because of their smaller size, JWTs can be sent through URL, POST parameters, or inside HTTP headers. Additionally, JWT's compact size makes it more feasible for SSO scenarios.
- Self-contained: The payload contains all the required information about the user, avoiding the need to query the database more than once.
- Security: public/private key supported
- JSON parsers: cross-platform supported
  
## Disadvantages
- Security concerns: If the token is intercepted, it can be used by an unauthorized party. Also, because the information in a JWT is encoded and not encrypted, sensitive information should not be stored in a JWT.
- No state management: JWTs do not allow for invalidation or updating without replacing the token on the client side.

# Security Considerations
- Always ensure HTTPS is used to prevent MITM (Man in the Middle) attacks.
- Implement token expiration (exp claim) to reduce the risk of token replay attacks.
- Consider using a public/private key pair (RSA) for signing if you want to avoid sharing a secret key.






## Creating & Validating
### Creating
1.  Create a JWT Claims Set containing the desired claims.  Note that
       whitespace is explicitly allowed in the representation and no
       canonicalization need be performed before encoding.

2.  Let the Message be the octets of the UTF-8 representation of the
       JWT Claims Set.

3.  Create a JOSE Header containing the desired set of Header
       Parameters.  The JWT MUST conform to either the [JWS] or [JWE]
       specification.  Note that whitespace is explicitly allowed in the
       representation and no canonicalization need be performed before
       encoding.
4.  Depending upon whether the JWT is a JWS or JWE, there are two
       cases:

       *  If the JWT is a JWS, create a JWS using the Message as the JWS
          Payload; all steps specified in [JWS] for creating a JWS MUST
          be followed.

       *  Else, if the JWT is a JWE, create a JWE using the Message as
          the plaintext for the JWE; all steps specified in [JWE] for
          creating a JWE MUST be followed.

   5.  If a nested signing or encryption operation will be performed,
       let the Message be the JWS or JWE, and return to Step 3, using a
       "cty" (content type) value of "JWT" in the new JOSE Header
       created in that step.

   6.  Otherwise, let the resulting JWT be the JWS or JWE.
### Validating
If any of the listed steps fail, then the JWT MUST be rejected
1.   Verify that the JWT contains at least one period ('.')
        character.

   2.   Let the Encoded JOSE Header be the portion of the JWT before the
        first period ('.') character.

   3.   Base64url decode the Encoded JOSE Header following the
        restriction that no line breaks, whitespace, or other additional
        characters have been used.

   4.   Verify that the resulting octet sequence is a UTF-8-encoded
        representation of a completely valid JSON object conforming to
        RFC 7159 [RFC7159]; let the JOSE Header be this JSON object.

   5.   Verify that the resulting JOSE Header includes only parameters
        and values whose syntax and semantics are both understood and
        supported or that are specified as being ignored when not
        understood.

   6.   Determine whether the JWT is a JWS or a JWE using any of the
        methods described in Section 9 of [JWE]
7.   Depending upon whether the JWT is a JWS or JWE, there are two
        cases:

        *  If the JWT is a JWS, follow the steps specified in [JWS] for
           validating a JWS.  Let the Message be the result of base64url
           decoding the JWS Payload.

        *  Else, if the JWT is a JWE, follow the steps specified in
           [JWE] for validating a JWE.  Let the Message be the resulting
           plaintext.

   8.   If the JOSE Header contains a "cty" (content type) value of
        "JWT", then the Message is a JWT that was the subject of nested
        signing or encryption operations.  In this case, return to Step
        1, using the Message as the JWT.

   9.   Otherwise, base64url decode the Message following the
        restriction that no line breaks, whitespace, or other additional
        characters have been used.

   10.  Verify that the resulting octet sequence is a UTF-8-encoded
        representation of a completely valid JSON object conforming to
        RFC 7159 [RFC7159]; let the JWT Claims Set be this JSON object.




## References
- [Introduction to JSON Web Tokens - JWT](https://jwt.io/introduction)
- [RFC 7519](https://www.rfc-editor.org/rfc/rfc7519)
- [JSON Web Token (JWT) for OAuth Client Authorization Grants - IBM](https://www.ibm.com/docs/en/was-liberty/base?topic=uocpao2as-json-web-token-jwt-oauth-client-authorization-grants)
- [pyjwt API Reference](https://pyjwt.readthedocs.io/en/stable/api.html)
- [Token Storage](https://auth0.com/docs/secure/security-guidance/data-security/token-storage)
- [透過 JWT 實作驗證機制](https://medium.com/%E9%BA%A5%E5%85%8B%E7%9A%84%E5%8D%8A%E8%B7%AF%E5%87%BA%E5%AE%B6%E7%AD%86%E8%A8%98/%E7%AD%86%E8%A8%98-%E9%80%8F%E9%81%8E-jwt-%E5%AF%A6%E4%BD%9C%E9%A9%97%E8%AD%89%E6%A9%9F%E5%88%B6-2e64d72594f8)
- [OAuth Vs JWT - Detailed Comparison](https://www.wallarm.com/what/oauth-vs-jwt-detailed-comparison)
