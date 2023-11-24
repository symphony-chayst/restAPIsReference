# List Message Receipts

Released in 1.54.2. Fetches receipts details from a specific message.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/messages/{messageId}/receipts" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> 🚧 Required roles
>
> Calling this endpoint requires the Content Management role with the VIEW\_MANAGE\_MESSAGES entitlement.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
