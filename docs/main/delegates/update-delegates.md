---
description: Update the delegates assigned to a user.
---

# Update User Delegates

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{uid}/delegates/update" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

As the example shows, the action to be performed (`ADD` or `REMOVE`) and the user to be added or removed as a delegate (specified by user ID) must be included in the data parameter.

> #### 🚧 Roles and Privileges
>
> Calling this endpoint requires the ACCESS\_USER\_PROVISIONING\_API privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
