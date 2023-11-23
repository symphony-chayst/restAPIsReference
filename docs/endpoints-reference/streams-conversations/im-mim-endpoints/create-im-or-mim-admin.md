# Create IM or MIM non-inclusive

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/im/create" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

* At least two participants must be specified.
* If a user ID appears in the list multiple times, duplicates will be ignored.
* If there is an existing IM conversation with the specified participants, then the id of the existing stream will be returned.
* Use [Create IM or MIM](ref:create-im-or-mim) to include the calling user.

> 🚧 Required Permissions
>
> This endpoint can only be called by Service Users with the User Provisioning role.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

> 📘 Overview of streams
>
> A stream is like a container for messages exchanged between two or more users via a given instant message (IM), multi-party instant message (MIM), or chat room. For more information, refer to [Overview of streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams).
