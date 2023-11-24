# Blast Message

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v4/message/blast" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

Blast Message enables you to post a new message to a given list of streams (each stream can either be a chatroom, an IM or a multiparty IM).\
It also includes all capabilities and limitations from Create Message V4 endpoint (i.e. using Symphony Elements, Apache FreeMarker Template, etc.)\
_Please check_ [_Create Message V4_](ref:create-message-v4) _where you will find those capabilities and limitations_

Please note that the blast message is not transactional, so you could have some failures sending some messages while others are successfully sent; for this reason, the service returns 200 OK even in case of error (i.e. there is an incorrect stream id within the list of `sids` provided). But in this case, each message failed is detailed.

> 🚧 Known Limitations
>
> * Considering performance purposes for encryption/decryption, the maximum number of stream Ids is set to 100. In case you want to send more messages, you will need to perform multiple requests to the endpoint.
> * See [Create Message V4](ref:create-message-v4) for more information about other limitations

> 📘 See also
>
> [Create Message V4](ref:create-message-v4)\
> [Message](https://docs.developers.symphony.com/building-bots-on-symphony/messages)\
> [MessageML](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml)\
> [Message ID](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml#message-identifiers)\
> [Message Format - MessageML](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml/message-format-messageml)\
> [PresentationML](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-presentationml)\
> [Message Format - ExtensionML](https://docs.developers.symphony.com/building-extension-applications-on-symphony/overview-of-extension-api/extension-api-services/entity-service/message-format-extensionml)\
> [Colors](https://docs.developers.symphony.com/developer-tools/developer-tools/ui-style-guide/colors)\
> [Symphony Elements](https://docs.developers.symphony.com/building-bots-on-symphony/symphony-elements)
