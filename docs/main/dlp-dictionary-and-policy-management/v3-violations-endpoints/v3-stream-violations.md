---
description: >-
  Available on Agent 2.1.4 and above. Gets violations as a result of policy
  enforcement on streams. Matched terms are decrypted by the Agent.
---

# V3 Stream Violations

When a violation occurs during the creation of a stream, there won't be any stream ID (because the stream was not created).

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v3/dlp/violations/stream" method="get" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> ### 🚧 Required Permissions
>
> Calling this endpoint requires the Expression Filter Policy Management role.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
