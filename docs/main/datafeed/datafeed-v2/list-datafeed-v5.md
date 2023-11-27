# List Datafeed v2

`Available on Agent 2.57.0 and above.`

The datafeed provides messages and events from all conversations that the user is in. The types of events surfaced in the datafeed can be found in the [Real Time Events](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/real-time-events) list.&#x20;

Returns the list of datafeeds for the user. Any datafeed ID of the list can then be used as input to the [Read Datafeed](read-datafeed-v5.md) endpoint.

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v5/datafeeds" method="get" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}
