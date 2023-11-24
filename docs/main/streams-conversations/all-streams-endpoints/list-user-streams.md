# List User Streams

`Released prior to 1.43.`

Returns a list of all the streams of which the requesting user is a member, sorted by creation date (ascending - oldest to newest).

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v1/streams/list" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

### Request Example

```curl
curl -X POST \
https://acme.symphony.com/pod/v1/streams/list \
-H "sessionToken: SESSION_TOKEN" \
-H "Content-Type: application/json" \
-d '{
	"streamTypes": [
  	{"type": "IM"},
    {"type": "MIM"},
    {"type": "ROOM"},
    {"type": "POST"}
  ],
  "includeInactiveStreams": true
}'
```

### streamTypes

`streamTypes`: A list of stream types (defined as an object) that will be returned. Options are IM (1-1 instant messages), MIM (multiparty instant messages), ROOM (rooms), POST (the user's wall).

```json
{
	"streamTypes": [
    {"type": "IM"}, 
    {"type": "MIM"}, 
    {"type": "ROOM"}, 
    {"type": "POST"}
  ],
	"includeInactiveStreams": true
}
```

> 📘 Overview of streams
>
> A stream is like a container for messages exchanged between two or more users via a given instant message (IM), multi-party instant message (MIM), or chat room. For more information, refer to [Overview of streams](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams).
