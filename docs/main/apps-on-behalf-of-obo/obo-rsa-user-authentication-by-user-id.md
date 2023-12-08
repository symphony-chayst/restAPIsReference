---
description: Enables an RSA application to authenticate on behalf of a particular user.
---

# User Authentication by User ID

{% swagger src="../../.gitbook/assets/login-api-public.yaml" path="/pubkey/app/user/{userId}/authenticate" method="post" expanded="true" fullWidth="true" %}
[login-api-public.yaml](../../.gitbook/assets/login-api-public.yaml)
{% endswagger %}

> #### 📘 Requirements
>
> The app must have been created on the pod.\
> The app must be enabled.\
> The user must exist and have the app installed. For more information, refer to [Update user Apps](../apps-entitlements/partial-update-user-apps.md).
