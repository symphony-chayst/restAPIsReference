# Update User Avatar

Released prior to 1.43. Updates the avatar of a particular user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{uid}/avatar/update" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> 📘 Note
>
> This API also allows the current user to update his own avatar.

> 🚧 Required Permissions
>
> Calling this endpoint requires the User Provisioning role with `ACCESS_USER_PROVISIONING_API` privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
