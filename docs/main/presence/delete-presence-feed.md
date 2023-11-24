# Delete Presence Feed

`Released in 1.48.`\
Deletes a presence status feed. This endpoint returns the ID of the deleted feed if the deletion is successful.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/presence/feed/{feedId}/delete" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

When calling this as an [OBO-enabled endpoint](ref:obo-enabled-endpoints), use the [OBO User Authenticate](ref:obo-user-authenticate) token for `sessionToken`.

This endpoint returns a **403 Forbidden** error when the user requesting the deletion isn’t the original user who created the presence feed with the [Create Presence Feed](ref:create-presence-feed) endpoint.
