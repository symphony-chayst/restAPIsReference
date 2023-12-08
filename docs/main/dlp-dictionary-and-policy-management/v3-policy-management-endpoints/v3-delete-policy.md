---
description: Deletes a disabled policy.
---

# V3 Delete Policy

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v3/dlp/policies/{policyId}/delete" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

To delete a policy, first call [Disable Policy](v3-disable-policy.md), then call this endpoint.

> #### 🚧 Required Permissions
>
> Calling this endpoint requires a Service User Account set with the Expression Filter Policy Management role. For more information about Service User accounts and their roles, see the [Symphony Administration Guide](https://symphony.direct/).
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
