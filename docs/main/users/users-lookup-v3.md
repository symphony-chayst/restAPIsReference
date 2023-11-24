# Users Lookup

Released in 1.50. Search users by emails, ids or username.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v3/users" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

### Request Examples

```bash
curl -X GET \
  'https://acme.symphony.com/pod/v3/users?uid=7696581394433,7696581394434&local=true' \
   -H 'SessionToken: SESSION_TOKEN' \
```

```bash
curl -X GET \
'https://cip3-qa.symphony.com/pod/v3/users?email=test_1@symphony.com,test_2@symphony.com&local=true' \
 -H 'SessionToken: SESSION_TOKEN' \
```

```bash
curl -X GET \
  'https://cip3-qa.symphony.com/pod/v3/users?username=test_1,test_2&local=true' \
   -H 'SessionToken: SESSION_TOKEN' \
```

The caller can specify whether to search locally (within the caller's company) or globally across companies that have enabled external communications.

To search for external users, the parameter `local` needs to be set as **false** and the service account has to be enabled externally. To do so, make sure at least one of the two following external entitlements are enabled, otherwise, the search will return zero results.\
• Can chat in external IM/MIMs\
• Can chat in private external rooms

By default, searches are performed externally. Set `local=true` to search locally.

### Searching external users by email

The service account is allowed to search for users using their registered email even without having a previous connection with them.

### OBO enabled endpoint

When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/obo-enabled-endpoints.md#api-endpoints-enabled-for-obo), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.

### Xpod entitlements set

The callers need to have the xpod (cross-company) entitlements set, otherwise, the API will return a 204 error (no content).

> 🚧 Rules & Limitations
>
> * Please note that the endpoint returns only the first 1000 entries.

> 📘 Note
>
> **Search list sizes:** search lists may contain up to 100 elements.\
> **Inactive users:** the results will include inactive users.\
> **Account type:** the `accountType` field returns `NORMAL` if the user is a user account and `SYSTEM` if the user is a service account.\
> **User department, location, title and email:** the `department`, `location`, `title` and `emailAddress` fields are returned only if the user is an internal user of the current pod. When searching between cross-pods, these fields will not be returned.
