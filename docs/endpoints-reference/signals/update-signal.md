# Update Signal

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v1/signals/{id}/update" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

### Request Example

```bash
curl -X POST \
  https://acme.symphony.com/agent/v1/signals/5a8da7edb9d82100011d508f/update \
  -H 'content-type: application/json' \
  -H 'sessiontoken: SESSION_TOKEN' \
  -H 'keymanagertoken: KEYMANAGER_TOKEN' \
  -d '{
    "name": "hashtag only",
    "query": "HASHTAG:hash",
    "visibleOnProfile": false,
    "companyWide": false
   }'
```

> 🚧 Known Limitations
>
> * To update a company-wide signal, the requesting user needs to have the `canCreatePushedSignals` entitlement.
> * To update a normal signal, the requesting user needs to be the owner of the signal.
> * To send numeric cashtags as signals, add a `*` before the number, for example, `$*122450`.
