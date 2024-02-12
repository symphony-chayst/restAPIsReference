---
description: List compliance user groups matching a set of filters. Released in 1.55.3
---

# List Compliance User Groups

{% swagger src="../../../.gitbook/assets/pod-api-restricted-fixed-Jan2024.yaml" path="/v2/admin/usergroups" method="get" %}
[pod-api-restricted-fixed-Jan2024.yaml](../../../.gitbook/assets/pod-api-restricted-fixed-Jan2024.yaml)
{% endswagger %}

> #### 🚧 Scoping groups
>
> Scoping groups are used to manage the set of users and conversations that Compliance Officers or Super Compliance Officers have access to.

> #### 📘 Note
>
> A compliance group must exactly match all of the specified query parameters to be included in the results.

> #### 🚧 Roles and Privileges
>
> Calling this endpoint requires the **Scope Management** role with the VIEW\_ROLE\_SCOPES entitleable action.\
> See [Bot Permissions](https://docs.developers.symphony.com/bots/overview-of-rest-api/bot-permissions) for a list of roles and associated privileges.
