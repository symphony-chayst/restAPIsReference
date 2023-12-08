---
description: Make a list of users to stop following a specific user.
---

# Unfollow User

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/user/{uid}/unfollow" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 🚧 Rules
>
> * The Service Account should have the Role _"User Provisioning"_ in order to make these changes for any user or itself.
> * It is impossible for a user/service account to follow himself. The fact that the user/service account to unfollow (whose id is the `uid` from path param) is part of the list `followers` will not generate an error in the payload:
>   * a 200 should still be received and nothing will happen regarding the affected user/service account;
>   * the other users included in the list will however stop following the user to be unfollowed (the one whose id is in path param as `uid`).
> * If an invalid user id is part of the list `followers`, then:
>   * a 400 error will be received in the payload mentioning the invalid user id;
>   * the other users included in the list will however stop following the user to be unfollowed (the one whose id is in path param as `uid`).
> * The fact that one of the user from the list `followers` does not follow the considered user (whose id is the `uid` from path param as the one to unfollow) will not generate an error in the payload: a 200 should still be received. The involved user from the `followers` list will still be out of the list of followers of the user to unfollow.

When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/obo-enabled-endpoints.md#api-endpoints-enabled-for-obo), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.

> #### 📘 See also
>
> * [Follow User](follow-user.md) to make a list of users to start following a specific user
