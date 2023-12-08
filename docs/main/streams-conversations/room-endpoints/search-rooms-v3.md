---
description: Search for rooms, querying name, description, and specified keywords.
---

# Search Rooms

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v3/room/search" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 📘 Room Search Scope
>
> Room search is performed on the set of:
>
> * All rooms that the calling user is a member of (private or public, active or inactive)
> * All active public rooms
> * Private rooms that the calling user is not a member of, where the room is set to be visible in search, is active and the room does not contain any user with whom the calling user has an information barrier
>
> Note: visit [Overview](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for an overview of streams.

> #### 🚧 Room Description Search
>
> The description is only searched for hashtags and cashtags containing the search query. For example if `query` were `foo` and the description of a room contained "foo", this room would not be returned in the search results; however, if the description contained "#foo", this room would be returned in the search results.
