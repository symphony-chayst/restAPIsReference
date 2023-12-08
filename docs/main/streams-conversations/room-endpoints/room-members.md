---
description: Lists the current members of an existing room.
---

# Room Members

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v2/room/{id}/membership/list" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 🚧 Required Permissions
>
> Room membership can only be read by:
>
> * Members of the room.
> * Compliance Officers and Super Compliance Officers who are not members of the room.
> * Service Users who are members of the room. If not a member, the User Provisioning role is needed.
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

> #### 📘 Room ID and User ID
>
> **Room ID**
>
> The room ID can be located in the Symphony web or desktop client by clicking on the timestamp of any message in the conversation. This will open the Message Status module overlay, and the Conversation ID can be found in the overlay footer.
>
> The room ID in the UI is in Standard Base64 encoding. When the room ID needs to be used in a URL, it should be in URLSafe Base64 encoding. To obtain the URLSafe Base64 room ID, replace forward slashes with underscores, replace pluses with minuses, and ignore any trailing equal signs.
>
> Visit [Overview](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for an overview of streams.
>
> **User ID**
>
> The user `id` returns a `long` numeric type.

> #### 📘 Note - Groups
>
> Since 20.14, please note that the object `addedThroughGroups` has been added only for members added to the room via Groups.
>
> See [Groups](../../groups-distribution-lists/) for more information.
