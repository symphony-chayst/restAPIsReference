# Update User Status

Released prior to 1.43. Update the status of a particular user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{uid}/status/update" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> 📘 Note
>
> It is not possible to disable protected service users (keymanager and ceservice)

> 🚧 Required Permissions
>
> Calling this endpoint requires the User Provisioning role with `ACCESS_USER_PROVISIONING_API` privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
