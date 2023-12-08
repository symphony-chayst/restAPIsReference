# Create Connection

Sends a connection request to another user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/connection/create" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 📘 Internal Connections
>
> Users who belong to the same private pod are implicitly connected. If you attempt to connect with an internal user, this endpoint will return the corresponding connection object with a status of `accepted`.

> #### 📘 Note
>
> * When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.
> * Pods from all users involved need to have `crossPod` enabled between them.
> * Only one connection request is allowed between two users. When this limit is exceeded, no more connections requests are allowed. A new connection request will be allowed only if the user that received the connection request declines it.

### Connection Behaviour

Currently, there are four possible connection status:

* PENDING\_INCOMING: The specified user requested to connect with the calling user.
* PENDING\_OUTGOING: The calling user requested to connect with the specified user.
* ACCEPTED: The two users are connected.
* REJECTED: The two users are not connected.

The following table shows the connection current behaviors:

<table><thead><tr><th width="301.3333333333333">Initial Connection Status</th><th>Request Action</th><th>New Connection Status</th></tr></thead><tbody><tr><td>None (connection did not exist)</td><td>Connect</td><td>PENDING_OUTGOING</td></tr><tr><td>PENDING_INCOMING</td><td>Accept</td><td>ACCEPTED</td></tr><tr><td>PENDING_INCOMING</td><td>Reject</td><td>REJECTED</td></tr></tbody></table>
