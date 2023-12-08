---
description: >-
  Authenticates the API caller on the Symphony servers (pod) using a Session
  token, and returns a valid OAuth2 access token.
---

# OAuth2 Authenticate

This authentication is required to use the Groups - Distribution Lists management endpoints.

`Released in 20.13.`

{% swagger src="../../.gitbook/assets/login-api-public.yaml" path="/idm/tokens" method="post" expanded="true" fullWidth="true" %}
[login-api-public.yaml](../../.gitbook/assets/login-api-public.yaml)
{% endswagger %}

> ### 📘 Notes
>
> * The payload consists is a JWT token object that is divided in three properties as follow:
>   * the token type.
>   * the duration of time the access token is granted for (in seconds).
>   * the JWT token containing the caller's id or application, an expiration date, and a set of entitlements related to the specified scope, signed by the caller's private RSA key.
