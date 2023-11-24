# Import Message

Available on Agent 2.0.0 and above. Organizations can import messages to Symphony from another system using Symphony’s REST API. Typically message import is performed before an organization begins using Symphony, so that users' previous content and context are available from day one within Symphony.This endpoint Imports a message into Symphony from another system. Imported messages will be displayed in Symphony clients with the original system's content, sender, and timestamp.This endpoint takes as input a list of messages to be imported and outputs a status for each message. If a message is successfully imported, the `messageId` of the message created in Symphony is returned.If import fails on a given message, the rest of the operation will continue. It will be possible to detect any failures only after the entire operation is completed.

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v4/message/import" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

### Request Examples

```bash
curl -X POST \
https://acme.symphony.com/agent/v4/message/import \
-H "sessionToken: SESSION_TOKEN" \
-H "keyManagerToken: KEY_MANAGER_TOKEN" \
-H "Content-Type: application/json" \
-d '[
    {
        "message": "<messageML>Imported message</messageML>",
        "format": "MESSAGEML",
        "intendedMessageTimestamp": 1433045622000,
        "intendedMessageFromUserId": 7215545057281,
        "originatingSystemId": "fooChat",
        "streamId": "Z3oQRAZGTCNl5KjiUH2G1n___qr9lLT8dA",
        "attachments": [
          {
            "filename": "symphonyLogo.png",
            "content": "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"
          },
          {
            "filename": "attachment.txt",
            "content": "VGhpcyBpcyBhbiBhdHRhY2htZW50Lg=="
          }
        ],
        "previews": [
          {
            "filename": "symphonyPreview.png",
            "content": "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"
          },
          {
            "filename": "attachment.txt",
            "content": "VGhpcyBpcyBhbiBhdHRhY2htZW50Lg=="
          }
        ]
    }
]'
```

```bash
curl -X POST \
https://acme.symphony.com/agent/v4/message/import \
-H "sessionToken: SESSION_TOKEN" \
-H "keyManagerToken: KEY_MANAGER_TOKEN" \
-H "Content-Type: application/json" \
-d '[
    {
        "message": "<messageML>Imported message</messageML>",
        "format": "MESSAGEML",
        "intendedMessageTimestamp": 1433045622000,
        "intendedMessageFromUserId": 7215545057281,
        "originatingSystemId": "fooChat",
        "streamId": "Z3oQRAZGTCNl5KjiUH2G1n___qr9lLT8dA"
    }
]'
```

### Prerequisites

* Your pod must be configured for Symphony's REST API, and you must have the [Agent](https://docs.developers.symphony.com/admin-guide/agent-guide/agent-download), the component used for handling encryption and decryption of messages and content, set up.
* You must have a Service User with the **Content Management** roles. This user can be set up in the Admin Portal. In most cases, you will also want this user to have the User Provisioning role as well. This user will be used to import messages.
* You must have a X.509 identity certificate for your import service user for REST API [authentication](../bot-authentication/), where the common name on the certificate matches your service user's username.

> 📘 Service User Accounts
>
> A service account is a type of account used for bots or applications, rather than for real end-users.

> 🚧 Importing Messages
>
> The Content Management role is required to call the Import Message endpoint.
>
> Please note that the service user account needs to be part of the room where it imports messages.
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

### v4ImportedMessage Format

You must specify each message to import as an object with the following fields:

