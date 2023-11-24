---
description: >-
  Released in 1.52. Deletes a URI protocol from a pod's configuration. Each pod
  stores a configuration to indicate which URI protocols can be transformed to a
  link inside a message in the UI.
---

# Delete Protocol

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/system/protocols/{scheme}" method="delete" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> ### ❗️ Required Permissions
>
> This endpoint may only be called by _Service User_ accounts with the _User Provisioning_ role.
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
