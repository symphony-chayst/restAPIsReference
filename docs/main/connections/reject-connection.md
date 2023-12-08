# Reject Connection

Accept the connection request from a requesting user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/connection/reject" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

This endpoint allows the user to reject a specific connection request. To define which connection request is to be rejected, the `userId` of the user who initiated the connection request must be included in the body.

Pods from all users involved need to have `crossPod` enabled between them.

> #### 📘 Rejected Connections
>
> Reject the connection between the requesting user and request sender. If both users are in the same private pod, an error will be returned because both users have an implicit connection which cannot be rejected.

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
