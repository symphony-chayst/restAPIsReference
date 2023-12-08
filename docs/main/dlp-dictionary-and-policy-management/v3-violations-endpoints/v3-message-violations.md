---
description: >-
  Gets violations as a result of policy enforcement on messages. The message
  part of this violation is the same as documented in Create Message v4
---

# V3 Message Violations

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v3/dlp/violations/message" method="get" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> #### 📘 sharedMessage
>
> Note that the `sharedMessage` attribute is only returned when the message represented by this class is a wall post sharing another message.\
> _Please note the payload example with `sharedMessage` object included._

> #### 🚧 Required Permissions
>
> Calling this endpoint requires the Expression Filter Policy Management role.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
