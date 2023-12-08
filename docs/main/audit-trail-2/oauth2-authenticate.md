---
description: >-
  Released in 20.13. Authenticates the API caller on the Symphony servers (pod)
  using a Session token, and returns a valid OAuth2 access token.
---

# OAuth2 Authenticate

This authentication is required to use the Audit Trails 2 enpoints.

{% swagger src="../../.gitbook/assets/login-api-public.yaml" path="/idm/tokens" method="post" expanded="true" fullWidth="true" %}
[login-api-public.yaml](../../.gitbook/assets/login-api-public.yaml)
{% endswagger %}

> ### 📘 Notes
>
> * Use scope 'at2' in order get access to the Audit Trail 2 endpoints.
> * The payload consists is a JWT token object that is divided in three properties as follow:
>   * the token type.
>   * the duration of time the access token is granted for (in seconds).
>   * the JWT token containing the caller's id or application, an expiration date, and a set of entitlements related to the specified scope, signed by the caller's private RSA key.
