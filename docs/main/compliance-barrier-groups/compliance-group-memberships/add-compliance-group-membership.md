---
description: >-
  Add multiple members to a compliance group. The provided list of users will
  replace the group's current membership. Any current members not in the
  provided list will have their membership deactivated.
---

# Add Compliance Group Membership

{% swagger src="../../../.gitbook/assets/pod-api-restricted-fixed-Jan2024.yaml" path="/v2/admin/usergroups/{groupId}/memberships" method="put" %}
[pod-api-restricted-fixed-Jan2024.yaml](../../../.gitbook/assets/pod-api-restricted-fixed-Jan2024.yaml)
{% endswagger %}

> #### 🚧 Roles and Privileges
>
> Calling this endpoint requires the **Scope Management** role with the MANAGE\_ROLE\_SCOPES entitleable action.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