<table><thead><tr><th>Field</th><th width="159">Type</th><th width="102" data-type="checkbox">Required</th><th>Description</th></tr></thead><tbody><tr><td>message</td><td>string</td><td>true</td><td><ul><li>Messages can be sent either in plain text or <a href="https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml">MessageML</a>, Symphony’s message format which allows for basic formatting and entities.</li><li>It is not possible to import file attachments.</li></ul></td></tr><tr><td>data</td><td>string</td><td>false</td><td>Entity data in EntityJSON</td></tr><tr><td>intendedMessageTimestamp</td><td>integer</td><td>true</td><td><p>The timestamp representing the time when the message was sent in the original system in milliseconds since January 1 1970 00:00:00 UTC.</p><p></p><p>Displays in Symphony clients as the timestamp of when the message was sent.</p><p></p><p>For example, if the message was originally sent in another system on January 1, 2016 and was imported on February 1, 2016, the Symphony conversation UI would show the message as being sent on January 1, 2016.</p><p></p><p>Must be a valid time in the past; a timestamp in the future returns an error.</p></td></tr><tr><td>intendedMessageFromUserId</td><td>long integer</td><td>true</td><td><p></p><p>The userId (long integer) of the Symphony user who sent the message. This user must:</p><ul><li>Be a member of the <code>streamId</code> that the message is being imported into.</li><li>Be an active user at the time of import.</li></ul><p>Importing messages from users who are inactive or not stream members results in an error.</p><p></p><p>You can deactivate this user after importing the message.</p><p></p><p>Note that the import service user does not need to be a member of the stream into which the message is imported.</p></td></tr><tr><td>originatingSystemId</td><td>string</td><td>true</td><td>An identifier for the original system through which the message was initially sent.</td></tr><tr><td>originalMessageId</td><td>string</td><td>false</td><td>The ID of the message in the originating system is used to prevent duplicate imports. During message import, the original messages IDs are compared to previously imported entries; in case of an exact match, the matching messages are ignored in the import.</td></tr><tr><td>streamId</td><td>string</td><td>true</td><td><p>The ID of the stream (IM, multi-party IM or chatroom) into which the message is imported. Must be an active stream. Importing a message into an inactive stream results in an error. See <a href="https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams">Conversation ID</a> for details. It is possible to deactivate the room (or user in the case of an IM/MIM) after import.</p><p></p><p><strong>Note</strong>: You can’t stream messages to this endpoint: <a href="ref:read-messagesevents-stream-v4">Read Messages/Events Stream v4</a></p></td></tr><tr><td>attachments</td><td>array of objects</td><td>false</td><td><p>One or more files to be sent along with the message. The limit is set to 30Mb total size; also, it is recommended not to exceed 25 files.</p><p></p><p>Each attachment object is made up of the two following required field:</p><ul><li><code>filename</code> including the extension (i.e. img.png, test.txt)</li><li><code>content</code> as Base64 encoded string</li></ul></td></tr><tr><td>previews</td><td>array of objects</td><td>false</td><td><p>Optional attachment preview.</p><p></p><p>Each preview object is made up of the two following required field:</p><ul><li><code>filename</code> including the extension (i.e. img.png, test.txt) </li><li><code>content</code> as Base64 encoded string</li></ul><p>When using previews, make sure to declare the same number of previews as the attachments declared.</p></td></tr></tbody></table>

### V4ImportResponse

| Field                 | Type       | Description                                                              |
| --------------------- | ---------- | ------------------------------------------------------------------------ |
| `messageId`           | **string** | Contains the Symphony message ID if the message is successfully created. |
| `originatingSystemId` | **string** | See the description in **v4ImportedMessage format**.                     |
| `originalMessageId`   | **string** | See the description in **v4ImportedMessage format**.                     |
| `diagnostic`          | **string** | Contains an error message if the message import fails.                   |

**Unread Status and Notifications**

* Imported messages do not generate unread message count badge notifications in the user's left navigation menu.
* Imported messages are not highlighted as unread in conversations.

**Read Receipts**

* Read receipts cannot be imported from another system to Symphony.
* Read receipts will be generated if a user views an imported message. This will be reflected in the Message Status table, displayed when clicking on the timestamp of a message.

**Special Entities**

* Imported messages which contain an at-mentions will appear in Social Activity under Recently Mentioned You; however, they do not generate unread message count badge notifications.
* Imported messages which contain hashtags and cashtags will not appear in Signals.

### Content Export of Imported Messages

Imported messages are reflected in content export based on their `intendedMessageTimestamp`. This means that when the import occurs, content export:

* **Excludes** historical messages with an `intendedMessageTimestamp` outside of the content export range.
* **Includes** include historical messages with an `intendedMessageTimestamp` within the content export range.

For ad-hoc content export, the content export range is specified by the user. For example, for an ad-hoc content export set with a start date of Jan 3 and an end date of Jan 5:

* Messages with an `intendedMessageTimestamp` prior to Jan 3 at 00:00:00 UTC \*\*are not \*\*exported.
* Messages with an `intendedMessageTimestamp` between to Jan 3 at 00:00:00 UTC and Jan 5 at 23:59:59 UTC **are** exported.
* Messages with an `intendedMessageTimestamp` after to Jan 5 at 23:59:59 UTC **are not** exported.

For recurring content export, the content export range is defined as the period until the next scheduled content export, with a duration of the content export frequency. For example, for a frequency of 24 hrs running at 01:00:00 UTC on Feb 10:

* Messages with an `intendedMessageTimestamp` prior to Feb 9 at 01:00:00 UTC \*\*are not \*\* exported.
* Messages with an `intendedMessageTimestamp` between to Feb 9 at 01:00:00 UTC and Feb 10 at 01:00:00 UTC **are** exported.

### Correct and Reimport Failed Messages

If a message import fails, use the information reported in the `diagnostic` field to correct the error and call this endpoint again. Symphony ignores any message with the same `originalMessageId` value as an existing message, and imports only those messages with unique`originalMessageId` values.

### Steps to Import a Message

1. Ensure users involved with the message are provisioned.
2. Ensure all streams have been created .
3. Import the message.
4. (Optional) User and Stream Membership and Deactivation.

### User Provisioning

