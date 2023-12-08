---
description: Returns details for a particular user.
---

# Get User

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v2/admin/user/{uid}" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 📘 Note - Suspension
>
> Since 20.14, `userSystemInfo` from the payload includes suspension info:
>
> * if user is active, then the `suspended` attribute is set to false,
> * if user is suspended, then the `suspended` attribute is set to true and both `suspendedUntil` and `suspensionReason` are as well included in the payload.
>
> _Please note that even if the suspendedUntil date is in the past, the user will remain suspended=true until he first logs on the client after the suspension ended. The suspended info are then automatically updated._\
> See the [Suspend User Account](suspend-user-v1.md) endpoint for more information.

See [End-User Account Attributes V2](user-attributes.md#end-user-account-attributes-v2) for information about the user attributes.

> #### 🚧 Roles and Privileges
>
> Calling this endpoint requires the ACCESS\_USER\_PROVISIONING\_API and ACCESS\_ADMIN\_API privileges.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
