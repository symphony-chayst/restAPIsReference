# V2 Violations endpoints

## Overview

The Violations endpoints enable you to get violations on messages, signals, and streams. Use these endpoints to retrieve Effective Filtering v1 and Effective Filtering v2 violations.

* **Message Violations:** A Block or warning that happens when sending messages with terms that match the violation policy. EFv2 provides DLP enforcement on the content (except mentions) of IMs, MIMs, chat rooms, wall posts, shared signals, posts on behalf of, shared wall posts, shared articles, blasts, forwards and replies.
* **Signal Violations:** A Block or warning that happens when creating or updating signals with terms that match the violation policy. For signals, only the signal name is analyzed.\
  Note that if a signal created before enabling DLP contains violations, DLP will block the signal when trying to “push signal”.
* **Stream Violations:** A Block or warning that happens when creating or updating rooms with terms that match the violation policy. For streams, the DLP analyses the name and description of internal and external rooms.

When EFv2 is enabled, Symphony may block or warn the user from sending a message, creating or updating rooms or signals if any of the terms used by the user match the terms in a policy. Any message that matches a term from a policy will be recorded.

* If the message action is block, the user cannot send the message, create or update the room or signal.
* If the message action is warn, the user can ignore the warning (and send the content) or edit the content

Messages and signals are encrypted end-to-end. To decrypt messages, you must be a “ceservice” user with the Service Account role of “Expression Filter Policy Management.”

With EFv2, the admin can create policies to parse the content of:

* Messages: violations for these can be retrieved via the https://\{{agent.url\}}/agent/v1/dlp/violations/message/?startTime=1504234983000\&endTime=1504237983000\&limit=100\&next= API
* Room names and description - aka streams: violations for these can be retrieved via the https://\{{agent.url\}}/agent/v1/dlp/violations/stream/?startTime=1504234983000\&endTime=1504237983000\&limit=100\&next= API
* Name and rules of signals - violations for these can be retrieved via the https://\{{agent.url\}}/agent/v1/dlp/violations/signal/?startTime=1504234983000\&endTime=1504237983000\&limit=100\&next= API

The parameters and behaviors are the same for all three APIs.

## Key Parameters

* Time range of violations
* Number violations in each request
* Next offset for next chunk. Value is null for first request

## Key Headers

Session token and Key Manager Tokens of the ceservice user

## Curl Examples

```
curl -X POST \
  https://<SYMPHONY_POD>/agent/v1/dlp/violations/message/?startTime=1504234983000&endTime=1504237983000&limit=100&next=<next> \
  -H 'Content-Type: multipart/form-data' \
  -H 'sessionToken: SESSION_TOKEN' \
  -H 'keyManagerToken: KEY_MANAGER_TOKEN'
 
curl -X POST \
  https://<SYMPHONY_POD>/agent/v1/dlp/violations/stream/?startTime=1504234983000&endTime=1504237983000&limit=100&next=<next> \
  -H 'Content-Type: multipart/form-data' \
  -H 'sessionToken: SESSION_TOKEN' \
  -H 'keyManagerToken: KEY_MANAGER_TOKEN'
 
curl -X POST \
  https://<SYMPHONY_POD>/agent/v1/dlp/violations/signal/?startTime=1504234983000&endTime=1504237983000&limit=100&next=<next> \
  -H 'Content-Type: multipart/form-data' \
  -H 'sessionToken: SESSION_TOKEN' \
  -H 'keyManagerToken: KEY_MANAGER_TOKEN'
```

## Viewing EFv1 violations

Violations triggered by EFv1 can be retrieved using the same violations APIs as for EFv2 violations.\
The JSON response structure will be exactly same as V2, except that the version will be V1.

User experience of V1:

