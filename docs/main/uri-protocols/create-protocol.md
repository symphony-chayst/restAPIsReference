---
description: >-
  Released in 1.52. Adds a URI protocol to a pod's configuration. Each pod
  stores a configuration to indicate which URI protocols can be transformed to a
  link inside a message in the UI.
---

# Create Protocol

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/system/protocols" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> ### 📘 Naming
>
> The name specified for the `scheme` parameter must start with a letter, must contain only letters, numbers, dashes, dots, and plus characters, and cannot be null.

> ### ❗️ Required Permissions
>
> This endpoint may only be called by _Service User_ accounts with the _User Provisioning_ role.
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
