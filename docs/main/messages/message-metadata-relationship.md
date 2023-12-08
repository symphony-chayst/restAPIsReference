---
description: >-
  Gets the message metadata relationship. This API allows users to track the
  relationship between a message and all the forwards and replies of that
  message.
---

# Message Metadata

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/messages/{messageId}/metadata/relationships" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

> #### 📘 Message Relationship
>
> The Message Metadata API returns information about the current message relationships (parent, replies, forwards and form replies).

> #### 🚧 Required Roles
>
> Calling this endpoint requires the Content Management role.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
