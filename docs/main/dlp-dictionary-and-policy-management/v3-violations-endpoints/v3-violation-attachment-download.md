---
description: >-
  Available on Agent 2.53.0 and above. See the SBE x Agent compatibilities for
  more details about the minimal requirements. API for downloading attachments
  sent as part of messages flagged by DLP system
---

# V3 Violation Attachment Download

{% swagger src="../../../.gitbook/assets/agent-api-public.yaml" path="/v3/dlp/violation/attachment" method="get" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> ### 🚧 Important
>
> A successful call returns the attachment body encoded in Base64. Be sure to decode the downloaded attachment.
