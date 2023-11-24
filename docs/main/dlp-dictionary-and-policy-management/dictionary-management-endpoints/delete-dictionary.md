---
description: Deletes a dictionary.
---

# Delete Dictionary

Available on Agent 2.0.0 and above. See the [SBE x Agent compatibilities](https://docs.developers.symphony.com/admin-guide/agent-guide/sbe-x-agent-compatibility-matrix) for more details about the minimal requirements.

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v1/dlp/dictionaries/{dictId}" method="delete" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> ### 🚧 Important
>
> A dictionary can only be deleted if no longer associated with any enabled or disabled policy. Use [All DLP Policies](ref:all-policies) and [Get Policy](ref:get-policy) to retrieve the dictionary or dictionaries associated with a particular policy.

> ### 🚧 Required Permissions
>
> Calling this endpoint requires a Service User Account set with the Expression Filter Policy Management role. For more information about Service User accounts and their roles, see the [Symphony Administration Guide](https://symphony.direct/).
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
