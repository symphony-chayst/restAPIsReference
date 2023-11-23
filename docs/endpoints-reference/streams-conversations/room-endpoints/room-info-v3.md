# Room Info

`Released in 1.48.`Returns information about a particular chat room.

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v3/room/{id}/info" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> 📘 Stream ID
>
> The stream ID can be located in the Symphony web or desktop client by clicking on the timestamp of any message in the conversation. This will open the Message Status module overlay, and the Conversation ID can be found in the overlay footer.
>
> The stream ID in the UI is in Standard Base64 encoding. When the stream ID needs to be used in a URL, it should be in URLSafe Base64 encoding. To obtain the URLSafe Base64 stream ID, replace forward slashes with underscores, replace pluses with minuses, and ignore any trailing equal signs.
>
> See [Overview of streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for details.

> 📘 Note - Groups
>
> Since 20.14, please note that the object `groups` has been added in the payload only if at least a Group has been added to the room. It is an array containing:
>
> * `id` attribute: ID of the Group,
> * `addedBy`: ID of the user who added the Group to the room
>
> See [Groups](ref:groups-distribution-lists) for more information.

> 🚧 Required Permissions
>
> Rooms information can only be requested by:
>
> * Members of the room
> * Compliance Officers and Super Compliance Officers who are not members of the room
> * Service Users with the User Provisioning role (members or not members of the room)
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
