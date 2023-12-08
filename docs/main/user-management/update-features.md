# Update User Features

Updates the feature entitlements for a particular user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/user/{uid}/features/update" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

### Request Example

```bash
curl -X POST \
https://acme.symphony.com/pod/v1/admin/user/7215545057281/features/update \
-H "sessionToken: SESSION_TOKEN" \
-H "Content-Type: application/json" \
-d '[
  {
    "entitlment": "canCreatePublicRoom",
    "enabled": true
  },
  {
    "entitlment": "isExternalRoomEnabled",
    "enabled": true
  },
  {
    "entitlment": "delegatesEnabled",
    "enabled": true
  },
  {
    "entitlment": "isExternalIMEnabled",
    "enabled": true
  },
  {
    "entitlment": "sendFilesEnabled",
    "enabled": true
  },
  {
    "entitlment": "canUpdateAvatar",
    "enabled": true
  }
]'
```

> #### 🚧 Required Permissions
>
> Calling this endpoint requires the User Provisioning role with `ACCESS_USER_PROVISIONING_API` privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

### Updating User Entitlements in Bulk

* When updating a large number of users, Symphony recommends parallelizing calls to this endpoint, typically to perform up to 300 calls concurrently.
* To reduce the effects of network latency, Symphony recommends executing these calls on a server in close geographic proximity to your pod.
