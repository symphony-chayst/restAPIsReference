# Accept Connection

`Released prior to 1.43.`\
Accept the connection request from a requesting user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/connection/accept" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

This endpoint allows the user to accept a specific connection request. To define which connection request is to be accepted, the `userId` of the user who initiated the connection request must be included in the body.

> 📘 Note
>
> Pods from all users involved need to have `crossPod` enabled between them.

> 📘 Accepted Connections
>
> For users of the same private pod who are implicitly connected, this endpoint returns the connection with status of "Accepted".

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
