---
description: >-
  To get the presence state of external users, you must first register interest
  in those users using this endpoint.
---

# External Presence Interest

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/user/presence/register" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

### Request Example

```bash
curl -X POST \
  https://acme.symphony.com/pod/v1/user/presence/register \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/json' \
  -H 'sessiontoken: SESSION_TOKEN' \
  -d '[7215545078541, 7215545078461]'
```

When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.

### Querying Presence of External Users

> #### 📘 External Users Presence Visibility
>
> Any user can see the presence of other users of the same company. For users of a different company, the two users must be connected to see presence.

To query the presence of external users:

1. Call this endpoint to register interest in the desired users.
2. Call the [Get User Presence](user-presence-v3.md) endpoint to query the presence of each user.\
   To keep the registration active, call this endpoint every hour.

To query the presence of internal users, you do not need to register interest.

> #### ❗️ Rate Limit
>
> Getting an external user’s presence is limited to one call every 5 minutes.

> #### 🚧 Roles and Privileges
>
> Calling this endpoint requires the ADMIN\_PRESENCE\_UPDATE privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
