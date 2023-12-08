---
description: Get a list of all Information Barrier Groups in the company (pod).
---

# List IB Groups

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/group/list" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 📘 Note
>
> This API returns only IB Groups that have at least one policy associated with it.

> #### 🚧 Roles and Privileges
>
> Calling this endpoint requires the ACCESS\_USER\_PROVISIONING\_API privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
