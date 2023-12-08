# Subscribe Signal

Subscribe an array of users to a Signal. To subscribe an entire pod to a Signal, set the `companyWide` field in [Create Signal](create-signal.md).

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v1/signals/{id}/subscribe" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

### Request Examples

```bash
curl -X POST \
https://acme.symphony.com/agent/v1/signals/5a6efc9db9d8210001b9960b/subscribe \
  -H 'content-type: application/json' \
  -H 'sessiontoken: SESSION_TOKEN' \
  -H 'keymanagertoken: KEYMANAGER_TOKEN' \   
  -d '[68719476759, 68719476760, 68719476761]'
```

```bash
curl -X POST
  -H 'content-type: application/json'
  -H 'sessiontoken: SESSION_TOKEN'
  -H 'keymanagertoken: KEYMANAGER_TOKEN'  
  https://acme.symphony.com/agent/v1/signals/5a6efc9db9d8210001b9960b/subscribe
```

> #### 🚧 Required Permissions
>
> To subscribe other users to a specific signal, the requesting user needs to have the `canManageSignalSubscription` entitlement.
