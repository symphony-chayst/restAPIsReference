---
description: Filters and lists compliance group memberships for a user. Released in 1.55.3
---

# List Compliance Group Memberships



{% swagger src="../../../.gitbook/assets/pod-api-restricted-fixed-Jan2024.yaml" path="/v2/admin/users/{userId}/groupmemberships" method="get" %}
[pod-api-restricted-fixed-Jan2024.yaml](../../../.gitbook/assets/pod-api-restricted-fixed-Jan2024.yaml)
{% endswagger %}

> #### 🚧 Roles and Privileges
>
> Calling this endpoint requires the **Scope Management** role.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

> #### 📘 Note
>
> `limit` query parameter: A query may return fewer than the value of limit due to filtering or service-side maximums. Do not depend on the number of results being fewer than the limit value to indicate your query reached the end of the list of data, use the absence of next instead as described in the following example:\
> If you set `limit` to 10 and only 9 results are returned, there may be more data available, but one item was removed due to privacy filtering. Some maximums for limit may be enforced for performance reasons.
>
> `sort` query parameter: if the name of the field is preceded by a "-", then the results will be returned in descending order, otherwise results will be returned in ascending order. For example, a sort param value of "-name" would return results sorted by the "name" field in descending order, while a value of "name" would return results sorted by the "name" field in ascending order.\
> The fields available for sorting are "lastAddedDate" and "lastRemovedDate".
