---
description: List all current connection statuses with external or specified users.
---

# List Connection

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/connection/list" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

This endpoint retrieves all connections of the requesting user. (i.e. both connections in which the requesting user is the sender and those in which the requesting user is the invitee). By default, if you have not specified the connection status to filter on, this call will only return results for both PENDING\_INCOMING and PENDING\_OUTGOING. You can optionally filter by userIds to further restrict the results of a specific connection status. If the users are in the same private pod, the users have an implicit connection status of ACCEPTED. Those users will not be returned in the response if you do not specify the connection status as ACCEPTED (default is "pending") and the explicit userIds in the request.

> #### 📘 Note
>
> * When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.
> * Pods from all users involved need to have `crossPod` enabled between them.

### Connection Status

Currently, there are four possible connection status:

* PENDING\_INCOMING: The specified user requested to connect with the calling user.
* PENDING\_OUTGOING: The calling user requested to connect with the specified user.
* ACCEPTED: The two users are connected.
* REJECTED: The two users are not connected.
