---
description: Accept the connection request from a requesting user.
---

# Accept Connection

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/connection/accept" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

This endpoint allows the user to accept a specific connection request. To define which connection request is to be accepted, the `userId` of the user who initiated the connection request must be included in the body.

> #### 📘 Note
>
> Pods from all users involved need to have `crossPod` enabled between them.

> #### 📘 Accepted Connections
>
> For users of the same private pod who are implicitly connected, this endpoint returns the connection with status of "Accepted".

### Connection Behaviour

Currently, there are four possible connection status:

* PENDING\_INCOMING: The specified user requested to connect with the calling user.
* PENDING\_OUTGOING: The calling user requested to connect with the specified user.
* ACCEPTED: The two users are connected.
* REJECTED: The two users are not connected.

The following table shows the connection current behaviors:

<table><thead><tr><th width="324.3333333333333">Initial Connection Status</th><th>Request Action</th><th>New Connection Status</th></tr></thead><tbody><tr><td>None (connection did not exist)</td><td>Connect</td><td>PENDING_OUTGOING</td></tr><tr><td>PENDING_INCOMING</td><td>Accept</td><td>ACCEPTED</td></tr><tr><td>PENDING_INCOMING</td><td>Reject</td><td>REJECTED</td></tr></tbody></table>
