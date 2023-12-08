---
description: Creates a new Signal.
---

# Create Signal

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v1/signals/create" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

### Request Example

```bash
curl -X POST \  
  https://acme.symphony.com/agent/v1/signals/create \
  -H 'content-type: application/json' \
  -H 'keymanagertoken: KEYMANAGER_TOKEN' \
  -H 'sessiontoken: SESSION_TOKEN' \
  -d '{
	  "name": "hash and cash",
	  "query": "HASHTAG:hash AND CASHTAG:cash",
	  "visibleOnProfile": true,
    "companyWide": false
  }'
```

> 🚧 Known Limitations
>
> * DLP only works with 1.53 version and onwards.
> * To create a company-wide signal, the requesting user needs to have the `canCreatePushedSignals` entitlement.
> * To send numeric cashtags as signals, add a `*` before the number, for example, `$*122450`.
