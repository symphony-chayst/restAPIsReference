# Demote Owner

Demotes room owner to a participant in the chat room.

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/room/{id}/membership/demoteOwner" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 📘 Room ID
>
> The room ID can be located in the Symphony web or desktop client by clicking on the timestamp of any message in the conversation. This will open the Message Status module overlay, and the Conversation ID can be found in the overlay footer.
>
> The room ID in the UI is in Standard Base64 encoding. When the room ID needs to be used in a URL, it should be in URLSafe Base64 encoding. To obtain the URLSafe Base64 room ID, replace forward slashes with underscores, replace pluses with minuses, and ignore any trailing equal signs.
>
> Note: visit [Overview](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for an overview of streams.

> #### 🚧 Required Permissions
>
> Room members can only be demoted to participants by:
>
> * Owners of the room
> * Service Users with the User Provisioning role (members or not members of the room)
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

At any time, a room must have at least one owner; therefore, it is not possible to demote the last owner of a room.
