# List Streams for Enterprise

`Released in 1.50`

Returns a list of all the streams (IMs, MIMs, chatrooms, Wall posts as well as streams reserved for internal use) for the calling user's company, sorted by creation date (ascending – oldest to newest).&#x20;

**Filtering** parameters can be used to narrow the list of streams that are returned. For more information, refer to the **Filtering Returned Streams** section below.

{% swagger src="../../../.gitbook/assets/pod-api-public.yaml" path="/v2/admin/streams/list" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

### Request Example

```bash
curl -X POST \
https://acme.symphony.com/pod/v2/admin/streams/list \
    -H 'Content-Type: application/json' \ 
    -H 'sessionToken: SESSION_TOKEN' \ 
    -d '{
          "streamTypes": [
            {"type": "IM"},
            {"type": "MIM"},
            {"type": "ROOM"},
            {"type": "POST"}
          ]
        }'
```

> 🚧 Required Permissions
>
> This endpoint may only be called by Service User accounts with the User Provisioning role.

Note: visit [Overview](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for an overview of streams.

### Filtering Returned Streams

You can filter the streams that are returned by specifying optional body parameters.

For instance, the filter below would return active external chatrooms created by users who do not belong to your firm, created between Mon, 12 Dec 2016 20:37:36.047 GMT and Thu, 29 Dec 2016 19:01:29.833 GMT.

```json
{
	"streamTypes": [{"type": "ROOM"}],
	"scope": "EXTERNAL",
	"origin": "EXTERNAL",
	"privacy": "PRIVATE",
	"status": "ACTIVE",
	"startDate": 1481575056047,
	"endDate": 1483038089833
}
```

> 📘 lastMessageDate
>
> This is the date that the last message was sent in that room. The time is in epoch format.

> 📘 Scope vs. Origin
>
> The `scope` property refers to the participants of the room: whether the room contains only users within the company (internal scope) or whether the room contains users within the company as well as users belonging to another company (external scope). The scope property can apply to IMs and MIMs as well.
>
> The `origin` property applies only to rooms with external scope. Origin refers to the creator of the room with external scope: whether the room was created by a user of the company (internal origin) or whether the room was created by a user belonging to another company (external origin).
>
> A room with external scope and internal origin would be a room created by a user within the company, where members can belong to both the origin company and one other company.
>
> The response has defined variable "isExternal", and for external scope, can have two values {true, false}. This value is false, whenever the stream is created by an internal user.

> 📘 Privacy
>
> The `privacy` property applies only to rooms with internal scope. It refers to the privacy setting of the internal room: whether members (who must belong to the same company) must be added to the room or whether anyone in the company can find and join the room.
>
> External rooms are always private - members must be added to the room.

> 📘 Date Range Filter
>
> The `startDate` and `endDate` properties can be used to filter the list of streams to return only streams that were modified within the specified time range.
>
> For rooms, modification entails a change of room properties (ex. name or description updated, settings changed) or a change in room membership (ex. users added/removed, roles changed). Modification does not include message activity.
>
> IMs and MIMs are immutable - there can be no membership changes or properties changes. Therefore, filtering is performed upon the stream creation date.
>
> If neither `startDate` nor `endDate` are specified, all rooms since the beginning of the enterprise's time until the time of call are returned.
>
> If `startDate` is specified, but not endDate, all rooms modified since the startDate until the time of call are returned.
>
> If `endDate` is specified, but not `startDate`, all rooms modified since the beginning of the enterprise's time until the endDate are returned.
