# Stream Info

`Released in 1.51.`

Returns information about a particular stream.

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v2/streams/{sid}/info" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

Note: visit [Overview](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for an overview of streams.

In the response,

* The `crossPod` field indicates whether the stream is External or Internal.
* The `origin` field indicates the origin of the room: INTERNAL (created by a user of the calling user's company) or EXTERNAL (created by a user of another company). Only applies to chatrooms with External scope.
* The `active` field indicates whether the stream is active or inactive. An IM/MIM is inactive if at least one of the participants is a deactivated user. A room is inactive if it has been deactivated by an owner or an administrator.
* `lastMessageDate` states when the last message sent in that stream. The time is in epoch format.
* `streamType` can be `IM` (1-1 instant message), `MIM` (multi-party instant message), `ROOM`, or `POST` (user profile wall posts).
* For IMs, MIMs, and walls, `streamAttributes` contains the `members` array with userIds of participants. In the case of wall posts, there is only one participant (the user whose wall it is).
* For rooms, `roomAttributes` contains the `name` of the room. To get the participants of the room, call the [Room Members](stream-members.md) endpoint.
* If the stream is IM/MIM or rooms with `discoverable`set as "false", the caller needs to have the VIEW\_ANY\_STREAM\_DETAILS privilege. Refer to [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

> 📘 Note - Groups
>
> Since 20.14, please note that the object `groups` has been added in the roomAttributes object only if at least a Group has been added to the room. It is an array containing:
>
> * `id` attribute: ID of the Group,
> * `addedBy`: ID of the user who added the Group to the room
>
> See [Groups](../../groups-distribution-lists/) for more information.
