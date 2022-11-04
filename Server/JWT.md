**CONTENTS**
- [JWT (JSON Web Token)](#jwt-json-web-token)
  - [Token Composition](#token-composition)
    - [1. HEADER parameter](#1-header-parameter)
    - [2. PAYLOAD Claims](#2-payload-claims)
      - [Claim](#claim)
      - [1. Registered Claim](#1-registered-claim)
        - [NumericDate](#numericdate)
      - [2. Public Claim](#2-public-claim)
      - [3. Private Claim](#3-private-claim)
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
    ![images]([https://i.imgur.com/x57MeJO.png](https://devonblog.com/wp-content/uploads/2018/08/jwt1.png))

### 1. HEADER parameter 
- Typically consists of 2 parts:
     1. "typ" (Token type) : JWT
     2. ["alg" (Signature Encryption Algorithm)](https://pyjwt.readthedocs.io/en/stable/algorithms.html#digital-signature-algorithms) : HS256
### 2. PAYLOAD Claims 
#### Claim
   - The ```JWT Claims``` represents a ```JSON``` object whose members are the claims conveyed by the JWT.  
   - The Claim Names within a JWT Claims Set MUST be unique; JWT parsers MUST either reject JWTs with duplicate Claim Names or use a JSON parser that returns only the lexically last duplicate member name.
#### 1. Registered Claim
1) "sub" (Subject) Claim
   -    The "sub" (subject) claim identifies the principal that is the
   subject of the JWT.  The claims in a JWT are normally statements
   about the subject.  The subject value MUST either be scoped to be
   locally unique in the context of the issuer or be globally unique.
   The processing of this claim is generally application specific.  The
   "sub" value is a case-sensitive string containing a StringOrURI
   value.  Use of this claim is OPTIONAL.
3) "iss" (Issuer) Claim
    -    The "iss" (issuer) claim identifies the principal that issued the
   JWT.  The processing of this claim is generally application specific.
   The "iss" value is a case-sensitive string containing a StringOrURI
   value.  Use of this claim is OPTIONAL.
4) "iat" (Issued At) Claim 
    -    The "iat" (issued at) claim identifies the time at which the JWT was
   issued.  This claim can be used to determine the age of the JWT.  Its
   value MUST be a number containing a NumericDate value.  Use of this
   claim is OPTIONAL.
6) "exp" (Expiration Time) Claim
    -    The "exp" (expiration time) claim identifies the expiration time on
   or after which the JWT MUST NOT be accepted for processing.  The
   processing of the "exp" claim requires that the current date/time
   MUST be before the expiration date/time listed in the "exp" claim.   Implementers MAY provide for some small leeway, usually no more than
   a few minutes, to account for clock skew.  Its value MUST be a number
   containing a NumericDate value.  Use of this claim is OPTIONAL.
7) "aud" (Audience) Claim
    -    The "aud" (audience) claim identifies the recipients that the JWT is
   intended for.  Each principal intended to process the JWT MUST
   identify itself with a value in the audience claim.  If the principal
   processing the claim does not identify itself with a value in the
   "aud" claim when this claim is present, then the JWT MUST be
   rejected.  In the general case, the "aud" value is an array of case-
   sensitive strings, each containing a StringOrURI value.  In the
   special case when the JWT has one audience, the "aud" value MAY be a
   single case-sensitive string containing a StringOrURI value.  The
   interpretation of audience values is generally application specific.
   Use of this claim is OPTIONAL.

8) "nbf" (Not Before) Claim
    -    The "nbf" (not before) claim identifies the time before which the JWT
   MUST NOT be accepted for processing.  The processing of the "nbf"
   claim requires that the current date/time MUST be after or equal to
   the not-before date/time listed in the "nbf" claim.  Implementers MAY
   provide for some small leeway, usually no more than a few minutes, to
   account for clock skew.  Its value MUST be a number containing a
   NumericDate value.  Use of this claim is OPTIONAL.
10) "jti" (JWT ID) Claim
    -    The "jti" (JWT ID) claim provides a unique identifier for the JWT.
   The identifier value MUST be assigned in a manner that ensures that
   there is a negligible probability that the same value will be
   accidentally assigned to a different data object; if the application
   uses multiple issuers, collisions MUST be prevented among values
   produced by different issuers as well.  The "jti" claim can be used
   to prevent the JWT from being replayed.  The "jti" value is a case-
   sensitive string.  Use of this claim is OPTIONAL.
##### NumericDate
  - A JSON numeric value representing the number of seconds from 1970-01-01T00:00:00Z UTC until the specified UTC date/time, ignoring leap seconds. 
  - each day is accounted for by exactly 86400 seconds
#### 2. Public Claim 
Claim Names can be defined at will by those using JWTs.  However, in
   order to prevent collisions, any new Claim Name should either be
   registered in the IANA "JSON Web Token Claims" registry established
   by Section 10.1 or be a Public Name: a value that contains a
   Collision-Resistant Name.  In each case, the definer of the name or
   value needs to take reasonable precautions to make sure they are in
   control of the part of the namespace they use to define the Claim
   Name.
#### 3. Private Claim 
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
- 
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
- https://medium.com/mr-efacani-teatime/%E6%B7%BA%E8%AB%87jwt%E7%9A%84%E5%AE%89%E5%85%A8%E6%80%A7%E8%88%87%E9%81%A9%E7%94%A8%E6%83%85%E5%A2%83-301b5491b60e
- https://medium.com/bandai%E7%9A%84%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/%E6%89%8B%E6%8A%8A%E6%89%8B%E7%A8%8B%E5%BC%8F%E5%AF%A6%E4%BD%9C%E5%88%86%E4%BA%AB%E7%B3%BB%E5%88%97-jwt-authentication-%E5%92%8C-django-rest-framework%E7%9A%84%E7%B5%90%E5%90%88-d1f811b8c9da
- https://www.wallarm.com/what/oauth-vs-jwt-detailed-comparison
- https://medium.com/%E9%BA%A5%E5%85%8B%E7%9A%84%E5%8D%8A%E8%B7%AF%E5%87%BA%E5%AE%B6%E7%AD%86%E8%A8%98/%E7%AD%86%E8%A8%98-%E9%80%8F%E9%81%8E-jwt-%E5%AF%A6%E4%BD%9C%E9%A9%97%E8%AD%89%E6%A9%9F%E5%88%B6-2e64d72594f8
- https://siddharthac6.medium.com/json-web-token-jwt-the-right-way-of-implementing-with-node-js-65b8915d550e
- https://www.iana.org/assignments/jwt/jwt.xhtml
- https://5xruby.tw/posts/what-is-jwt
