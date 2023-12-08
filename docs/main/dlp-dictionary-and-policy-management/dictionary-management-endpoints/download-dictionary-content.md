---
description: Downloads Base64-encoded dictionary content.
---

# Download Dictionary Content

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v1/dlp/dictionaries/{dictId}/data/download" method="get" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

### Decoded Results Example

`term1`\
`term2`\
`term3`

> #### 🚧 Required Permissions
>
> Calling this endpoint requires a Service User Account set with the Expression Filter Policy Management role. For more information about Service User accounts and their roles, see the [Symphony Administration Guide](https://symphony.direct/).
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
