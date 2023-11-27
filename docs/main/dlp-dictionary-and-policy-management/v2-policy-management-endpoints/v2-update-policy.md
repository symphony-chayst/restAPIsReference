---
description: >-
  Available on Agent 2.0.0 and above. Updates data for an existing policy, such
  as the dictionaries and also `name`, `type`, `contentTypes`, and `scopes`.
---

# V2 Update Policy

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v1/dlp/policies/{policyId}" method="put" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> ### 🚧 Important
>
> Do not use this endpoint to create new policies. Use [Create Policy](ref:create-policy).

> ### ❗️ Warning
>
> Sending an empty list of dictionaries with this endpoint deletes all dictionaries for the policy and disables the policy.

> ### 🚧 Required Permissions
>
> Calling this endpoint requires a Service User Account set with the Expression Filter Policy Management role. For more information about Service User accounts and their roles, see the [Symphony Administration Guide](https://symphony.direct/).
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
