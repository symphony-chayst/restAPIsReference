---
description: Add members to an Information Barrier group.
---

# Add IB Group Members

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/group/{gid}/membership/add" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

As the example shows, the users to be added to the Information Barrier group (specified as a list of user IDs) must be included in the data parameter.

> #### 🚧 Roles and Privileges
>
> Calling this endpoint requires the ACCESS\_USER\_PROVISIONING\_API privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

Note: The underlying call to add the user ID is synchronous, adding a large number of ID to an Information Barrier group may result in a long wait for this call to return.\
The maximum number of user IDs that can be passed in one call is conditioned by the size of that parameter: Maximum 2Mb.
