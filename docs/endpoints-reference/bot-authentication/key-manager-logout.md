# Key Manager Logout

{% swagger src="../../.gitbook/assets/authenticator-api-public.yaml" path="/v1/logout" method="post" expanded="true" fullWidth="true" %}
[authenticator-api-public.yaml](../../.gitbook/assets/authenticator-api-public.yaml)
{% endswagger %}

To call the Key Manager Logout endpoint for a user, you must have a valid keyManagerToken for the user.

Example call sequence:

1. Call [Key Manager Authenticate](rsa-key-manager-authenticate.md) to get a `keyManagerToken`.
2. Call [Key Manager Logout](key-manager-logout.md) with the `keyManagerToken`.
