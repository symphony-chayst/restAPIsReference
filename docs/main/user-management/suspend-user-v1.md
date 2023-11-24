# Suspend User Account

Released in Symphony 20.7. This API suspends or re-activates (unsuspend) a user account.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{userId}/suspension/update" method="put" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

### Request Examples

```bash
curl -X PUT \
 'https://devx1.symphony.com/pod/v1/admin/user/12987981107250/suspension/update' \
-H 'sessionToken: SESSION_TOKEN' \
-H 'Content-Type: application/json' \
-d '{
      "suspended": true,
      "suspensionReason": "The user will be OOO due to a mandatory leave",
      "suspendedUntil": 1601546400
    }'
```

```bash
curl -X PUT \
 'https://devx1.symphony.com/pod/v1/admin/user/suspension/update' \
-H 'sessionToken: SESSION_TOKEN' \
-H 'Content-Type: application/json' \
-d '{
      "suspended": false
    }'
```

> 📘 Required Fields
>
> When suspending a user account, `suspended=true`, all three body parameters are required.\
> When activating a user account, `suspended=false`, the other two remaining body parameters are not required.

> 🚧 Required Permissions
>
> Calling this endpoint requires a service account with the User Provisioning role.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and their associated privileges.
