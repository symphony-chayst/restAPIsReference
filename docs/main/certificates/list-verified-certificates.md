---
description: >-
  Return a list of all certificates that are verified to a specified
  fingerprint.
---

# List Verified Certificates

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/companycert/{fingerPrint}/issuedBy" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 🚧 Roles and privilges
>
> Calling this endpoint requires the USER\_PROVISIONING or the SUPER\_ADMINISTRATOR role.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
