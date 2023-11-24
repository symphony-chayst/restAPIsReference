# Get Connection

`Released prior to 1.43.`\
Get connection status, i.e. check if the calling user is connected to the specified user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/connection/user/{userId}/info" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> 📘 Note
>
> * When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.
> * Pods from all users involved need to have `crossPod` enabled between them.

> 📘 404 Not Found
>
> A `404 Not Found` error indicates either:
>
> * The specified user doesn’t exist.
> * The calling user and specified user are not connected because a [Create Connection](create-connection.md) request has not yet been sent.

> 📘 Internal Connections
>
> Users who belong to the same private pod are implicitly connected. Getting the connection status with an internal user will return the corresponding connection object with a status of `ACCEPTED`.

### Connection Status

Currently, there are four possible connection status:

* `PENDING_INCOMING`: The specified user requested to connect with the calling user.
* `PENDING_OUTGOING`: The calling user requested to connect with the specified user.
* `ACCEPTED`: The two users are connected.
* `REJECTED`: The two users are not connected.
