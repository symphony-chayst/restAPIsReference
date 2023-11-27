---
description: >-
  Released in SBE 20.13. Updates the application entitlements for a particular
  user. Supports partial update.
---

# Update User Apps

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{uid}/app/entitlement/list" method="patch" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

As shown in the example, the updated user application entitlements should be included in the data parameter.

> ### 📘 Info
>
> Unlike [Update All User Apps](update-user-apps.md) endpoint, it is not mandatory to provide in the body request all app entitlements for a given app.\
> You can therefore update only one or several of them among the following body params: "install", "listed", or "products".
>
> The "product" field is not required but cannot be set to "null". When provided, please specify all subfields specified such as in the example: "appId", "subscribed", "type", "sku", and "name".
