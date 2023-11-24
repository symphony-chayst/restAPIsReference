# Follow User

Available on Symphony 20.9 and above. Make a list of users to start following a specific user.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/user/{uid}/follow" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> 🚧 Rules
>
> * The Service Account should have the Role _"User Provisioning"_ in order to make these changes for any user or itself.
> * It is impossible for a user/service account to follow himself. The fact that the user/service account to follow (whose id is the `uid` from path param) is part of the list `followers` will not generate an error in the payload:
>   * a 200 should still be received but the user/service account will not follow himself;
>   * the other users included in the list will however start following the user to be followed (the one whose id is in path param as `uid`).
> * If an invalid user id is part of the list `followers`, then:
>   * a 400 error will be received in the payload mentioning the invalid user id;
>   * the other users included in the list will however start following the user to be followed (the one whose id is in path param as `uid`).
> * The fact that one of the user from the list `followers` already follows the considered user (from the path param as the one to follow) will not generate an error in the payload: a 200 should still be received. The involved user from the `followers` list will continue following the one to be followed.

When calling this as an [OBO-enabled endpoint](../apps-on-behalf-of-obo/obo-enabled-endpoints.md#api-endpoints-enabled-for-obo), use the [OBO User Authenticate](../apps-on-behalf-of-obo/obo-rsa-user-authentication-by-user-id.md) token for `sessionToken`.

> 📘 See also
>
> * [Unfollow User](unfollow-user.md) to make a list of users to stop following a specific user
