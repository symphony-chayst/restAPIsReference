# Create IM or MIM

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/im/create" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

* The calling user is implicitly included as a member of the instant message conversation.
* At least one other participant must be specified.
* If a user ID appears in the list multiple times, duplicates will be ignored.
* If there is an existing IM conversation with the specified participants, then the id of the existing stream will be returned.
* Use [Create IM or MIM non-inclusive](ref:create-im-or-mim-admin) to exclude the calling user.

When calling this as an [OBO-enabled endpoint](ref:obo-enabled-endpoints), use the [OBO User Authenticate](ref:obo-user-authenticate) token for `sessionToken`.

A user needs to have the entitlement `isExternalIMEnabled` if he wants to create a crosspod IM/MIM (User entitlements are set on Admin Portal).

All external users must be connected with the caller before adding them.

> 📘 Overview of streams
>
> A stream is like a container for messages exchanged between two or more users via a given instant message (IM), multi-party instant message (MIM), or chat room. For more information, refer to [Overview of streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams).
