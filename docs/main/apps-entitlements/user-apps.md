---
description: Returns the list of Symphony application entitlements for this user.
---

# List User Apps

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{uid}/app/entitlement/list" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 🚧 Important
>
> This endpoint returns all enabled entitlements for a specific user, returning both the global and the custom settings.\
> Currently, it is not possible to identify by API response whether the returned entitlements are global or custom.
>
> To know more about how to modify an app entitlement per user, and how to reset the app entitlements for that user to the default global settings, refer to [Update User Apps](partial-update-user-apps.md)
