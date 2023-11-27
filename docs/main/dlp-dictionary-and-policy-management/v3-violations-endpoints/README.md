# V3 Violations endpoints

## Overview:

The Violations endpoints enable you to get violations of messages, signals, and streams. Use these endpoints to retrieve Expression Filtering v3 (EFv3) violations.

* **Message Violations:** A Block or warning that happens when sending messages with terms that match the violation policy. EFv3 provides DLP enforcement on the content (except mentions) of IMs, MIMs, chat rooms, wall posts, shared signals, posts on behalf of, shared wall posts, shared articles, blasts, forwards and replies.\
  In addition, administrators can configure EFv3 policies that will enforce DLP on the content of attachments and certain metadata of attachments. The metadata that can be enforced in EFv3 are size (e.g. 3 Mb limit), classification tags, password protection and attachment type (file extension, e.g .txt files). For more information on creating and updating EFv3 policies please view the documentation for [V3 Policy Management endpoints](../v3-policy-management-endpoints/).
* **Signal Violations:** A Block or warning that happens when creating or updating signals with terms that match the violation policy. For signals, only the signal name is analyzed.\
  Note that if a signal created before enabling DLP contains violations, DLP will block the signal when trying to “push signal”.
* **Stream Violations:** A Block or warning that happens when creating or updating rooms with terms that match the violation policy. For streams, the DLP analyses the name and description of internal and external rooms.

When EFv3 is enabled, Symphony may block or warn the user from sending a message, creating or updating rooms or signals if any of the terms used by the user match the terms in a policy. Any message that matches a term from a policy will be recorded.

* If the policy action is "block", the user cannot send the message, create or update the room or signal.
* If the policy action is "warn", the user can ignore the warning (and send the content) or edit the content

Additionally, the policy action could be set to "log-only". If the message action is set to "log-only", DLP does not block the content but a violation is generated. In this case, the end-user will not be affected but a corresponding violation will be saved so that users of these violation endpoints can view all information regarding the action.

## API Description and Sample Responses

## EFv3 Endpoints:

• Stream metadata - https:///agent/v3/dlp/violations/stream/?startTime=1504234983000\&endTime=1504237983000\&limit=100\&next=\
[Details here](v3-stream-violations.md)

• Signal names and rules - https:///agent/v3/dlp/violations/signal/?startTime=1504234983000\&endTime=1504237983000\&limit=100\&next= \
[Details here](v3-signal-violations.md)

• Messages - https:///agent/v3/dlp/violations/message/?startTime=1504234983000\&endTime=1504237983000\&limit=100\&next=\
[Details here](v3-message-violations.md)

> ### 📘 Attachment Related Violations
>
> Violations that occur for attachment content or metadata will be queryable through the Messages endpoint
>
> The fileId of the attachment and messageId of the message that triggered the DLP policy are included in the violation. You can use these two parameters in the [download attachment endpoint](v3-violation-attachment-download.md) to download the actual attachment

## Key Parameters

* Time range of violations - `startTime`, `endTime`.
* Number of violations in each request - `limit` (max is 500).\
  If `limit` is not set, the maximum of 50 violations will be returned and the `nextOffset` parameter will be empty. The `nextOffset` parameter only returns a value when the response reaches more than 50 violations.
* Next offset for next chunk - `next` (the value is null for the first request).

## Key Headers

* Session token obtained from [Session Authenticate](../../bot-authentication/rsa-session-authenticate.md) endpoint - `sessionToken`.
* Key manager token obtained from [Key Manager Authenticate](../../bot-authentication/rsa-key-manager-authenticate.md) endpoint - `keyManagerToken`.

Please, visit the [Swagger API definition](https://github.com/symphonyoss/symphony-api-spec) for more details.

## Sample Responses

For more information and examples of message and attachment violations, refer to:

[Sample responses](v3-violations-sample-responses.md).\
[Special Scenarios of Attachment Violations](v3-violations-special-scenarios-of-attachments.md).

> ### 🚧 Migrating from older versions of DLP
>
> If you are migrating from an older version of DLP (EFv1 or EFv2), please keep in mind that violations that occurred with any older versions will not be accessible through these endpoints. Only EFv3 violations can be queried through EFv3 violations endpoints. You will need to use the older violation endpoints to retrieve EFv1 or EFv2 violations.
>
> Once EFv3 is enabled, EFv2 violations will no longer be generated.

## Encryption and Authorization:

Message content and violation details for EFv3 violations are encrypted using a special key referred to as the DLP\_CRYPTO\_KEY. Only users with specific roles can access this key to decrypt the message content and violation details. The roles that have access to this key are:

* CONTENT\_EXPORT\_SERVICE
* EF\_POLICY\_MANAGEMENT
* SUPER\_ADMINISTRATOR
* SUPER\_COMPLIANCE\_OFFICER

> ### 🚧 Service User Accounts
>
> For more information about Service User accounts and their roles, see the [Symphony Administration Guide](https://symphony.direct/).
