# Stream Members

Returns a list of all the current members of a stream (IM or chatroom).

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/stream/{id}/membership/list" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

Note: visit [Overview](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for an overview of streams.

> #### 🚧 Required Permissions
>
> To get the stream membership of any stream in your enterprise, you should call this endpoint with a Service User account with the User Provisioning role. The Service User does not need to be a member of the stream.
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

> #### 📘 External users
>
> If you call this endpoint with a user that has the User Provisioning role, you will get the email address for both internal and external users.

> #### 📘 Creation and Ownership
>
> The `isCreator` field is relevant to IMs and chatrooms. For an IM, this is the person who initiated the first chat with the other user(s).
>
> The `isOwner` field is relevant only to chatrooms. It denotes whether the user is an owner of the chatroom. While a room can only have one creator, it can have multiple owners.

> #### 📘 Join Date
>
> The `joinDate` field is most relevant for chatrooms. It represents the time the user was added to the chatroom. If a user was added, removed, and then added back to the room, the `joinDate` reflects the most recent add date.
>
> In the case of IMs and MIMs, the `joinDate` reflects the initiation date of the conversation. Every member will have the same `joinDate`.

> #### 📘 Note - Groups
>
> Since 20.14, please note that the object `addedThroughGroups` has been added only for members added to the room via Groups.
>
> See [Groups](../../groups-distribution-lists/) for more information.
