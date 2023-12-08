# Set Presence

Sets the online status of the calling user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v2/user/presence" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.

The available online status values (presence categories) for users are are available in [Get Presence](get-presence.md)

> #### 📘 Idle state
>
> When the end-user is idle on the Symphony clients and either in `AVAILABLE` or `BUSY` categories, the online status of the user is automatically changed to `AWAY`. When the user is active again on the client, then the online status is automatically changed back to the prior category.

> #### 🚧 Roles and Privileges
>
> Calling this endpoint requires the ADMIN\_PRESENCE\_UPDATE privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
