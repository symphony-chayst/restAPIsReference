---
description: >-
  Updates data for an existing policy, such as the dictionaries and also `name`,
  `type`, `contentTypes`, and `scopes`.
---

# V3 Update Policy

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v3/dlp/policies/{policyId}/update" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> #### 🚧 Important
>
> Do not use this endpoint to create new policies. Use [Create Policy](v3-create-policy.md).

> #### ❗️ Warning
>
> Updating a policy requires to send a whole data that was used for creation a policy with modification to be applied. There is no partial update for this endpoint.

> #### 🚧 Required Permissions
>
> Calling this endpoint requires a Service User Account set with the Expression Filter Policy Management role. For more information about Service User accounts and their roles, see the [Symphony Administration Guide](https://symphony.direct/).
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