![](https://files.readme.io/30a98a6-v1\_UI\_example.png)

The JSON Response for this scenario is shown below. Note that "version": "V1" indicates this violation event is for the v1 policy

```json
{
    "violation": {
        "enforcementEventID": "MESSAGE-TlxuOjh0zN85WpctHjqt3n///qF5VtnAdA==-1505497785925",
        "entityID": "TlxuOjh0zN85WpctHjqt3n___qF5VtnAdA",
        "createTime": 1505497785925,
        "lastModified": 0,
        "requesterId": 7215545057281,
        "matchedPolicies": [
            {
                "id": "",
                "version": "",
                "policyName": "",
                "type": "BLOCK",
                "terms": "iwan"
            }
        ],
        "action": "BLOCK",
        "outcome": {
            "type": "REJECTED_VIOLATION"
        },
        "version": "V1",
        "ignoreDLPwarning": false
    },
    "message": {
        "messageId": "TlxuOjh0zN85WpctHjqt3n___qF5VtnAdA",
        "timestamp": 0,
        "message": "<div data-format=\"PresentationML\" data-version=\"2.0\"><br/>iwan</div>",
        "data": "{}",
        "user": {
            "userId": 7215545057281,
            "displayName": "Admin Admin"
        },
        "stream": {
            "streamId": "mefj3zeuw1DiXUJ9UYGS7n___qGmLnd_dA",
            "streamType": "IM"
        }
    }
},
```

## Viewing EFv2 violations

The response from the server is controlled by the “limit” parameter. “nextOffset” is the starting point of the violation records.

When nextOffset is null, there are no records for that startTime, endTime, and content type. (If enforceExpressionFiltering is true in the request, that means client is v2 compatible)

The violation response contains a list of:

* Matched policies
* Matched term(s)
* Policy action: block or warn\
  Violations resulting from DLP will have version V2

## **Case 1:** A term is blocked, and the user needs to edit the message.

JSON-snippet:

```json
"action": "BLOCK", "outcome": { "type": "REJECTED_VIOLATION" }, "version": "V2", "ignoreDLPwarning": false
```

In this scenario, the user has been blocked and the message was not sent.\
Flag: ignoreDLPwarning wouldn't make difference because user MUST change the content in order to send the message.

The UI for this scenario is shown below:

![](https://files.readme.io/4045467-EFv2\_Block.png)

The corresponding JSON for this violation in this scenario (BLOCK):

```json
{
    "violations": [
        {
            "violation": {
                "enforcementEventID": "MESSAGE-owrnjQwyzA1po9T7t+X0Zn///qF5Wgl/dA==-1505497577139",
                "entityID": "owrnjQwyzA1po9T7t-X0Zn___qF5Wgl_dA",
                "createTime": 1505497577139,
                "lastModified": 0,
                "requesterId": 7215545057281,
                "matchedPolicies": [
                    {
                        "id": "59bc1108e4b09308efcabb3e",
                        "version": "1.0",
                        "policyName": "facebook-IPO",
                        "type": "BLOCK",
                        "terms": "facebook-IPO"
                    },
                    {
                        "id": "59bc1108e4b09308efcabb3e",
                        "version": "1.0",
                        "policyName": "facebook-IPO",
                        "type": "BLOCK",
                        "terms": "facebook"
                    }
                ],
                "action": "BLOCK",
                "outcome": {
                    "type": "REJECTED_VIOLATION"
                },
                "version": "V2",
                "ignoreDLPwarning": false
            },
            "message": {
                "messageId": "owrnjQwyzA1po9T7t-X0Zn___qF5Wgl_dA",
                "timestamp": 1505497577094,
                "message": "<div data-format=\"PresentationML\" data-version=\"2.0\"><br/>There is facebook-IPO next month</div>",
                "data": "{}",
                "user": {
                    "userId": 7215545057281,
                    "firstName": "Admin",
                    "lastName": "Admin",
                    "displayName": "Admin Admin",
                    "email": "admin@symphony.com",
                    "username": "admin@symphony.com"
                },
                "stream": {
                    "streamId": "mefj3zeuw1DiXUJ9UYGS7n___qGmLnd_dA",
                    "streamType": "IM"
                },
                "externalRecipients": false
            }
        },
```

## **Case 2**: The user is warned about a term and edits the content of their message.

JSON-snippet:

```json
"action": "WARN", "outcome": { "type": "REJECTED_VIOLATION" }, "version": "V2", "ignoreDLPwarning": false
```

In this scenario, the user has been warned and the message was not sent.

The UI for this scenario is shown below:

![](https://files.readme.io/9cc4f14-EFv2\_Warn.png)

The corresponding JSON for this violation in this scenario (WARN):

```json
{
    "violation": {
        "enforcementEventID": "MESSAGE-dMbc7cAho5jLUAWWs/VJu3///qF5WI/3dA==-1505497673771",
        "entityID": "dMbc7cAho5jLUAWWs_VJu3___qF5WI_3dA",
        "createTime": 1505497673771,
        "lastModified": 0,
        "requesterId": 7215545057281,
        "matchedPolicies": [
            {
                "id": "59bc11b1e4b09308efcabb47",
                "version": "1.0",
                "policyName": "potential-merger",
                "type": "WARN",
                "terms": "potential-merger"
            }
        ],
        "action": "WARN",
        "outcome": {
            "type": "REJECTED_VIOLATION"
        },
        "version": "V2",
        "ignoreDLPwarning": false
    },
    "message": {
        "messageId": "dMbc7cAho5jLUAWWs_VJu3___qF5WI_3dA",
        "timestamp": 1505497673740,
        "message": "<div data-format=\"PresentationML\" data-version=\"2.0\"><br/>potential-merger with Oracle</div>",
        "data": "{}",
        "user": {
            "userId": 7215545057281,
            "firstName": "Admin",
            "lastName": "Admin",
            "displayName": "Admin Admin",
            "email": "admin@symphony.com",
            "username": "admin@symphony.com"
        },
        "stream": {
            "streamId": "mefj3zeuw1DiXUJ9UYGS7n___qGmLnd_dA",
            "streamType": "IM"
        },
        "externalRecipients": false
    }
},
```

If the user decided to edit the message, that edited message is treated as a brand new message: there is no further violation event assuming the content in this new message does not trigger any policies

## **Case 3**: The user is warned, accepts the warning, and sends the message as-is

JSON-snippet:

```json
"action": "WARN", "outcome": { "type": "ACCEPTED_WARNING" }, "version": "V2", "ignoreDLPwarning": true
```

In this scenario, the system will generate 2 violation events. If a user chooses to send a message that flagged a warning, it will generate two violations back-to-back. The two events can be correlated based on the timestamp in the records.

* The first time the user sends the message, a warning message will appear, similar to case 2. If the user continues to send the message without editing the flagged term, 'ignoreDLPwarning=true' flag is added to the message.
* By choosing to ignore the warning, the message is flagged again, and 'ACCEPTED\_WARNING' flag is added to the message.

The corresponding UI is shown below

![](https://files.readme.io/d4c96e9-EFv2\_Warn\_Ignored.png)

The corresponding JSON for this violation in this scenario:

```json
{
    "violation": {
        "enforcementEventID": "MESSAGE-tGpmIT1K5QBky8D5xF+hqn///qF5WDBTdA==-1505497698262",
        "entityID": "tGpmIT1K5QBky8D5xF-hqn___qF5WDBTdA",
        "createTime": 1505497698262,
        "lastModified": 0,
        "requesterId": 7215545057281,
        "matchedPolicies": [
            {
                "id": "59bc11b1e4b09308efcabb47",
                "version": "1.0",
                "policyName": "potential-merger",
                "type": "WARN",
                "terms": "potential-merger"
            }
        ],
        "action": "WARN",
        "outcome": {
            "type": "ACCEPTED_WARNING"       <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
        },
        "version": "V2",
        "ignoreDLPwarning": true             <<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<<
    },
    "message": {
        "messageId": "tGpmIT1K5QBky8D5xF-hqn___qF5WDBTdA",
        "timestamp": 1505497698230,
        "message": "<div data-format=\"PresentationML\" data-version=\"2.0\"><br/>potential-merger with Oracle</div>",
        "data": "{}",
        "user": {
            "userId": 7215545057281,
            "firstName": "Admin",
            "lastName": "Admin",
            "displayName": "Admin Admin",
            "email": "admin@symphony.com",
            "username": "admin@symphony.com"
        },
        "stream": {
            "streamId": "mefj3zeuw1DiXUJ9UYGS7n___qGmLnd_dA",
            "streamType": "IM"
        },
        "externalRecipients": false
    }
},
```

## Viewing violations triggered by legacy clients

Legacy Clients are older clients that do not have functionality to display the Warn or Block UI of EFv2. There will be no warning or block message preventing them from sending messages that violate any policies.

DLP parsing is still done and the violations will be recorded, but the users will not be aware of this violation

JSON-snippet:

```json
"action": "ALLOW", "outcome": { "type": "ACCEPTED_LEGACY_CLIENT" }, "version": "V2", "ignoreDLPwarning": false
```

## Violation API FAQ

* What am I not always seeing violations?\
  \*\* Make sure you have a “ceservice” role and have the correct privileges to call this API.\
  \*\* If Symproxies are unavailable, the default behavior is to continue, even in violation of a policy.

> ### 🚧 Required Permissions
>
> Calling these endpoints requires a `ceservice` account. For more information, see the [Symphony Administration Guide](https://symphony.direct/).
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
