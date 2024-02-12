---
description: List assignments of a compliance group. Released in 1.55.3
---

# List Assignments

{% swagger src="../../../.gitbook/assets/pod-api-restricted-fixed-Jan2024.yaml" path="/v2/admin/usergroups/{groupId}/assignments" method="get" %}
[pod-api-restricted-fixed-Jan2024.yaml](../../../.gitbook/assets/pod-api-restricted-fixed-Jan2024.yaml)
{% endswagger %}

> #### 🚧 Roles and Privileges
>
> Calling this endpoint requires the **Scope Management** role with the VIEW\_ROLE\_SCOPES entitleable action.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

> #### 📘 Note
>
> Certain types of groups support assignment to specific users, which is different from group membership. Assignment of a group can be likened to the assignment of responsibility for that group of users, which will have a different meaning depending on the type of the group.\
> Group assignment is only available for groups of certain types.
>
> Query parameter `limit`: A query may return fewer than the value of limit due to filtering or service-side maximums. Do not depend on the number of results being fewer than the limit value to indicate your query reached the end of the list of data, use the absence of next instead.\
> For example, if you set the limit to 10 and only 9 results are returned, there may be more data available, but one item was removed due to privacy filtering. Some maximums for limit may be enforced for performance reasons.
