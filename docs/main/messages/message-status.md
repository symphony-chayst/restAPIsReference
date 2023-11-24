# Message Status

Released in 1.47. Get the status of a particular message: `sent`, `delivered`, and `read`.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/message/{mid}/status" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

The response indicates the status of the message for internal and external users:

* `sent`: All users to whom the message has been sent and received by the Symphony system, but not yet delivered to any user's Symphony client.
* `delivered`: All users who have at least one Symphony client to which the message has been delivered, and not read yet.
* `read`: All users who have read that message, in any Symphony client.

Note:

* For security reasons, the response excludes `userName` for external users.
* If a message is suppressed, the `sent` array will never contain any users as the message would no longer be accessible to users who have not already seen it. If the message has been `read` or `delivered` prior to being suppressed, the relevant arrays are available.

> 📘 known exceptions
>
> • If the user was on the stream when the message was sent and the stream had "viewHistory" (for rooms) enabled, he can get the message status.\
> • If the user is a member of the stream, he can get the message status.

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
