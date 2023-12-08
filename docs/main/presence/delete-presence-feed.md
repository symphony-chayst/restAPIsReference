# Delete Presence Feed

Deletes a presence status feed. This endpoint returns the ID of the deleted feed if the deletion is successful.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/presence/feed/{feedId}/delete" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.

This endpoint returns a **403 Forbidden** error when the user requesting the deletion isn’t the original user who created the presence feed with the [Create Presence Feed](create-presence-feed.md) endpoint.
