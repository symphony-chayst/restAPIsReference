---
description: >-
  Creates a new instant message conversation or returns an existing IM between
  the specified users, but excluding the calling user.
---

# Create IM non-inclusive

{% hint style="info" %}
**Important**: This endpoint also allows the creation of Multi-party Instant Messages, which are not supported anymore. If you need to create a chat with several participants, please create a room instead.
{% endhint %}

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/im/create" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

* Two participants must be specified.
* If a user ID appears in the list multiple times, duplicates will be ignored.
* If there is an existing IM conversation with the specified participants, then the id of the existing stream will be returned.
* Use [Create IM or MIM](create-im-or-mim.md) to include the calling user.

> #### 🚧 Required Permissions
>
> This endpoint can only be called by Service Users with the User Provisioning role.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

> #### 📘 Overview of streams
>
> A stream is like a container for messages exchanged between two or more users via a given instant message (IM) or chat room. For more information, refer to [Overview of streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams).
