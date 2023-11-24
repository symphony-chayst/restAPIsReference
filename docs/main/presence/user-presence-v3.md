# Get User Presence

`Released in 1.47.`\
Returns the online status of the specified user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v3/user/{uid}/presence" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

The `timestamp` in the response is in UTC format and contains the time when the presence was set using [Set Presence](ref:set-presence). For users who are offline, the `timestamp` contains the current time when the Get User Presence endpoint was invoked.

To get the presence of external users, you must first [register interest](ref:register-user-presence-interest) about their presence.

When calling this as an [OBO-enabled endpoint](ref:obo-enabled-endpoints), use the [OBO User Authenticate](ref:obo-user-authenticate) token for `sessionToken`.

The available online status values (presence categories) for users are listed on the [Get Presence](ref:get-presence) page.

### Query Presence of External Users

To query the presence of external users, you must first perform an additional step:

1. Call the [Register Interest in External User Presence](ref:register-user-presence-interest) endpoint to register interest in those users.
2. Call this endpoint to query the presence of each user.

To query the presence of internal users, you do not need to register interest and can call this endpoint directly.
