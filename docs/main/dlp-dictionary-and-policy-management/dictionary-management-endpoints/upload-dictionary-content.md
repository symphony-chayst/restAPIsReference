---
description: Upload new content to a dictionary and override the existing content.
---

# Upload Dictionary Content

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v1/dlp/dictionaries/{dictId}/data/upload" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> #### 📘 Note
>
> The DLP functionality supports two dictionary types for release 1.48.0: "Word" and "Regex". Because we could add more dictionary types in future without changes to the API version, make sure that your code can accommodate other new types.

> #### 🚧 Required Permissions
>
> Calling this endpoint requires a Service User Account set with the Expression Filter Policy Management role. For more information about Service User accounts and their roles, see the [Symphony Administration Guide](https://symphony.direct/).
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
