---
description: Returns the userId of the calling user.
---

# Session User

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v2/sessioninfo" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/obo-enabled-endpoints.md#api-endpoints-enabled-for-obo):

* Use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.
* An OBO application must include the Primary User Identity (GET\_BASIC\_USER\_INFO) permission, along with all other required authentication and permissions. See [App Authenticate](../apps-on-behalf-of-obo/obo-rsa-app-authentication.md) and [OBO-Enabled Endpoints](../apps-on-behalf-of-obo/obo-enabled-endpoints.md#api-endpoints-enabled-for-obo).

See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
