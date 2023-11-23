# Remove Member

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/room/{id}/membership/remove" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> 🚧 Rules and limitations
>
> * Currently, it is possible to remove all members from a room, however, this action is not recommended since the removal of all members leaves the room in an unrecoverable state. At any time, a room should have at least one owner.
> * It is not possible to remove members from deactivated rooms.

> 🚧 Required Permissions
>
> New room members can only be removed by:
>
> * Owners of the room
> * Compliance Officers and Super Compliance Officers who are not members of the room
> * Service Users with the User Provisioning role (members or not members of the room)
>
> Note: The service user can always remove itself from the room without the need for a particular permission.
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

**Jumbo Chat Rooms**

When creating or deconstructing jumbo rooms (i.e. more than 1,000 members) in one bulk load, please be advised of the following:

1. Members should be added/deleted 1 member every "3 seconds" to allow key management functions time to process.
2. Members should be added out of working hours (best is during weekend maintenance)
3. Ensure at least 2 room owners are created (for room management backup purposes)

Please note, the maximum number of members that can be added to a room is dependent on your service type (i.e. Business or Enterprise Tier). ​ Please notify Symphony Support when creating Jumbo Chat Rooms and our team will advise on maximum room size and monitor your launch.
