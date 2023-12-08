---
description: Removes a role or optional entitleable action from a user’s account.
---

# Remove Role

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{uid}/roles/remove" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

### Request Example

```bash
curl -X POST \
  https://acme.symphony.com/pod/v1/admin/user/346147139412345/roles/remove \
  -H 'cache-control: no-cache' \
  -H 'content-type: application/json' \
  -H 'sessiontoken: SESSION_TOKEN' \
  -d '{"id" : "L2_SUPPORT"}'
```

If you remove a role from a user’s account, all optional entitleable actions that are associated with that role and assigned to the user are also removed. For example, removing `COMPLIANCE_OFFICER` also removes `COMPLIANCE_OFFICER.MONITOR_ROOMS` and `COMPLIANCE_OFFICER.MONITOR_WALL_POSTS`.

To remove only the optional entitleable action and retain the role, call this endpoint with the complete {roleID}.{optionalEA} value in `payload`. For example, removing `COMPLIANCE_OFFICER.MONITOR_ROOMS` disables the user’s ability to monitor rooms but retains his or her role as a compliance officer.

> #### 🚧 Required Permissions
>
> Calling this endpoint requires the User Provisioning role with `ACCESS_USER_PROVISIONING_API` privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
