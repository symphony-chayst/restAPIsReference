# Bots Authentication

When a bot process (API caller) starts, it must perform both session authentication and key manager authentication to obtain session tokens. These two tokens, which should be treated as opaque data by the bot, must be presented in custom headers with each subsequent REST API request. This authentication process can be performed using client certificates or a JSON Web Token (JWT) signed and verified using an [RSA public/private key pair](https://docs.developers.symphony.com/building-bots-on-symphony/authentication/rsa-authentication).

### Authentication Using an RSA Public/Private Key Pair

When a bot process (API caller) starts, it must first call the [RSA Session Authenticate](rsa-session-authenticate.md) endpoint for authenticating on the Symphony servers (pod). This endpoint will examine the JWT provided to identify the bot user and return a session token.

The bot must then call the analogous [RSA Key Manager Authenticate](rsa-key-manager-authenticate.md) endpoint for authenticating on the key manager. This endpoint will return another session token.

For more information, refer to [RSA Bot Authentication Workflow](https://docs.developers.symphony.com/building-bots-on-symphony/authentication/rsa-authentication).

### Authentication Using Client Certificates

When a bot process (API caller) starts, it must first call the [Session Authenticate](rsa-session-authenticate.md) endpoint for authenticating on the Symphony servers (pod). This endpoint will examine the client certificate provided in the TLS session to identify the bot user and return a session token.

The bot must then call the analogous [Key Manager Authenticate](rsa-key-manager-authenticate.md) endpoint for authenticating on the key manager. This endpoint will return another session token.

This approach provides a cryptographically secure authentication mechanism for callers of the API, without requiring the bot process to perform any cryptographic operations. The secure authentication is implemented in the TLS layer and handled for the client by the SSL Socket library used to establish the network connection.

For more information, refer to [Certificate Authentication Workflow](https://docs.developers.symphony.com/building-bots-on-symphony/authentication/certificate-authentication).
