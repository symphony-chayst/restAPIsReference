---
description: Returns the list of followers of a specific user.
---

# List User Followers

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/user/{uid}/followers" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 👍 Rules for pagination
>
> * The count indicates the total number of items (e.g. the total number of followers)
> * Considering that ranking indexing starts with 1, the cursor `before` indicates:
>   * _in the request:_ the rank of the last item wished in the payload (we want to show the maximum number of items positioned right before and including this one)
>   * _in the payload:_ the number of items that are present before the first item of the payload
> * Considering that ranking indexing starts with 1, the cursor `after` indicates:
>   * _in the request:_ the rank of the first item wished from the payload + 1 (we want to show the maximum number of items positioned right after and excluding this one)
>   * _in the payload:_ the rank of the last item from the payload. When it is not present, it means that the last item in the payload is the last follower.

> #### 🚧 Notes & limitations
>
> * No specific entitlement is required to call this endpoint, but it is not possible to have access to external users' information:
>   * It is not possible to get the list of followers of an external user;
>   * No external user is included in the list returned by the endpoint.
> * If no `limit` parameter specified in the path of the request, it will be set by default to 100

> #### 📘 See also
>
> * [List Users Followed](list-users-followed.md) to list users who are followed by a specific user
