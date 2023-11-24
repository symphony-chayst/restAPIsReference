# Create Presence Feed

`Released in 1.48.`\
Creates a new stream capturing online status changes ("presence feed") for the company (pod) and returns the ID of the new feed. The feed will return the presence of users whose presence status has changed since it was last read.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/presence/feed/create" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

When calling this as an [OBO-enabled endpoint](ref:obo-enabled-endpoints), use the [OBO User Authenticate](ref:obo-user-authenticate) token for `sessionToken`.
