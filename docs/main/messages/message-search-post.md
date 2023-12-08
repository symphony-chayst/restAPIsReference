---
description: >-
  Searches for messages in the context of a specified user, given an
  argument-based query.
---

# Message Search

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v1/message/search" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

### Request Example

```bash
curl -X POST https://acme.symphony.com/agent/v1/message/search \
    -H "sessionToken: SESSION_TOKEN" \
    -H "keyManagerToken: KEYMANAGER_TOKEN" \
    -H "Content-Type: application/json" \
    -d '{ "hashtag":"newWorld" }'
```

> #### 📘 Optional attributes returned
>
> Note that some attributes are returned in the payload only under specific conditions:
>
> * `sharedMessage` only when the message represented by this class is a wall post sharing another message;
> * `initialMessageId`, `initialTimestamp`, and `replacing` only when the corresponding message is sent as an update to another message thanks to [Update Message](update-message-v4.md) endpoint. Note that the first two attributes relate to the original (and therefore first) message sent, whereas the `replacing` attribute relates to the message that has been updated by this message;
> * `replacedBy` only when this message has been updated by a new message. It contains the id of the replacing message.
> * `parentMessageId` only when this message is a reply or a forward of another message which id is returned in this attribute.

### Search Query Arguments

The `query` parameter supports the following combination of arguments. When multiple arguments are supported, the search results are the union of all query arguments. Only a certain combination of arguments is supported.

* At least one argument in the list is required.
* Arguments names and values are case-insensitive.
* The same argument cannot be used multiple times.
* Search terms cannot contain the following reserved characters: colon `:`, parentheses `( )` and whitespaces (except when applying multi-word text search. See the `text` argument in the table below).
* `fromDate`, `toDate`, `mention`, and `author` are integers. All other arguments are strings.

<table><thead><tr><th width="149">Argument</th><th>Usage</th><th>Comment</th></tr></thead><tbody><tr><td><code>hashtag</code></td><td>Searches for a specific hashtag across messages to or in a specific <code>streamType</code></td><td><ul><li>Can be used in conjunction with <code>cashtag</code> or <code>mention</code>.</li><li>Can be used in conjunction to <code>author</code> or <code>text</code> only for a specific <code>streamType</code></li></ul></td></tr><tr><td><code>cashtag</code></td><td>Searches for a specific cashtag across all messages or in a specific <code>streamType</code></td><td><ul><li>Can be used in conjunction with <code>hashtag</code> or <code>mention</code>.</li><li>Can be used in conjunction to <code>author</code> or <code>text</code> only for a specific <code>streamType</code></li></ul></td></tr><tr><td><code>mention</code></td><td>Searches for a specific user mention, by user id, across all messages or in a specific <code>streamType</code></td><td><ul><li>Can be used in conjunction with <code>hashtag</code> or <code>cashtag</code>.</li><li>Can be used in conjunction to <code>author</code> or <code>text</code> only for a specific <code>streamType</code></li></ul></td></tr><tr><td><code>author</code></td><td>Searches for a specific message author, by user id, across all messages or for a specific <code>streamType</code></td><td>(<em>1.52 and later</em>) You can now search for an <code>author</code> in conjunction with a specific <code>streamType</code></td></tr><tr><td><code>text</code></td><td>Searches for plain text field in a specific message, not including any hashtag, cashtag or user mention.</td><td><ul><li>Requires a <code>streamId</code> to be provided.</li><li>Searching for text across all messages or a specific <code>streamType</code> is not supported.</li><li>Multi-word search is allowed.<br>Syntax: <code>"text":"Hello World"</code></li></ul></td></tr><tr><td><code>streamType</code></td><td>Searches for messages in a specific stream type, either:<br>• <code>CHAT</code> (1-1 instant messages and multi-party instant messages),<br>• <code>IM</code> (1-1 instant message),<br>• <code>MIM</code> (multi-party instant message),<br>• <code>ROOM</code>, or<br>• <code>POST</code> (user profile wall posts).</td><td>Can be used in conjunction with <code>author</code>, <code>hashtag</code>, <code>cashtag</code> or <code>mention</code></td></tr><tr><td><code>streamId</code></td><td>Searches for messages in a specific stream. See <a href="doc:room-id">Conversation ID</a> for streamId format.</td><td>Can be used in conjunction with <code>hashtag</code>, <code>cashtag</code>, <code>mention</code>, <code>text</code> or <code>author</code></td></tr><tr><td><code>signal</code></td><td>Search for messages matching this signal.</td><td>Can only be combined with date filtering and paging parameters.</td></tr></tbody></table>

### Date selector

The `query`parameter can optionally support the following date selectors:

* `fromDate`: selects messages sent after `fromDate`. Supported for all query parameters above.
* `toDate`: selects messages sent before `toDate`. Supported for all query parameters above.\
  The date selector parameter is inclusive: a message sent at exactly the same time as the query `fromDate` will be included in the results.

> #### 📘 See also
>
> [Message](https://docs.developers.symphony.com/building-bots-on-symphony/messages)\
> [MessageML](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml)\
> [Message ID](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml#message-identifiers)\
> [Message Format - MessageML](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-messageml/message-format-messageml)\
> [PresentationML](https://docs.developers.symphony.com/building-bots-on-symphony/messages/overview-of-presentationml)\
> [Message Format - ExtensionML](https://docs.developers.symphony.com/building-extension-applications-on-symphony/overview-of-extension-api/extension-api-services/entity-service/message-format-extensionml)\
> [Colors](https://docs.developers.symphony.com/developer-tools/developer-tools/ui-style-guide/colors)\
> [Symphony Elements](https://docs.developers.symphony.com/building-bots-on-symphony/symphony-elements)

> #### 🚧
>
> The messages returned by this endpoint follow the permissions required by the [Messages](messages-v4.md) endpoint.
