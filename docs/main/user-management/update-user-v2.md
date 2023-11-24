# Update User

Released in 1.51. Updates an existing user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v2/admin/user/{uid}/update" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

### Request Example

```bash
curl -X POST \
https://acme.symphony.com/pod/v1/admin/user/7215545078541/update \
-H "sessionToken: SESSION_TOKEN" \
-H "Content-Type: application/json" \
-d '{   
    "accountType": "NORMAL",
    "firstName": "Jane",
    "lastName": "Doe",
    "username": "janedoe",
    "displayName": "Jane Doe",
    "companyName": "Symphony",
    "department": "",
    "division": "",
    "title": "Sales Manager",
    "workPhoneNumber": "",
    "mobilePhoneNumber": "",
    "twoFactorAuthPhone": "",
    "location": "San Francisco",
    "jobFunction": "Sales",
    "assetClasses": ["Commodities"],
    "industries": ["Basic Materials"],
    "marketCoverage": ["EMEA"],
    "responsibility": ["BAU"],
    "function": ["Trade Management"],
    "instrument": ["Securities"],
    "currentKey": {
        "key":"-----BEGIN PUBLIC KEY-----\nMIICIj...==\n-----END PUBLIC KEY-----",
        "action":"SAVE"
    }    
}'
```

> 📘 Note - Suspension
>
> Since 20.14, `userSystemInfo` from the payload includes suspension info:
>
> * if user is active, then the `suspended` attribute is set to false,
> * if user is suspended, then the `suspended` attribute is set to true and both `suspendedUntil` and `suspensionReason` are as well included in the payload.
>
> _Please note that even if the suspendedUntil date is in the past, the user will remain suspended=true until he first logs on the client after the suspension ended. The suspended info are then automatically updated._\
> See the [Suspend User Account](suspend-user-v1.md) endpoint for more information.

> 🚧 Required Permissions
>
> Calling this endpoint requires the ACCESS\_USER\_PROVISIONING\_API and ACCESS\_ADMIN\_API privileges.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

> ❗️ Known Issues
>
> There is a known bug where the "Industries" and "Asset Classes" fields cannot be cleared once set. For example, if you set `assetClasses` on a user to \[`Conglomerates`, `Healthcare`], you can update the user and set it to \[`Conglomerates`], but you cannot update the user and clear it by setting it to \[].
