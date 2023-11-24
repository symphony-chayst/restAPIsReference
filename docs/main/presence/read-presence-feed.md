# Read Presence Feed

`Released in 1.48.`\
Reads the specified presence feed that was created using the [Create Presence feed](ref:create-presence-feed) endpoint. The feed returned includes the user presence statuses that have changed since they were last read.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/presence/feed/{feedId}/read" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

When calling this as an [OBO-enabled endpoint](ref:obo-enabled-endpoints), use the [OBO User Authenticate](ref:obo-user-authenticate) token for `sessionToken`.
