**CONTENTS**
- [Introduction to JWT](#introduction-to-jwt)
- [Structure of JWT](#structure-of-jwt)
  - [Header](#header)
  - [Payload](#payload)
  - [Signature](#signature)
- [How JWT Works](#how-jwt-works)
- [Uses of JWT](#uses-of-jwt)
  - [Authentication](#authentication)
  - [Information Exchange](#information-exchange)
- [Advantages and Disadvantages](#advantages-and-disadvantages)
  - [Advantages](#advantages)
  - [Disadvantages](#disadvantages)
- [Security Considerations](#security-considerations)

# Introduction to JWT
- JSON Web Tokens (JWT) are an open standard (RFC 7519) that define a compact and self-contained way for securely transmitting information between parties as a JSON object.

- This information can be verified and trusted because it is digitally signed. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.

# Structure of JWT
JWTs consist of three parts, separated by dots (.), which are: Header, Payload, and Signature. Therefore, a JWT typically looks like `xxxxx.yyyyy.zzzzz`.

## Header
The header typically consists of two parts: the type of the token, which is JWT, and the signing algorithm being used, such as HMAC SHA256 or RSA.

## Payload
The payload contains the claims. Claims are statements about an entity (typically, the user) and additional data. There are three types of claims: registered, public, and private claims.

## Signature
To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.

# How JWT Works
- When a user logs in using their credentials, a JWT is returned.
- Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema.
- The server's protected routes will check for a valid JWT in the Authorization header, and if it's present, the user will be allowed to access protected resources.

# Uses of JWT
## Authentication
JWTs are often used to implement authentication. Once the user is logged in, each subsequent request will include the JWT, allowing the user to access routes, services, and resources that are permitted with that token.

## Information Exchange
JWTs are a good way of securely transmitting information between parties because they can be signed, which means you can be sure that the senders are who they say they are.

# Advantages and Disadvantages
## Advantages
- Compact: Because of their smaller size, JWTs can be sent through URL, POST parameters, or inside HTTP headers. Additionally, JWT's compact size makes it more feasible for SSO scenarios.
- Self-contained: The payload contains all the required information about the user, avoiding the need to query the database more than once.

## Disadvantages
- Security concerns: If the token is intercepted, it can be used by an unauthorized party. Also, because the information in a JWT is encoded and not encrypted, sensitive information should not be stored in a JWT.
- No state management: JWTs do not allow for invalidation or updating without replacing the token on the client side.

# Security Considerations
- Always ensure HTTPS is used to prevent MITM (Man in the Middle) attacks.
- Implement token expiration (exp claim) to reduce the risk of token replay attacks.
- Consider using a public/private key pair (RSA) for signing if you want to avoid sharing a secret key.








- [JWT (JSON Web Token)](#jwt-json-web-token)
  - [Token Composition](#token-composition)
    - [1. HEADER](#1-header)
    - [2. PAYLOAD Claims](#2-payload-claims)
      - [Claim](#claim)
      - [i. Registered Claim](#i-registered-claim)
        - [NumericDate](#numericdate)
      - [ii. Public Claim](#ii-public-claim)
      - [iii. Private Claim](#iii-private-claim)
    - [3. SIGNATURE](#3-signature)
  - [Creating & Validating](#creating--validating)
    - [Creating](#creating)
    - [Validating](#validating)
  - [When to use ?](#when-to-use-)
    - [Authorization](#authorization)
    - [Information Exchange (securely transmitting)](#information-exchange-securely-transmitting)
  - [Pros & Cons](#pros--cons)
    - [Pros](#pros)
    - [Cons](#cons)
  - [References](#references)

# JWT (JSON Web Token)
   - A ```string``` representing a set of ```claims``` as a ```JSON``` object that is encoded in ```base64url```, enabling the ```claims``` to be digitally signed and/or encrypted, and separated by period ```.``` characters.

## Token Composition
  - Token consist of 3 parts separated by dots ```.``` and encode with ```base64Url```
  - **Encode** but **Not Encrypted** : Secret data should not be in the ```HEADER``` and ```PAYLOAD```
    - <img width="530" alt="image" src="https://user-images.githubusercontent.com/73396926/200079344-e5b3062e-3534-45e3-be20-1a5fd1e2755e.png">

### 1. HEADER 
  - Typically consists of 2 parts:
     1. "typ" (Token type) : JWT
     2. ["alg" (Signature Encryption Algorithm)](https://pyjwt.readthedocs.io/en/stable/algorithms.html#digital-signature-algorithms) : HS256
### 2. PAYLOAD Claims 
#### Claim
   - The ```JWT Claims``` represents a ```JSON``` object whose members are the claims conveyed by the JWT.  
   - The ```Claim Names``` MUST be unique; JWT parsers MUST either reject JWTs with duplicate Claim Names.
#### i. Registered Claim 
  - All OPTIONAL & application specific
  - See also : [JSON Web Token Claims](https://www.iana.org/assignments/jwt/jwt.xhtml)
  1. ```"sub"```(Subject) Claim 
      - The subject value MUST either be scoped to be locally unique in the context of the issuer or be globally unique.
  3. ```"iss"``` (Issuer) Claim
  4. ```"iat"``` (Issued At) Claim 
      -  the time at which the JWT was issued.  
      -  Can be used to determine the age of the JWT.  
      -  Its value MUST be a ```Number``` containing a``` NumericDate``` value.
  5. ```"exp"``` (Expiration Time) Claim
      -  The expiration time on or after which the JWT MUST NOT be accepted for processing. 
      -  requires that the current date/time MUST be before the expiration date/time listed in the "exp" claim.   
      -  Implementers MAY provide for some small leeway, usually no more than a few minutes
      -  Its value MUST be a number containing a NumericDate value.
  6. ```"nbf"``` (Not Before) Claim
      - like **"exp"** (Expiration Time) Claim
      - The time before which the JWT MUST NOT be accepted for processing.  
      - The processing of the "nbf" claim requires that the current date/time MUST be after or equal to the not-before date/time listed in the "nbf" claim.
  7. ```"aud"``` (Audience) Claim
      - The recipients that the JWT is intended for.  
      - Each principal intended to process the JWT MUST identify itself with a value in the audience claim.  
      - In the general case, the "aud" value is an ```array``` of case-sensitive ```strings```, each containing a StringOrURI value.  
      - In the special case when the JWT has one audience, the "aud" value MAY be a ```single case-sensitive string``` containing a StringOrURI value.
  8. ```"jti"``` (JWT ID) Claim
      - A unique identifier for the JWT.
      - The identifier value MUST be assigned in a manner that ensures that there is a negligible probability that the same value will be accidentally assigned to a different data object
      - if the application uses multiple issuers, collisions MUST be prevented among values produced by different issuers as well.
      - The "jti" claim can be used to prevent the JWT from being replayed.
##### NumericDate
  - A JSON numeric value representing the number of seconds from 1970-01-01T00:00:00Z UTC until the specified UTC date/time, ignoring leap seconds. 
  - each day is accounted for by exactly 86400 seconds
#### ii. Public Claim 
Claim Names can be defined at will by those using JWTs.  However, in
   order to prevent collisions, any new Claim Name should either be
   registered in the IANA "JSON Web Token Claims" registry established
   by Section 10.1 or be a Public Name: a value that contains a
   Collision-Resistant Name.  In each case, the definer of the name or
   value needs to take reasonable precautions to make sure they are in
   control of the part of the namespace they use to define the Claim
   Name.
#### iii. Private Claim 
  A producer and consumer of a JWT MAY agree to use Claim Names that
   are Private Names: names that are not Registered Claim Names
   (Section 4.1) or Public Claim Names (Section 4.2).  Unlike Public
      Claim Names, Private Claim Names are subject to collision and should
   be used with caution.

### 3. SIGNATURE
- Encryption Algorithm
- HEADER(base64Url encoded) : For integrality, to make sure the HEADER is not changed.
- PAYLOAD(base64Url encoded) : For integrality, to make sure the PAYLOAD is not changed.
- server-side Private Key : The decryption key is only stored on the server side.

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

## When to use ?
### Authorization
   - Single Sign On (SSO) : It's easily used across different domains.
### Information Exchange (securely transmitting)
   - public/private key pairs 
   - signature : It is calculated using the header and the payload  =  Could verify that the content hasn't been tampered with.
## Pros & Cons
### Pros
  - JSON : simplicity Compact, less verbose, smaller size
  - Self-contained : payload 裡面包含了使用者的資訊，也就是說解析後就可以看到，不需要再去 query 你的 database。
  - Security : public/private key supportred
  - JSON parsers - cross-platform supported
### Cons
  - Security Considerations
## References
- [Introduction to JSON Web Tokens - JWT](https://jwt.io/introduction)
- [RFC 7519](https://www.rfc-editor.org/rfc/rfc7519)
- [JSON Web Token (JWT) for OAuth Client Authorization Grants - IBM](https://www.ibm.com/docs/en/was-liberty/base?topic=uocpao2as-json-web-token-jwt-oauth-client-authorization-grants)
- [pyjwt API Reference](https://pyjwt.readthedocs.io/en/stable/api.html)
- [Token Storage](https://auth0.com/docs/secure/security-guidance/data-security/token-storage)
- [透過 JWT 實作驗證機制](https://medium.com/%E9%BA%A5%E5%85%8B%E7%9A%84%E5%8D%8A%E8%B7%AF%E5%87%BA%E5%AE%B6%E7%AD%86%E8%A8%98/%E7%AD%86%E8%A8%98-%E9%80%8F%E9%81%8E-jwt-%E5%AF%A6%E4%BD%9C%E9%A9%97%E8%AD%89%E6%A9%9F%E5%88%B6-2e64d72594f8)
- [OAuth Vs JWT - Detailed Comparison](https://www.wallarm.com/what/oauth-vs-jwt-detailed-comparison)
