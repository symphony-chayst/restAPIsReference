---
description: >-
  Available on Agent 2.0.0 and above. Gets violations as a result of policy
  enforcement on streams. Matched terms are decrypted by the agent.
---

# V2 Stream Violations

When a violation occurs during the creation of a stream, note that there won't be any stream ID (because the stream was not created).

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v1/dlp/violations/stream" method="get" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> 🚧 Required Permissions
>
> Calling this endpoint requires a `ceservice` account. For more information, see the [Symphony Administration Guide](https://symphony.direct/).
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
