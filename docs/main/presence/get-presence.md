---
description: Returns the online status of the calling user.
---

# Get Presence

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v2/user/presence" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.

The available online status values (presence categories) for users are:

| Presence category | Interface icon   | External view   | Comment             |
| ----------------- | ---------------- | --------------- | ------------------- |
| `AVAILABLE`       | Green check mark | `AVAILABLE`     | Released in 1.46    |
| `AWAY`            | Yellow clock     | `AWAY`          | Released in 1.46    |
| `OFFLINE`         | Grey cross       | `OFFLINE`       | Introduced in 20.16 |
| `BUSY`            | Red sign         | `BUSY`          | Released in 1.46    |
| `ON_THE_PHONE`    | Red phone        | `ON_THE_PHONE`  | Released in 1.46    |
| `BE_RIGHT_BACK`   | Yellow clock     | `AWAY`          | Released in 1.47    |
| `IN_A_MEETING`    | Red phone        | `IN_A_MEETING`  | Released in 1.47    |
| `OUT_OF_OFFICE`   | Purple circle    | `OUT_OF_OFFICE` | Released in 1.47    |
| `OFF_WORK`        | Yellow clock     | `OFFLINE`       | Deprecated in 20.16 |
| `DO_NOT_DISTURB`  | Red circle       | `AWAY`          | Deprecated in 20.16 |

See [Set Presence](set-presence.md) for a description of the **Presence category** and **External view** values for internal and external users.

**Note**: It is also possible for Symphony users to have other presence values, which should be handled in your implementation as edge cases.
