---
description: Released prior to 1.43. Assign a disclaimer to a user.
---

# Update User Disclaimer

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{uid}/disclaimer/update" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

As the example shows, the disclaimer to be assigned to the user must be included in the data parameter.

> ### 🚧 Roles and privileges
>
> Calling this endpoint requires the User Provisioning role with ACCESS\_USER\_PROVISIONING\_API privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
