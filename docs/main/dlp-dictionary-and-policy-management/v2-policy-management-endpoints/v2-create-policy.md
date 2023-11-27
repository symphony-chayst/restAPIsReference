---
description: >-
  Available on Agent 2.0.0 and above. See the SBE x Agent compatibilities for
  more details about the minimal requirements. Creates a new policy with
  dictionary references.
---

# V2 Create Policy

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v1/dlp/policies" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

After you create a policy, call [Enable Policy](v2-enable-policy.md) to start enforcing the policy.

> ### 🚧 Required Permissions
>
> Calling this endpoint requires a Service User Account set with the Expression Filter Policy Management role. For more information about Service User accounts and their roles, see the [Symphony Administration Guide](https://symphony.direct/).
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
