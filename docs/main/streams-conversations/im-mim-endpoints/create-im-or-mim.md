# Create IM

Creates a new instant message conversation or returns an existing IM between the specified users and the calling user.

{% hint style="info" %}
**Important**: This endpoint also allows the creation of Multi-party Instant Messages, which are not supported anymore. If you need to create a chat with several participants, please create a room instead.
{% endhint %}

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/im/create" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

* The calling user is implicitly included as a member of the instant message conversation.
* One other participant must be specified.
* If a user ID appears in the list multiple times, duplicates will be ignored.
* If there is an existing IM conversation with the specified participant, then the id of the existing stream will be returned.
* Use [Create IM or MIM non-inclusive](create-im-or-mim-admin.md) to exclude the calling user.

When calling this as an [OBO-enabled endpoint](../../apps-on-behalf-of-obo/), use the [OBO User Authenticate](../../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.

A user needs to have the entitlement `isExternalIMEnabled` if he wants to create a crosspod IM (User entitlements are set on Admin Portal).

External users must be connected with the caller before adding them.

> #### 📘 Overview of streams
>
> A stream is like a container for messages exchanged between two or more users via a given instant message (IM) or chat room. For more information, refer to [Overview of streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams).
