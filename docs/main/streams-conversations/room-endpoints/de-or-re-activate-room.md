# De/Re-activate Room

Deactivate or reactivate a chatroom. At creation, a new chatroom is active.

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/room/{id}/setActive" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 🚧 Rules and limitations
>
> Only rooms with members can be reactivated

> #### 📘 Room ID
>
> The room ID can be located in the Symphony web or desktop client by clicking on the timestamp of any message in the conversation. This will open the Message Status module overlay, and the Conversation ID can be found in the overlay footer.
>
> The room ID in the UI is in Standard Base64 encoding. When the room ID needs to be used in a URL, it should be in URLSafe Base64 encoding. To obtain the URLSafe Base64 room ID, replace forward slashes with underscores, replace pluses with minuses, and ignore any trailing equal signs.
>
> See [Overview of Streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for details.

> #### 🚧 Required Permissions
>
> **External Rooms that have not been created by your company cannot be de/re-activated.**\
> Rooms can only be de/re-activated by:
>
> * Owners of the room
> * Compliance Officers and Super Compliance Officers who are not members of the room
> * Service Users with the User Provisioning role (members or not members of the room)
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
