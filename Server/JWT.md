# JWT (JSON Web Token)
## What it is ?
### 1. Definition
JWTs represent a set of claims as a JSON object that is encoded in a
   JWS and/or JWE structure.  This JSON object is the JWT Claims Set.
   As per Section 4 of RFC 7159 [RFC7159], the JSON object consists of
   zero or more name/value pairs (or members), where the names are
   strings and the values are arbitrary JSON values.  These members are
   the claims represented by the JWT.  This JSON object MAY contain
   whitespace and/or line breaks before or after any JSON values or
   structural characters, in accordance with Section 2 of RFC 7159
   [RFC7159].

   The member names within the JWT Claims Set are referred to as Claim
   Names.  The corresponding values are referred to as Claim Values.

   The contents of the JOSE Header describe the cryptographic operations
   applied to the JWT Claims Set.  If the JOSE Header is for a JWS, the
   JWT is represented as a JWS and the claims are digitally signed or
   MACed, with the JWT Claims Set being the JWS Payload.  If the JOSE
   Header is for a JWE, the JWT is represented as a JWE and the claims
   are encrypted, with the JWT Claims Set being the plaintext encrypted
   by the JWE.  A JWT may be enclosed in another JWE or JWS structure to
   create a Nested JWT, enabling nested signing and encryption to be
   performed.

   A JWT is represented as a sequence of URL-safe parts separated by
   period ('.') characters.  Each part contains a base64url-encoded
   value.  The number of parts in the JWT is dependent upon the
   representation of the resulting JWS using the JWS Compact
   Serialization or JWE using the JWE Compact Serialization.

#### (1). JWT
     A string representing a set of claims as a JSON object 
     that is encoded in a JWS or JWE, enabling the claims 
     to be digitally signed or MACed and/or encrypted.
#### (2). Claim
The JWT Claims Set represents a JSON object whose members are the
   claims conveyed by the JWT.  The Claim Names within a JWT Claims Set
   MUST be unique; JWT parsers MUST either reject JWTs with duplicate
   Claim Names or use a JSON parser that returns only the lexically last
   duplicate member name, as specified in Section 15.12 ("The JSON
   Object") of ECMAScript 5.1 [ECMAScript].

   The set of claims that a JWT must contain to be considered valid is
   context dependent and is outside the scope of this specification.
   Specific applications of JWTs will require implementations to
   understand and process some claims in particular ways.  However, in
   the absence of such requirements, all claims that are not understood
   by implementations MUST be ignored.

   There are three classes of JWT Claim Names: Registered Claim Names,
   Public Claim Names, and Private Claim Names.

#### NumericDate
    A JSON numeric value representing the number of seconds from
    1970-01-01T00:00:00Z UTC until the specified UTC date/time,
    ignoring leap seconds.  This is equivalent to the IEEE Std 1003.1,
    2013 Edition [POSIX.1] definition "Seconds Since the Epoch", in
    which each day is accounted for by exactly 86400 seconds, other
    than that non-integer values can be represented.  See RFC 3339
    [RFC3339] for details regarding date/times in general and UTC in particular.
### 2. Token Composition
#### Real Structure
Token consist of 3 parts separated by dots "." and encode with base64Url
![](https://i.imgur.com/x57MeJO.png)

#### (1). HEADER parameter 
・Encode by **base64Url**
・**Not Encrypted** : Secret data should not be here
・Typically consists of 2 parts:
1)  "typ" (Token type) : JWT
2)  "alg" (Signature Encryption Algorithm) : HS256
#### (2). PAYLOAD Claims 
・Encode by **base64Url**
・**Not Encrypted** : Secret data should not be here

   The following Claim Names are registered in the IANA "JSON Web Token
   Claims" registry established by Section 10.1.  None of the claims
   defined below are intended to be mandatory to use or implement in all
   cases, but rather they provide a starting point for a set of useful,
   interoperable claims.  Applications using JWTs should define which
   specific claims they use and when they are required or optional.  All
   the names are short because a core goal of JWTs is for the
##### 1). Registered claims:
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
##### 2). Public claims
   Claim Names can be defined at will by those using JWTs.  However, in
   order to prevent collisions, any new Claim Name should either be
   registered in the IANA "JSON Web Token Claims" registry established
   by Section 10.1 or be a Public Name: a value that contains a
   Collision-Resistant Name.  In each case, the definer of the name or
   value needs to take reasonable precautions to make sure they are in
   control of the part of the namespace they use to define the Claim
   Name.
##### 3). Private claims
  A producer and consumer of a JWT MAY agree to use Claim Names that
   are Private Names: names that are not Registered Claim Names
   (Section 4.1) or Public Claim Names (Section 4.2).  Unlike Public
      Claim Names, Private Claim Names are subject to collision and should
   be used with caution.
#### (3). SIGNATURE
1) Encryption Algorithm
2) HEADER(base64Url encoded) : For integrality, to make sure the HEADER is not changed.
4) PAYLOAD(base64Url encoded) : For integrality, to make sure the PAYLOAD is not changed.
5) server-side Private Key : The decryption key is only stored on the server side.
## How to use it ?
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

## When should use it?
Single Sign On ( SSO ) 因為它的開銷很小，而且

可以很輕鬆的跨 domains
## Why use it ? (Pros)
simplicity Compact
  less verbose
  smaller size
Self-contained  payload 裡面包含了使用者的資訊，也就是說解析後就可以看到，不需要再去 query 你的 database。
Security
  public/private key supportred
JSON parsers
![](https://i.imgur.com/NkFVYS1.png)
## Security Considerations (Cons)

## References
ww
