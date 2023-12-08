# Read Datafeed 2

Reads the specified datafeed. The datafeed provides messages and events from all conversations that the user is in. The types of events surfaced in the datafeed can be found in the [Real Time Events](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/real-time-events) list.

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v5/datafeeds/{datafeedId}/read" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> 📘 ackId
>
> The `ackId` sent as a parameter can be empty in the first call. In the response, an `ackId` will be sent back and it can be used for the next call. This way, you acknowledge that you have received the events that came with that `ackId` and that the datafeed will remove the events associated with that `ackId` from your queue.
