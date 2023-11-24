# Add Role

Released in 1.47. Adds a role or optional entitleable action to a user’s account.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{uid}/roles/add" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

### Request Example

```bash
curl -X POST \
	https://acme.symphony.com/pod/v1/admin/user/346147139412345/roles/add \
  -H 'cache-control: no-cache' \
	-H 'content-type: application/json' \
	-H 'sessiontoken: SESSION_TOKEN' \
	-d '{"id":"COMPLIANCE_OFFICER"}'
```

> 🚧 Required Permissions
>
> Calling this endpoint requires the User Provisioning role with `ACCESS_USER_PROVISIONING_API` privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
