# Get Message

Available on Agent 2.53.3 and above. Returns details about the specified message.

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v1/message/{id}" method="get" expanded="true" fullWidth="true" %}
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
