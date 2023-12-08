# Search Users

Search for end-users, bots or distribution lists (groups) by first name, last name, display name, and email, and filter results by company, title, location, marketCoverage, responsibility, function, or instrument.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/user/search" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

### Request Example

```bash
curl -X POST \
https://acme.symphony.com/pod/v1/user/search?local=false \
-H "sessionToken: SESSION_TOKEN" \
-H "Content-Type: application/json"  \
-d '{
  "query": "jane",
  "filters": {
    "title": "Sales Manager",
    "location": "San Francisco",
    "company": "Symphony",
    "marketCoverage":"EMEA",
    "responsibility":"BAU",
    "function":"Trade Management",
    "instrument":"Securities",
    "accountTypes":["NORMAL","SDL"]
  }
}'
```

> #### 📘 Note
>
> * This endpoint can return inexact matches of the specified criteria, while [Find Users](../user-management/find-users.md) returns only exact matches.
> * Account type:
>   * The `accountType` field can contain a list of strings with the following supported values: `NORMAL`, `SYSTEM`, or `SDL`. Please note that if this is not specified, then the default search will return `NORMAL` and `SYSTEM` users in the payload.
>   * The `accountType` field returns `NORMAL` if the user is a user account, `SYSTEM` if the user is a service account, or `SDL` if the user is a Symphony Distribution List (Groups).\
>     **User location, title and email:** the `location`, `title` and `emailAddress` fields are returned only if the user is an internal user of the current pod. When searching between cross-pods, these fields will not be returned.

The caller can specify whether to search locally (within the caller's company) or globally across companies that have enabled external communications.

To search for external users, the parameter **local** needs to be set as **false** and the service account has to be enabled externally. To do so, make sure at least one of the two following external entitlements are enabled, otherwise, the search will return zero results.\
• Can chat in external IM/MIMs\
• Can chat in private external rooms

By default, searches are performed externally. Set `local=true` to search locally.

### Searching external users by email

The service account is allowed to search for users using their registered email even without having a previous connection with them.

### OBO enabled endpoint

When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/obo-enabled-endpoints.md#api-endpoints-enabled-for-obo), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.
