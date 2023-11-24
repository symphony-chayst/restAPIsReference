---
description: >-
  Released prior to 1.43. Updates all the application entitlements for a
  particular user.
---

# Update All User Apps

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{uid}/app/entitlement/list" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

As shown in the example, the updated user application entitlements should be included in the data parameter.

> ### ❗️ Important
>
> Please, consider the following information before using this endpoint:
>
> The endpoint is designed to update all app entitlements of a user using a single API call.\
> It is not meant to modify one single entitlement for a user.
>
> However, it is possible to do this using the Patch [Update User Apps](ref:partial-update-user-apps) endpoint.
