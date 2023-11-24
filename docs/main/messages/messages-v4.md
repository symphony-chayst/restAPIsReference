# Get Messages

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v4/stream/{sid}/message" method="get" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> 📘 Optional attributes returned
>
> Note that some attributes are returned in the payload only under specific conditions:
>
> * `sharedMessage` only when the message represented by this class is a wall post sharing another message;
> * `initialMessageId`, `initialTimestamp`, and `replacing` only when the corresponding message is sent as an update to another message thanks to [Update Message](ref:update-message-v4) endpoint. Note that the first two attributes relate to the original (and therefore first) message sent, whereas the `replacing` attribute relates to the message that has been updated by this message;
> * `replacedBy` only when this message has been updated by a new message. It contains the id of the replacing message.
> * `parentMessageId` only when this message is a reply or a forward of another message which id is returned in this attribute.

## Pagination usage

• The `skip` parameter is supposed to be used to skip messages that have the same timestamp as the one specified on `since`.

• Pagination is supposed to use the `since` parameter instead of `skip` and `limit`.

Examples:

If you want to get two messages at a time skipping the ones you have already seen, the calls should be the following:

1. First call\
   `https://acme.symphony.com/agent/v4/stream/sid/message?since=0&limit=2`
2. Second call\
   Let's assume here that the timestamp from the message returned on the first call was 1551052800000 and there was no other message with that same timestamp returned.

`https://acme.symphony.com/agent/v4/stream/sid/message?since=1551052800000&limit=2&skip=1`

It returns the two messages received after or on the timestamp 1551052800000, skipping one message from that same timestamp (which is the one you have already seen).

Note that you can keep doing this process with subsequent calls.

> 📘 Supported stream types
>
> In addition to conversation streams such as IM, MIM, Chat rooms and Wall posts, Symphony also supports other types of streams, some of them reserved for internal use. These other stream types (ACTION, POST, PRIVATE\_CHANNEL, MEETING, SUPPRESS\_JUSTIFICATION) are not supported by the Get Messages endpoint.

> 📘 See also:
>
> [Message](https://docs.developers.symphony.com/building-bots-on-symphony/messages)\
> [MessageML](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml)\
> [Message ID](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml#message-identifiers)\
> [Message Format - MessageML](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml/message-format-messageml)\
> [PresentationML](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-presentationml)\
> [Message Format - ExtensionML](https://docs.developers.symphony.com/building-extension-applications-on-symphony/overview-of-extension-api/extension-api-services/entity-service/message-format-extensionml)\
> [Colors](https://docs.developers.symphony.com/developer-tools/developer-tools/ui-style-guide/colors)
