---
description: Log out a user’s key manager session.
---

# Key Manager Logout

{% swagger src="../../.gitbook/assets/km-cert-api-public.yaml" path="/v1/logout" method="post" %}
[km-cert-api-public.yaml](../../.gitbook/assets/km-cert-api-public.yaml)
{% endswagger %}

To call the Key Manager Logout endpoint for a user, you must have a valid keyManagerToken for the user.

Example call sequence:

1. Call [Key Manager Authenticate](rsa-key-manager-authenticate.md) to get a `keyManagerToken`.
2. Call [Key Manager Logout](key-manager-logout.md) with the `keyManagerToken`.
