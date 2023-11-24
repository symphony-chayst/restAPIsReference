# Attachment

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v1/stream/{sid}/attachment" method="get" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> 🚧 Note
>
> A successful call returns the attachment body encoded in Base64. Be sure to decode the downloaded attachment.

> 📘 Attachments
>
> * Anyone can download attachments from public rooms or rooms with _viewHistory_ enabled.
> * The Content Export service user is able to download attachments even from rooms he is not a member of.

