# Update IM

`Released in 20.13.`

Updates the attributes of an existing IM.

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/im/{id}/update" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

Returns an error when:

* The call doesn’t include an update to at least one editable attribute.

> 📘 Stream ID
>
> The stream ID can be located in the Symphony web or desktop client by clicking on the timestamp of any message in the conversation. This will open the Message Status module overlay, and the Conversation ID can be found in the overlay footer.
>
> The stream ID in the UI is in Standard Base64 encoding. When the stream ID needs to be used in a URL, it should be in URLSafe Base64 encoding. To obtain the URLSafe Base64 stream ID, replace forward slashes with underscores, replace pluses with minuses, and ignore any trailing equal signs.
>
> Note: visit [Overview of streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for more information.

> 🚧 Attributes
>
> * The `pinnedMessageId` attribute allows to display an exact copy of the original message in a pinned area placed beneath the chat header and that remains always visible to all users. From this area, they can interact with the message content (i.e. forms or ui actions buttons), and they are able to automatically jump to the original message in the chat canvas. You can use this attribute as follows:
>   * either by entering the URLSafe Base 64 ID of the message you wish to pin beneath the chat header (as you can see in the example). Even if another message is pinned, this new message will replace it in the pinned area;
>   * either by entering an empty value as follows: "pinnedMessageId": "". This is used to upin any message and remove therefore this area from being visible to users;
>   * _Please note that, in an IM, users can only perform unpinning action._
