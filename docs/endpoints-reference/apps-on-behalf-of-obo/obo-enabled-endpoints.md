# API Endpoints for Apps

### Get Started with OBO

OBO or On-Behalf-Of authentication allows an extension application to be able to call REST API endpoints to perform operations on behalf of an application end-user.

Such operations include:

* List the streams of a given user
* Initiate connection requests to and determine connection status with other users
* Get the presence state of other connected users
* Initiate IMs and MIMs with other users
* Send messages and attachments
* Set the context user's own presence

> 📘 More information on OBO
>
> For more information, please refer to [OBO Authentication](https://docs.developers.symphony.com/building-extension-applications-on-symphony/app-authentication/obo-authentication).

## API endpoints enabled for OBO

The following table describes which of our REST API endpoints are OBO-enabled, and for each the application permission that must be granted to the app.

| OBO-enabled endpoint                                       | Permission                                  | Endpoint documentation                                                                                                                                                                     |
| ---------------------------------------------------------- | ------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| "GET" "/pod/v1/connection/list"                            | GET\_USER\_CONNECTIONS                      | [list-connections.md](../connections/list-connections.md "mention")                                                                                                                        |
| "GET" "/pod/v1/admin/system/protocols/list"                | SEND\_MESSAGES                              | <p><em>Deprecated documentation. For more information, refer to:</em></p><p><a data-mention href="../uri-protocols/list-protocols-v2.md">list-protocols-v2.md</a></p>                      |
| "GET" "/pod/v1/connection/user/{userId}/info"              | GET\_USER\_CONNECTIONS                      | [get-connection.md](../connections/get-connection.md "mention")                                                                                                                            |
| "GET" "/pod/v1/files/allowedTypes"                         | SEND\_MESSAGES                              | [attachment-types.md](../messages/attachment-types.md "mention")                                                                                                                           |
| "GET" "/pod/v1/presence/feed/{feedId}/read"                | GET\_PRESENCE                               | [read-presence-feed.md](../presence/read-presence-feed.md "mention")                                                                                                                       |
| "GET" "/pod/v1/sessioninfo"                                | GET\_BASIC\_USER\_INFO                      | <p><em>Deprecated documentation. For more information, refer to:</em><br><a data-mention href="../info-health-check/session-info-v2.md">session-info-v2.md</a></p>                         |
| "GET" "/pod/v1/streams/{streamId}/info"                    | SEND\_MESSAGES                              | <p><em>Deprecated documentation. For more information, refer to:</em><br><a data-mention href="../streams-conversations/all-streams-endpoints/stream-info-v2.md">stream-info-v2.md</a></p> |
| "GET" "/pod/v1/user"                                       | GET\_BASIC\_CONTACT\_INFO                   | <p><em>Deprecated documentation. For more information, refer to:</em><br><a data-mention href="../users/users-lookup-v3.md">users-lookup-v3.md</a></p>                                     |
| "GET" "/pod/v1/user/presence"                              | GET\_PRESENCE                               | <p><em>Deprecated documentation. For more information, refer to:</em><br><a data-mention href="../presence/get-presence.md">get-presence.md</a></p>                                        |
| "GET" "/pod/v1/user/{userId}/presence"                     | GET\_PRESENCE                               | <p><em>Deprecated documentation. For more information, refer to:</em><br><a data-mention href="../presence/user-presence-v3.md">user-presence-v3.md</a></p>                                |
| "GET" "/pod/v2/sessioninfo"                                | GET\_BASIC\_USER\_INFO                      | [session-info-v2.md](../info-health-check/session-info-v2.md "mention")                                                                                                                    |
| "GET" "/pod/v2/user"                                       | GET\_BASIC\_CONTACT\_INFO  \nSEND\_MESSAGES | <p><em>Deprecated documentation. For more information, refer to:</em><br><a data-mention href="../users/users-lookup-v3.md">users-lookup-v3.md</a></p>                                     |
| "GET" "/pod/v2/user/presence"                              | GET\_PRESENCE                               | [get-presence.md](../presence/get-presence.md "mention")                                                                                                                                   |
| "GET" "/pod/v2/user/{userId}/presence"                     | GET\_PRESENCE                               | <p><em>Deprecated documentation. For more information, refer to:</em><br><a data-mention href="../presence/user-presence-v3.md">user-presence-v3.md</a></p>                                |
| "GET" "/pod/v3/room/{roomId}/info"                         | MANAGE\_ROOMS                               | [room-info-v3.md](../streams-conversations/room-endpoints/room-info-v3.md "mention")                                                                                                       |
| "GET" "/pod/v3/user/{userId}/presence"                     | GET\_PRESENCE                               | [user-presence-v3.md](../presence/user-presence-v3.md "mention")                                                                                                                           |
| "GET" "/pod/v3/users"                                      | GET\_BASIC\_CONTACT\_INFO                   | [users-lookup-v3.md](../users/users-lookup-v3.md "mention")                                                                                                                                |
| "POST" "/v1/user/{uid}/follow"                             | MANAGE\_USER\_FOLLOWING                     | [follow-user.md](../users/follow-user.md "mention")                                                                                                                                        |
| "POST" "/v1/user/{uid}/unfollow"                           | MANAGE\_USER\_FOLLOWING                     | [unfollow-user.md](../users/unfollow-user.md "mention")                                                                                                                                    |
| "GET" "/agent/v1/signals/{signalId}/get"                   | MANAGE\_SIGNALS                             | [get-signal.md](../signals/get-signal.md "mention")                                                                                                                                        |
| "GET"  "/agent/v1/signals/{signalId}/subscribers"          | MANAGE\_SIGNALS                             | [subscribers.md](../signals/subscribers.md "mention")                                                                                                                                      |
| "GET"  "/agent/v1/signals/list"                            | MANAGE\_SIGNALS                             | [list-signals.md](../signals/list-signals.md "mention")                                                                                                                                    |
| "POST" "/agent/v1/signals/create"                          | MANAGE\_SIGNALS                             | [create-signal.md](../signals/create-signal.md "mention")                                                                                                                                  |
| "POST" "/agent/v1/signals/{signalId}/update"               | MANAGE\_SIGNALS                             | [update-signal.md](../signals/update-signal.md "mention")                                                                                                                                  |
| "POST" "/agent/v1/signals/{signalId}/delete"               | MANAGE\_SIGNALS                             | [delete-signal.md](../signals/delete-signal.md "mention")                                                                                                                                  |
| "POST" "/agent/v1/signals/{signalId}/subscribe"            | MANAGE\_SIGNALS                             | [subscribe-signal.md](../signals/subscribe-signal.md "mention")                                                                                                                            |
| "POST" "/agent/v1/signals/{signalId}/unsubscribe"          | MANAGE\_SIGNALS                             | [unsubscribe-signal.md](../signals/unsubscribe-signal.md "mention")                                                                                                                        |
| "POST" "/agent/v3/stream/{streamId}/share"                 | SEND\_MESSAGES                              | [share-v3.md](../streams-conversations/all-streams-endpoints/share-v3.md "mention")                                                                                                        |
| "POST" "/agent/v4/stream/{streamId}/message/create"        | SEND\_MESSAGES                              | [create-message-v4.md](../messages/create-message-v4.md "mention")                                                                                                                         |
| "POST" "/agent/v4/message/blast"                           | SEND\_MESSAGES                              | [blast-message.md](../messages/blast-message.md "mention")                                                                                                                                 |
| "POST" "/agent/v4/stream/{:sid}/message/{:mid}/update"     | SEND\_MESSAGES                              | [update-message-v4.md](../messages/update-message-v4.md "mention")                                                                                                                         |
| "POST" "/v1/admin/messagesuppression/{messageId}/suppress" | SUPPRESS\_MESSAGES                          | [suppress-message.md](../messages/suppress-message.md "mention")                                                                                                                           |
| "POST" "/pod/v1/connection/create"                         | REQUEST\_USER\_CONNECTIONS                  | [create-connection.md](../connections/create-connection.md "mention")                                                                                                                      |
| "POST" "/pod/v1/im/create"                                 | SEND\_MESSAGES                              | [create-im-or-mim.md](../streams-conversations/im-mim-endpoints/create-im-or-mim.md "mention")                                                                                             |
| "POST" "/pod/v1/presence/feed/create"                      | GET\_PRESENCE                               | [create-presence-feed.md](../presence/create-presence-feed.md "mention")                                                                                                                   |
| "POST" "/pod/v1/presence/feed/{feedId}/delete"             | GET\_PRESENCE                               | [delete-presence-feed.md](../presence/delete-presence-feed.md "mention")                                                                                                                   |
| "POST" "/pod/v1/room/{roomId}/membership/add"              | MANAGE\_ROOMS                               | [add-member.md](../streams-conversations/room-endpoints/add-member.md "mention")                                                                                                           |
| "POST" "/pod/v1/room/{roomId}/membership/demoteOwner"      | MANAGE\_ROOMS                               | [demote-owner.md](../streams-conversations/room-endpoints/demote-owner.md "mention")                                                                                                       |
| "POST" "/pod/v1/room/{roomId}/membership/promoteOwner"     | MANAGE\_ROOMS                               | [promote-owner.md](../streams-conversations/room-endpoints/promote-owner.md "mention")                                                                                                     |
| "POST" "/pod/v1/room/{roomId}/membership/remove"           | MANAGE\_ROOMS                               | [remove-member.md](../streams-conversations/room-endpoints/remove-member.md "mention")                                                                                                     |
| "POST" "/pod/v1/room/{roomId}/setActive"                   | MANAGE\_ROOMS                               | [de-or-re-activate-room.md](../streams-conversations/room-endpoints/de-or-re-activate-room.md "mention")                                                                                   |
| "POST" "/pod/v1/streams/list"                              | LIST\_USER\_STREAMS                         | [list-user-streams.md](../streams-conversations/all-streams-endpoints/list-user-streams.md "mention")                                                                                      |
| "POST" "/pod/v1/user/presence"                             | SET\_PRESENCE                               | <p><em>Deprecated documentation. For more information, refer to:</em><br><a data-mention href="../presence/set-presence.md">set-presence.md</a></p>                                        |
| "POST" "/pod/v1/user/presence/register"                    | GET\_PRESENCE                               | [register-user-presence-interest.md](../presence/register-user-presence-interest.md "mention")                                                                                             |
| "POST" "/pod/v1/user/search"                               | GET\_BASIC\_CONTACT\_INFO                   | [search-users.md](../users/search-users.md "mention")                                                                                                                                      |
| "POST" "/pod/v2/user/presence"                             | SET\_PRESENCE                               | [set-presence.md](../presence/set-presence.md "mention")                                                                                                                                   |
| "POST" "/pod/v3/room/create"                               | MANAGE\_ROOMS  \nCREATE\_USER\_STREAM       | [create-room-v3.md](../streams-conversations/room-endpoints/create-room-v3.md "mention")                                                                                                   |
| "POST" "/pod/v3/room/search"                               | MANAGE\_ROOMS                               | [search-rooms-v3.md](../streams-conversations/room-endpoints/search-rooms-v3.md "mention")                                                                                                 |
| "POST" "/pod/v3/room/{roomId}/update"                      | MANAGE\_ROOMS                               | [update-room-v3.md](../streams-conversations/room-endpoints/update-room-v3.md "mention")                                                                                                   |
| "POST" "/pod/v3/user/presence"                             | SET\_PRESENCE                               | [set-user-presence.md](../presence/set-user-presence.md "mention")                                                                                                                         |

### The following table describes the use of permissions:

| Permission                 | Usage                                                                                        |
| -------------------------- | -------------------------------------------------------------------------------------------- |
| GET\_BASIC\_CONTACT\_INFO  | An app can get basic contact info.                                                           |
| GET\_BASIC\_USER\_INFO     | An app can get basic contact info.                                                           |
| SEND\_MESSAGES             | An app can send messages on behalf of a user. Creates IM for users.                          |
| SUPPRESS\_MESSAGES         | An app can suppress a user's messages on behalf of that user.                                |
| CREATE\_USER\_STREAM       | An app can create streams on behalf of a user.                                               |
| MANAGE\_ROOMS              | An app can manage streams on behalf of a user.                                               |
| MANAGE\_SIGNALS            | An app can list, create, edit, and delete signals on behalf of a user.                       |
| LIST\_USER\_STREAMS        | An app can get a list of user streams on behalf of users.                                    |
| GET\_USER\_CONNECTIONS     | An app can get an `appinfo` of all user connections on behalf of users.                      |
| REQUEST\_USER\_CONNECTIONS | An app can send connection requests on behalf of users.                                      |
| GET\_PRESENCE              | An app can get a user presence on behalf of users.                                           |
| SET\_PRESENCE              | An app can set presence on behalf of users.                                                  |
| MANAGE\_USER\_FOLLOWING    | An app can make a list of users follow or unfollow a considered user, identified by his uid. |

> 🚧 All OBO endpoints respect any existing entitlements or state for the user in session.
>
> For instance, if a user is not already connected to another user, an app cannot send a message to the second user on behalf of the first. Another example is that if a user does not have the "Can Send Files" entitlement in Symphony, an app cannot send a message containing an attachment on behalf of the user.
