# Health Check Extended

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v3/health/extended" method="get" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

{% hint style="info" %}
📘 **Result Fields**

This API returns the connectivity status of the Agent services as well as users connectivity. The global status will be set to `DOWN` if at least one of the sub-status is also `DOWN`.\
\
**Agent services**: pod, key manager and datafeed.\
**User connectivity**: agentservice and ceservice
{% endhint %}
