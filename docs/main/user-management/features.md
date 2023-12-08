# User Features

Returns the list of Symphony feature entitlements for a particular user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{uid}/features" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

Use the data returned from this endpoint with [Find Users](find-users.md) to filter users by a specific entitlement.

> #### 🚧 Required Permissions
>
> Calling this endpoint requires the User Provisioning role with ACCESS\_USER\_PROVISIONING\_API privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
