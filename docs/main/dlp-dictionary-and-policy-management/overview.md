# Overview

The Data Loss Prevention (DLP) endpoints are part of the Expression Filtering v2 (EFv2) and v3 (EFv3) functionality released in 1.49. This functionality is an extension of Expression Filtering v1.

When this feature is turned on, a Super Administrator can define content violation policies with dictionary terms and the appropriate policy scoping (Internal or External) for messages, streams, and signals. As Symphony client end users perform certain actions (specifically send messages and create or update rooms and signals), the system may block or warn the user when any content matches terms defined in the policy, as follows:

* BLOCK: The end user can’t send the message or create or update the room or signal.
* WARN: The end user can rectify the issue by either:\
  • Removing the text that matched policy terms. The results show `"ignoreDLPwarning": "false"`.\
  • Sending the content as is and ignoring the warning. The results show `"ignoreDLPwarning": "true"`.

When an end user’s communication results in a BLOCK or WARN, the EFv2 or EFv3 functionality records these violation events. This data is available via the Violation endpoints.

### DLP Endpoints

The dictionary and policy management endpoints enable you to view, create, edit, and delete your dictionaries and policies in the EFv2 or EFv3 system. The violations endpoints enable you to get violations on messages, signals, and streams. For authentication, use the [Key Manager](../bot-authentication/rsa-key-manager-authenticate.md) and [Session](../bot-authentication/rsa-session-authenticate.md) tokens.

The Dictionary Management endpoints are described in the subpages, accessible using the navigation menu on the left.

### Requirements

The Symphony administrator must be a Super Administrator.

The endpoint caller must have the following:

* Be a Content Export Service (`ceservice`) user.
* Have the service account role "Expression Filter Policy Management".
* Be able to decrypt Base64-encoded messages.

Your company must have implemented EFv2 or EFv3 functionality for the pod. This requires a new component called the SymProxy that decrypts and parses content.

* If you are doing on-prem management of your security keys (i.e.; if you have an on-prem KM), you will need to deploy the Symproxies on-prem as well
* If you are leveraging an on-pod KM, your pod will have on-pod Symproxies managed by Symphony

For more information, see the Symphony Administration Guide.

> #### 📘 Notes
>
> * When a SymProxy is unavailable, messages are ingested and sent even though not parsed.
> * Legacy clients won’t show BLOCK and WARN messages on the interface. Because there is no interface to prevent users from performing an action, the content is sent and the violation is recorded as `"type": "ACCEPTED_LEGACY_CLIENT"`.

### Embedded Error Responses

For the beta release of these endpoints, the error response includes the error message contained within the "message" property of the returned object.

The example shows a sample error response for a dictionary validation issue.

```json
{
  "code": 400,
  "message": "400 Bad Request: {\"message\":\"Request contains invalid dictionaries that can not be found in database\"}"
}
```

### DLP for Agent Endpoints

With DLP (Data Loss Prevention) enabled, when the Agent performs an action with terms predefined in the Policy, the Expression Filters (v3) records these violation events as shown below.

EFv3:

* Message content: verifies if a message contains forbidden content or files.
* File content: verifies if a file contains a forbidden name, terms or expressions.
* File size: verifies the maximum size of an attachment.
* File extension: verifies if the file extension is forbidden.
* File password protection: blocks files with or without a password, depending on what was configured in the policy.
* File Classifier: blocks files with metadata violation.
* Chat Room: verifies if the chat name or description contains forbidden expressions.
* Signals: verifies name, words, and tags.

In order to perform the actions mentioned above and return a 451 error (BLOCK or WARN), the following endpoints are subject to DLP:

* [Create Message v4](../messages/create-message-v4.md).
* [Create Room v3](../streams-conversations/room-endpoints/create-room-v3.md).
* [Create Signal](../signals/create-signal.md).

Click on the endpoints above to see the messages returned by each 451 error response.
