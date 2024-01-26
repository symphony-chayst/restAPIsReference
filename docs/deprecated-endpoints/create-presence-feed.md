# Create Presence Feed

Creates a new stream capturing online status changes ("presence feed") for the company (pod) and returns the ID of the new feed. The feed will return the presence of users whose presence status has changed since it was last read.

{% hint style="danger" %}
Starting with SBE 24.1, the API is deprecated&#x20;
{% endhint %}



{% swagger src="../.gitbook/assets/pod-api-public.yaml" path="/v1/presence/feed/create" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

When calling this as an [OBO-enabled endpoint](../main/apps-on-behalf-of-obo/), use the [OBO User Authenticate](../main/apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.
