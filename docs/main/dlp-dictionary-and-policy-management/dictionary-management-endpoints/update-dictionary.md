---
description: >-
  Updates a dictionary's name. This also automatically updates the version
  number.
---

# Update Dictionary

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v1/dlp/dictionaries/{dictId}" method="put" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> #### 📘 Note
>
> * You can’t create a new dictionary with this endpoint.
> * All related policies will also have versions updated. (FIX)

> #### 🚧 Required Permissions
>
> Calling this endpoint requires a Service User Account set with the Expression Filter Policy Management role. For more information about Service User accounts and their roles, see the [Symphony Administration Guide](https://symphony.direct/).
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
