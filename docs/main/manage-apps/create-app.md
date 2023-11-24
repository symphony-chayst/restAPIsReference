---
description: Creates a new application.
---

# Create App

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/app/create" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

Please note to use either:

* `cert` attribute when using a certificate
* or `authenticationKeys` object when using RSA Public Key

> ### 🚧 Roles and Privileges
>
> Calling this endpoint requires the Super Administrator or User Provisioning role.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

> ### 📘 RSA Application Authentication
>
> For more information on how to authenticate an application using RSA, refer to [App Authentication](https://docs.developers.symphony.com/building-extension-applications-on-symphony/app-authentication).
