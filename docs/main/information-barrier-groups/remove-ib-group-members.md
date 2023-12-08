---
description: Remove members from an Information Barrier group.
---

# Remove IB Group Members

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/group/{gid}/membership/remove" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

As the example shows, the users to be removed from the Information Barrier group (specified as a list of user IDs) must be included in the data parameter.

> #### ❗️ Known Limitation
>
> It is currently not possible to remove a deactivated user from an IB group via the API. Please use the Admin Portal if you wish to do this.

> #### 🚧 Roles and Privileges
>
> Calling this endpoint requires the ACCESS\_USER\_PROVISIONING\_API privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
