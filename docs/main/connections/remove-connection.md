---
description: Removes a connection with a user.
---

# Remove Connection

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/connection/user/{uid}/remove" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 📘 Note
>
> Pods from all users involved need to have `crossPod` enabled between them.

> #### 📘 HTTP 400
>
> This endpoint returns **400 Bad Request** when the users are not connected. For example, when a user has not yet accepted a connection request from another user.

### Connection Behaviour

Currently, there are four possible connection status:

* PENDING\_INCOMING: The specified user requested to connect with the calling user.
* PENDING\_OUTGOING: The calling user requested to connect with the specified user.
* ACCEPTED: The two users are connected.
* REJECTED: The two users are not connected.

The following table shows the connection current behaviors:

| Initial Connection Status | Request Action | New Connection Status                 |
| ------------------------- | -------------- | ------------------------------------- |
| ACCEPTED                  | Remove         | None (the connection no longer exist) |
| PENDING\_INCOMING         | Remove         | REJECTED                              |
| REJECTED                  | Remove         | PENDING\_INCOMING                     |
