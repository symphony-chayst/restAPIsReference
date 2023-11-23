# Room Attributes

The following attributes apply to these Room endpoints:

* [Create Room](ref:create-room-v3)
* [Update Room](ref:update-room-v3)
* [Room Info](ref:room-info-v3)
* [Search Rooms](ref:search-rooms-v3)

<table><thead><tr><th width="190">Name</th><th width="116">Type</th><th>Description</th></tr></thead><tbody><tr><td>name</td><td>string</td><td>Room name</td></tr><tr><td>description</td><td>string</td><td>Room description</td></tr><tr><td>keywords</td><td>array</td><td>A list of key-value pairs, describing additional properties of the room. It is possible to search rooms by keyword values using the <a href="ref:search-rooms-v3">Search Rooms</a> endpoint.</td></tr><tr><td>membersCanInvite</td><td>boolean</td><td>If <strong>true</strong>, any chat room participant can add new participants. <br>If <strong>false</strong>, only owners can add new participants.</td></tr><tr><td>discoverable</td><td>boolean</td><td>If <strong>true</strong>, this chat room (name, description and messages) non-participants can search for this room. If <strong>false</strong>, only participants can search for this room.</td></tr><tr><td>public</td><td>boolean</td><td>If <strong>true</strong>, this is a public chatroom and anyone can join. If <strong>false</strong>, this is a private chatroom and participants must be added.</td></tr><tr><td>readOnly</td><td>boolean</td><td>If <strong>true</strong>, only room owners can send messages.</td></tr><tr><td>copyProtected</td><td>boolean</td><td>If <strong>true</strong>, users cannot copy content from this room.</td></tr><tr><td>crossPod</td><td>boolean</td><td>If <strong>true</strong>, this room is a cross pod room.</td></tr><tr><td>viewHistory</td><td>boolean</td><td>If <strong>true</strong>, new members can view the room chat history of the room.</td></tr><tr><td>multiLateralRoom</td><td>boolean</td><td>If <strong>true</strong>, this is a multilateral room where users belonging to more than two companies can be found.</td></tr><tr><td>pinnedMessageId</td><td>string</td><td><a href="https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml#message-identifiers">URLSafe Base64</a> ID of the pinned message.</td></tr></tbody></table>

> 🚧 Copy Protection
>
> Once set to `true`, `copyProtected` cannot be set to `false`. Copy protection can be added to a room but cannot be removed.

> 📘 Overview of streams
>
> A stream is like a container for messages exchanged between two or more users via a given instant message (IM), multi-party instant message (MIM), or chat room. For more information, refer to [Overview of streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams).
