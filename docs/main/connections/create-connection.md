# Create Connection

`Released prior to 1.43.`\
Sends a connection request to another user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/connection/create" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> 📘 Internal Connections
>
> Users who belong to the same private pod are implicitly connected. If you attempt to connect with an internal user, this endpoint will return the corresponding connection object with a status of `accepted`.

> 📘 Note
>
> * When calling this as an [OBO-enabled endpoint](ref:obo-enabled-endpoints), use the [OBO User Authenticate](ref:obo-user-authenticate) token for `sessionToken`.
> * Pods from all users involved need to have `crossPod` enabled between them.
> * Only one connection request is allowed between two users. When this limit is exceeded, no more connections requests are allowed. A new connection request will be allowed only if the user that received the connection request declines it.

### Connection Behaviour

Currently, there are four possible connection status:

* PENDING\_INCOMING: The specified user requested to connect with the calling user.
* PENDING\_OUTGOING: The calling user requested to connect with the specified user.
* ACCEPTED: The two users are connected.
* REJECTED: The two users are not connected.

The following table shows the connection current behaviors:

| Initial Connection Status       | Request Action | New Connection Status |
| ------------------------------- | -------------- | --------------------- |
| None (connection did not exist) | Connect        | PENDING\_OUTGOING     |
| PENDING\_INCOMING               | Accept         | ACCEPTED              |
| PENDING\_INCOMING               | Reject         | REJECTED              |
