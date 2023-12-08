---
description: Unsubscribes an array of users from the specified Signal.
---

# Unsubscribe Signal

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v1/signals/{id}/unsubscribe" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> #### 🚧 Permissions
>
> * To unsubscribe from a signal, the requesting user cannot be the owner of the signal.
> * To unsubscribe other users from a signal, the requesting user needs to have the `canManageSignalSubscription` entitlement and the signal cannot be a company-wide signal.
