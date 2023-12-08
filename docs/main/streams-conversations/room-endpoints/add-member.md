# Add Member

Adds a new member to an existing room.

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/room/{id}/membership/add" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 📘 Room ID
>
> The room ID can be located in the Symphony web or desktop client by clicking on the timestamp of any message in the conversation. This will open the Message Status module overlay, and the Conversation ID can be found in the overlay footer.
>
> The room ID in the UI is in Standard Base64 encoding. When the room ID needs to be used in a URL, it should be in URLSafe Base64 encoding. To obtain the URLSafe Base64 room ID, replace forward slashes with underscores, replace pluses with minuses, and ignore any trailing equal signs.
>
> See [Overview of Streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for details.

> #### 🚧 Rules and limitations
>
> * **Joining Public Rooms:** this endpoint can be used by the calling user to join a public room. To do so, specify the ID of the public room the user wishes to join in the URL and specify the user ID of the calling user in the body.
>   * New members cannot be added to deactivated rooms.
>   * For rooms with more than 500 users, members should be added/deleted 1 member every "3 seconds" to allow key management functions time to process.

> #### 🚧 Required Permissions
>
> New room members can only be added by:
>
> * Owners of the room
> * Members of the room (if “Let participants add members” has been specified in Room Preferences)
> * Compliance Officers and Super Compliance Officers who are not members of the room
> * Service Users with the User Provisioning role who are not members of the room
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

**Jumbo Chat Rooms**

When creating or deconstructing jumbo rooms (i.e. more than 1000 members) in one bulk load, please be advised of the following:

1. Ensure that a member will be added/deleted every "3 seconds".
2. Members should be added out of working hours (best is during weekend maintenance).
3. Ensure at least 2 room owners are created (for room management backup purposes).

Please note, the maximum number of members that can be added to a room is dependent on your service type (i.e. Business or Enterprise Tier). ​ Please notify Symphony Support when creating Jumbo Chat Rooms and our team will advise on maximum room size and monitor your launch.
