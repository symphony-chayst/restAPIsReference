# Get All Presence

Returns the presence of all users in a pod.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v2/users/presence" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> 📘 All non-inactive users are returned and some inactive users may be included. Any omitted user is inactive.

> 🚧 Only users with the "User Provisioning" role can call this endpoint

When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.

For a list of the available presence statuses, please see the [Get Presence](get-presence.md)
