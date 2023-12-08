---
description: >-
  Share third-party content, such as a news article, into the specified stream.
  The stream can be a chat room or an IM.
---

# Share Content

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v3/stream/{sid}/share" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

### Request Example

```url
curl -X POST \
https://acme.symphony.com/agent/v3/stream/7w68A8sAG_qv1GwVc9ODzX___ql_RJ6zdA/share \
-H "sessionToken: SESSION_TOKEN" \
-H "keyManagerToken: KEY_MANAGER_TOKEN" \
-H "Content-Type: application/json" \
-d '{
   "type": "com.symphony.sharing.article",
   "content":{
        "articleId":"tsla",
        "title": "The Secret'"'"'s Out: Tesla Enters China and Is Winning",
        "description": "Check this out",
        "publisher": "Capital Market Laboratories",
        "thumbnailUrl": "http://www.cmlviz.com/cmld3b/images/tesla-supercharger-stop.jpg",
        "author": "OPHIRGOTTLIEB",
        "articleUrl": "http://ophirgottlieb.tumblr.com/post/146623530819/the-secrets-out-tesla-enters-china-and-is",
        "summary": "Tesla Motors Inc. (NASDAQ:TSLA) has a CEO more famous than the firm itself, perhaps. Elon Musk has made some bold predictions, first stating that the firm would grow sales from 50,000 units in 2015 to 500,000 by 2020 powered by the less expensive Model 3 and the massive manufacturing capability of the Gigafactory.",
        "appId": "ticker",
        "appName": "Market Data Demo",
        "appIconUrl": "https://apps-dev.symphony.com/ticker/assets/images/logo.png"
    }
}'
```

> #### 📘 Note
>
> Visit [Overview](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/overview-of-streams) for an overview of streams.

> #### 🚧 Roles and Privileges
>
> For not public rooms, the caller needs to be on the stream or have the Content Management role.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.

### Content Fields

<table><thead><tr><th width="179">Parameter</th><th width="85">Type</th><th width="140">Required</th><th>Description</th></tr></thead><tbody><tr><td><code>articleId</code></td><td>string</td><td>Yes, if <code>articleUrl</code> not specified</td><td>A unique ID for this article, not used by any other article</td></tr><tr><td><code>title</code></td><td>string</td><td>Yes</td><td>The title of the article</td></tr><tr><td><code>subTitle</code></td><td>string</td><td>No</td><td>The subtitle of the article</td></tr><tr><td><code>message</code></td><td>string</td><td>No</td><td>The message text that can be sent along with the shared article</td></tr><tr><td><code>publisher</code></td><td>string</td><td>Yes</td><td>Publisher of the article</td></tr><tr><td><code>publishDate</code></td><td>string</td><td>No</td><td>Article publish date in unix timestamp (in seconds)</td></tr><tr><td><code>thumbnailUrl</code></td><td>string</td><td>No</td><td>URL to the thumbnail image</td></tr><tr><td><code>author</code></td><td>string</td><td>Yes</td><td>Author of the article</td></tr><tr><td><code>articleUrl</code></td><td>string</td><td>Yes, if <code>articleId</code> not specified</td><td>URL to the article</td></tr><tr><td><code>summary</code></td><td>string</td><td>No</td><td>Preview summary of the article</td></tr><tr><td><code>appId</code></td><td>string</td><td>Yes</td><td>App ID of the calling application</td></tr><tr><td><code>appName</code></td><td>string</td><td>No</td><td>App name of the calling application</td></tr><tr><td><code>appIconUrl</code></td><td>string</td><td>No</td><td>App icon URL of the calling application</td></tr></tbody></table>
