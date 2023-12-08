# Create Datafeed 2

Creates a new real time messages / events stream ("datafeed"). The datafeed provides messages and events from all conversations that the user is in. The types of events surfaced in the datafeed can be found in the [Real Time Events](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/real-time-events) list.

Returns the `ID` of the datafeed that has just been created. This `ID` should then be used as input to the [Read Datafeed](read-datafeed-v5.md) endpoint.

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v5/datafeeds" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}
