---
description: Creates a new chatroom. See Room Attributes for room creation parameters.
---

# Create Room

`Starting with SBE 20.14, it is possible to create External chat rooms with view history enabled, depending on a pod parameter.`

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v3/room/create" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

_Starting with SBE 20.14, it is possible to create External chat rooms with view history enabled, depending on a pod parameter. See_ [_Room Attributes_](room-attributes-1.md) _for room creation parameters._

> #### 🚧 More Information
>
> * Room names will be considered the same if they only differ in capitalization and whitespace. E.g. "room1" and "R O O M 1" are considered the same. Also, room names must be shorter than 50 characters.
> * `viewHistory`, `discoverable` and `membersCanInvite` attributes cannot be _false_ if `public=true`.
> * `readOnly`, `public` and `discoverable` attributes cannot be _true_ if `crossPod=true`.
> * When 'crossPod' is true, then `viewHistory` can be true ONLY if the pod entitlement canCreateExternalRoomSharedHistory is enabled.

> #### 📘 Overview of streams
>
> A stream is like a container for messages exchanged between two or more users via a given instant message (IM) or chat room. For more information, refer to [Overview of streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams).

> #### 🚧 Entitlements
>
> * A user needs to have the entitlement `canCreatePublicRoom` if he wants to create a public room (User entitlements are set on Admin Portal).
> * A user needs to have the entitlement `isExternalRoomEnabled` if he wants to create a crosspod room (User entitlements are set on Admin Portal).

