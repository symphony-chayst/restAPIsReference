# Read Presence Feed

Reads the specified presence feed that was created using the [Create Presence feed](create-presence-feed.md) endpoint. The feed returned includes the user presence statuses that have changed since they were last read.

{% hint style="danger" %}
Starting with SBE 24.1, the API is deprecated&#x20;
{% endhint %}



{% swagger src="../.gitbook/assets/pod-api-public.yaml" path="/v1/presence/feed/{feedId}/read" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

When calling this as an [OBO-enabled endpoint](../main/apps-on-behalf-of-obo/), use the [OBO User Authenticate](../main/apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.
