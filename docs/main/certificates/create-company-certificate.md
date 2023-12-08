---
description: Create a company trusted or untrusted certificate
---

# Create Company Certificate

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v2/companycert/create" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 📘 Note
>
> This v2 endpoint rejects expired certificates. When creating company certificates, make sure that you are calling the v2 version of this endpoint, and not v1.

> #### 🚧 Roles and privileges
>
> Calling this endpoint requires the USER\_PROVISIONING or the SUPER\_ADMINISTRATOR role.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
