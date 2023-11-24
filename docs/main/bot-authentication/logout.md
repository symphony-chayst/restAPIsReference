# Session Logout

Released in 1.47. Log out a user’s session.

{% swagger src="../../.gitbook/assets/authenticator-api-public.yaml" path="/v1/logout" method="post" expanded="true" fullWidth="true" %}
[authenticator-api-public.yaml](../../.gitbook/assets/authenticator-api-public.yaml)
{% endswagger %}

> 📘 Note
>
> You must provide a certificate where the Common Name of the certificate matches the username of an active Service User account on your pod.\
> To call the Logout endpoint for a user, you must have a valid sessionToken for the user.

Example call sequence:

1. Call [Session Authenticate](rsa-session-authenticate.md) to get a `sessionToken`.
2. Call [Logout](logout.md) with the `sessionToken`.

To call the Logout endpoint for an app, you must have a valid session token for an app that's been installed for the user whom you intend to log out.

Example call sequences:

1. Call [App Authenticate](../apps-on-behalf-of-obo/obo-rsa-app-authentication.md) to get a `sessionToken`.
2. Call [Logout](logout.md) with the `sessionToken`.
3. Call [App Authenticate](../apps-on-behalf-of-obo/obo-rsa-app-authentication.md) to get a `sessionToken`.
4. Call [User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) with the `sessionToken`.
5. Call [Logout](logout.md) with the `sessionToken`.
