# Set Other User's Presence - Admin

Sets the presence state of a another user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v3/user/presence" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 🚧 User role requirement
>
> To set the presence of another user, this endpoint requires to be called by a service user with the "User Provisioning" Entitlement.