When you migrate messages from another system to Symphony, you will need to ensure that the accounts of all users involved (all original senders and recipients) are created.

If all these users exist, you can skip this step.

User accounts can be provisioned via Symphony's REST API.

> 📘 User Provisioning Service User Account
>
> Accounts are provisioned by a Service User account which must be assigned the User Provisioning role. This user can be set up in the Admin Portal.
>
> It is possible to use the same service user account for both message import and account provisioning provided it has been assigned both the Content Management and User Provisioning roles.

In some cases, you will want to import messages where the original sender is no longer a member of the room or the firm. In this case, you should create the user, import any messages sent by that user, and either remove the user from the room or deactivate the user after the import has been performed.

### Stream Creation

You will also need to ensure that all the streams (IMs/MIMs/chatrooms) have been created.

If all of these streams exist, you can skip this step.

Chatrooms can be created and managed via Symphony's REST API. Refer to the [Create Room v3](ref:create-room-v3) endpoint.

> 📘 Changing Chatroom Ownership
>
> If the import service user account is used to create chatrooms, the import service user will be the owner of those chatrooms.
>
> To change this, you can promote a member of the room to an owner and remove the import service user from the room.

In some cases, you may wish to import conversations into chats between two or more users - IMs or MIMs.

IMs and MIMs can be created using the [Create IM or MIM (admin)](ref:create-im-or-mim-admin) endpoint.

> 🚧 Admin IM/MIM Creation
>
> The User Provisioning role is required to call the [Create IM or MIM (admin)](ref:create-im-or-mim-admin) endpoint.
>
> You must use this endpoint rather than the [Create IM or MIM](ref:create-im-or-mim) endpoint, so that the calling service user is not included as a participant of the chat.

### Message Import

Messages are imported using the **Import Message** endpoint described above.

> 🚧 Message Import Limits
>
> * We recommend importing in batches of no more than 5,000 messages at a time. Importing more than this number may result in slowness.
> * We recommend to be very precautious when using attachments with this endpoint as it will increase the payload hence the network usage between the Bot and the Agent.

> 🚧 Migration Times
>
> You should plan for a migration period, length dependent on the volume of messages to import and network latency.
>
> In our experience, an organization can import about 200K messages / hour.

> ❗️ Import Limitations
>
> It is only possible to import messages from another system into Symphony. It is not possible to import read receipts or chatroom events (ex. membership changes).

### User and Stream Membership and Deactivation

Once you have imported all your messages, you may wish to remove certain users from rooms or deactivate certain users or rooms.

For example, if you used the import service user for room creation, you may want to transfer ownership of the room and remove this user from the room.

For example, you may want to deactivate the Symphony user that was created to represent a user who sent messages in the old system, but has since left the firm.

### Admin Impact

**Content Export**\
The following are some notes that may be of interest to admins regarding aspects of imported messages:

* Imported messages are exported in Content Export based on the original timestamp (`intendedMessageTimestamp`).
* After messages are imported, Content Export will not include imported messages where the original timestamp is outside of the Content Export range and will include messages where the original timestamp is within the Content Export range.
* In ad-hoc content export, the range is specified by the admin user.
* For example, for an ad-hoc content export with a start date of January 1 and end date of January 5:
  * Messages with an original timestamp before January 1, 00:00:00 UTC **would not be** exported.
  * Messages with an original timestamp between January 1, 00:00:00 UTC and January 5, 23:59:59 UTC **would be** exported.
  * Messages with an original timestamp after January 5, 23:59:59 **would not be** exported.
* In recurring content export, the range is defined as the period until the next scheduled content export, with a duration of the content export frequency specified by the admin user.
* For example, for a recurring content export with a frequency of 24 hours running on February 2, 00:00:00 UTC:
  * Messages with an original timestamp before February 1, 00:00:00 UTC **would not be** exported.
  * Messages with an original timestamp between February 1, 00:00:00 UTC and January 2, 00:00:00 UTC **would be** exported.

**Room Monitor**

* Imported messages will be displayed in the Room Monitor as they are displayed to room members - with the original sender and original timestamp.

> 📘 See also
>
> [Message](https://docs.developers.symphony.com/building-bots-on-symphony/messages)\
> [MessageML](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml)\
> [Message ID](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml#message-identifiers)\
> [Message Format - MessageML](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml/message-format-messageml)\
> [PresentationML](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-presentationml)\
> [Message Format - ExtensionML](https://docs.developers.symphony.com/building-extension-applications-on-symphony/overview-of-extension-api/extension-api-services/entity-service/message-format-extensionml)\
> [Colors](https://docs.developers.symphony.com/developer-tools/developer-tools/ui-style-guide/colors)\
> [Symphony Elements](https://docs.developers.symphony.com/building-bots-on-symphony/symphony-elements)
