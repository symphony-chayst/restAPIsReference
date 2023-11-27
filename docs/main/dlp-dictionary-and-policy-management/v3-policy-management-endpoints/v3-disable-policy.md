---
description: >-
  Available on Agent 2.1.4 and above. See the SBE x Agent compatibilities for
  more details about the minimal requirements. Disables a policy.
---

# V3 Disable Policy

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v3/dlp/policies/{policyId}/disable" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

Delete disabled policies with [Delete Policy](v3-delete-policy.md).

> ### 🚧 Required Permissions
>
> Calling this endpoint requires a Service User Account set with the Expression Filter Policy Management role. For more information about Service User accounts and their roles, see the [Symphony Administration Guide](https://symphony.direct/).
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
