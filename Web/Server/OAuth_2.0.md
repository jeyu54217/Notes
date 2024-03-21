

- [OAuth 2.0](#oauth-20)
  - [Terminology](#terminology)
  - [Authorization Grant Types](#authorization-grant-types)
  - [Access Tokens](#access-tokens)
  - [Security Considerations](#security-considerations)
  - [Extensions](#extensions)
  - [Flow Example: Authorization Code Grant](#flow-example-authorization-code-grant)


# OAuth 2.0

- An authorization framework that enables applications to secure access to user accounts on an HTTP service(Facebook, GitHub, and Google). 
- Provides authorization flows for web, desktop, and mobile devices.

## Terminology

- **Resource Owner**: The user, who can grant access to their account. (User)
- **Resource Server**: The server hosting the protected resources.(social media or banking site).
- **Client**: The application requesting access to the resource server.
- **Authorization Server**: The server that authenticates the Resource Owner and issues access tokens to the Client after getting proper authorization.

## Authorization Grant Types

1. **Authorization Code Grant**: Used by Web and mobile applications where the client redirects the user to the authorization server, the user authenticates, and the client receives an authorization code it can exchange for an access token.
2. **Implicit Grant**: Designed for clients implemented in a browser using a scripting language such as JavaScript. It is less secure and is being replaced by the Authorization Code Grant with PKCE.
3. **Resource Owner Password Credentials Grant**: Should only be used when there is a high degree of trust between the Resource Owner and the Client, such as the device operating system or a highly privileged application.
4. **Client Credentials Grant**: Used when the client is also the resource owner. Suitable for machine-to-machine authentication where a specific user’s permission is not required.

## Access Tokens

- **Access Token**: A token that is issued by the authorization server that the client uses to access the protected resources hosted by the resource server.
- **Refresh Token**: A token used to obtain a new access token without requiring the user to be present.

## Security Considerations

OAuth 2.0 requires careful security considerations, especially when handling tokens that grant access to user resources. Some best practices include:

- Using secure connections (HTTPS) to transmit tokens.
- Storing tokens securely on the client side.
- Implementing token expiration and renewal mechanisms.

## Extensions

OAuth 2.0 can be extended with specifications to address specific use cases or add features, such as OpenID Connect for authentication or OAuth 2.0 Token Introspection for token validation.

## Flow Example: Authorization Code Grant

1. **Authorization Request**: The client redirects the user to the authorization server with the type of access requested.
2. **User Authorization**: The user authorizes the application at the authorization server.
3. **Authorization Response**: The server redirects the user back to the client with an authorization code.
4. **Token Request**: The client requests an access token from the authorization server by presenting authentication of its own identity, and the authorization code.
5. **Token Response**: The authorization server authenticates the client, validates the authorization code, and if valid, issues an access token and, optionally, a refresh token.

OAuth 2.0 is a complex framework that requires a deep understanding of its components and security implications to implement securely and effectively.
