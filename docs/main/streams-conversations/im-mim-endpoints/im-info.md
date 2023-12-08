# IM Info

Returns information about a particular IM conversation.

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/im/{id}/info" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 📘 Stream ID
>
> The stream ID can be located in the Symphony web or desktop client by clicking on the timestamp of any message in the conversation. This will open the Message Status module overlay, and the Conversation ID can be found in the overlay footer.
>
> The stream ID in the UI is in Standard Base64 encoding. When the stream ID needs to be used in a URL, it should be in URLSafe Base64 encoding. To obtain the URLSafe Base64 stream ID, replace forward slashes with underscores, replace pluses with minuses, and ignore any trailing equal signs.
>
> See [Overview of streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for details.

> #### 🚧 Required Permissions
>
> Streams information can only be requested by:
>
> * Members of the IM
> * Compliance Officers and Super Compliance Officers who are not members of the stream
> * Service Users with the User Provisioning role (members or not members of the stream)
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
