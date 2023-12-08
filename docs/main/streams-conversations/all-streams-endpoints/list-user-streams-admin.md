---
description: >-
  Returns a list of all the streams of which the specified user is a member,
  sorted by creation date (ascending - oldest to newest).
---

# List User Streams (Admin)

`Released in 20.16.`&#x20;

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{uid}/streams/list" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 🚧 Required Permissions
>
> Only service users with the User Provisioning role can use this endpoint.

> #### 📘 Overview of streams
>
> A stream is like a container for messages exchanged between two or more users via a given instant message (IM) or chat room. For more information, refer to [Overview of streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams).
