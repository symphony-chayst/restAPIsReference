---
description: >-
  Authenticates the API caller on the key manager using the client certificate
  provided in the TLS session, returning a key manager token.
---

# Key Manager Authenticate (Cert)

{% swagger src="../../.gitbook/assets/km-cert-api-public.yaml" path="/v1/authenticate" method="post" %}
[km-cert-api-public.yaml](../../.gitbook/assets/km-cert-api-public.yaml)
{% endswagger %}

> #### ❗️ Key Manager Token Management
>
> The token you receive is valid for the lifetime of a session that is defined by your pod's administration team. This ranges from 1 hour to 2 weeks.
>
> You should keep using the same token until you receive a HTTP 401, at which you should re-authenticate and get a new token for a new session.
>
> [Datafeeds](../datafeed/) survive session expiration, you do not need to re-create your datafeed if your session expires.

> #### 🚧
>
> Before calling the Pod endpoints, the caller must be authenticated with the pod (the dedicated Symphony cloud service) by calling the [Session Authenticate](rsa-session-authenticate.md) endpoint, followed by this one.

To call the Key Manager Authenticate endpoint, you must provide a certificate where the Common Name of the certificate matches the username of an active Service User account on your pod.
