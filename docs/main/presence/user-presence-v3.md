---
description: Returns the online status of the specified user.
---

# Get User Presence

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v3/user/{uid}/presence" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

The `timestamp` in the response is in UTC format and contains the time when the presence was set using [Set Presence](set-presence.md). For users who are offline, the `timestamp` contains the current time when the Get User Presence endpoint was invoked.

To get the presence of external users, you must first [register interest](register-user-presence-interest.md) about their presence.

When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.

The available online status values (presence categories) for users are listed on the [Get Presence](get-presence.md) page.

### Query Presence of External Users

To query the presence of external users, you must first perform an additional step:

1. Call the [Register Interest in External User Presence](register-user-presence-interest.md) endpoint to register interest in those users.
2. Call this endpoint to query the presence of each user.

To query the presence of internal users, you do not need to register interest and can call this endpoint directly.
