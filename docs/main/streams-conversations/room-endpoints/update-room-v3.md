# Update Room

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v3/room/{id}/update" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

Returns an error when:

* The call doesn’t include an update to at least one editable attribute.
* The attribute being updated is read-only, such as \``copyProtected`. See **Attributes** below.

> #### 📘 Stream ID
>
> The stream ID can be located in the Symphony web or desktop client by clicking on the timestamp of any message in the conversation. This will open the Message Status module overlay, and the Conversation ID can be found in the overlay footer.
>
> The stream ID in the UI is in Standard Base64 encoding. When the stream ID needs to be used in a URL, it should be in URLSafe Base64 encoding. To obtain the URLSafe Base64 stream ID, replace forward slashes with underscores, replace pluses with minuses, and ignore any trailing equal signs.
>
> Note: visit [Overview of streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for more information.

> #### 🚧 Attributes
>
> * Once set to `true`, `copyProtected` cannot be set to `false`. Copy protection can be added to a room but cannot be removed.
> * The `discoverable` attribute cannot be true if crossPod is set.
> * `membersCanInvite` and `discoverable` cannot be changed for public Rooms.
> * Via the API only, the `viewHistory` attribute can be changed:
>   * either by a room owner, in any condition;
>   * or by any other member having the entitlement "Can Toggle Room's Share History Property" enabled.
> * The `pinnedMessageId` attribute allows to display an exact copy of the original message in a pinned area placed beneath the chat header and that remains always visible to all users. From this area, they can interact with the message content (i.e. forms or ui actions buttons), and they are able to automatically jump to the original message in the chat canvas. You can use this attribute as follows:
>   * either by entering the URLSafe Base 64 ID of the message you wish to pin beneath the chat header (as you can see in the example). Even if another message is pinned, this new message will replace it in the pinned area;
>   * either by entering an empty value to upin any message and remove therefore this area from being visible to users as follows: "pinnedMessageId": "";
>   * _Please note that these actions (pin/unpin) can also be performed by end users when they are owners of the room._

> #### 📘 Note - Groups
>
> Since 20.14, please note that the object `groups` has been added in the payload only if at least a Group has been added to the room. It is an array containing:
>
> * `id` attribute: ID of the Group,
> * `addedBy`: ID of the user who added the Group to the room
>
> See [Groups](ref:groups-distribution-lists) for more information.

> #### 🚧 Required Permissions
>
> Rooms can only be updated by owners of the room.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
