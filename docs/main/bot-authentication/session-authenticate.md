---
description: >-
  Authenticates the API caller on the Symphony servers (pod) using the client
  certificate provided in the TLS session, returning a session token.
---

# Session Authenticate (Cert)

{% swagger src="../../.gitbook/assets/authenticator-api-public.yaml" path="/v1/authenticate" method="post" expanded="true" fullWidth="true" %}
[authenticator-api-public.yaml](../../.gitbook/assets/authenticator-api-public.yaml)
{% endswagger %}

> #### ❗️ Session Token Management
>
> The token you receive is valid for the lifetime of a session that is defined by your pod's administration team. This ranges from 1 hour to 2 weeks.
>
> You should keep using the same token until you receive a HTTP 401, at which you should re-authenticate and get a new token for a new session.
>
> [Datafeeds](../datafeed/) survive session expiration, you do not need to re-create your datafeed if your session expires.

To call the Session Authenticate endpoint, you must provide a certificate where the Common Name of the certificate matches the username of an active Service User account on your pod.

> #### 🚧 Important
>
> * Before calling any of the Pod or Agent API endpoints, the caller must be authenticated on both the pod and key manager by calling this endpoint, followed by the [Key Manager Authenticate](rsa-key-manager-authenticate.md) endpoint.
>
> The certificate used for authentication (and therefore the Root certification) must have a strength of 4096 bits, or the cert will be rejected
>
> * Symphony prevents bots from calling this endpoint when the following conditions are true:
> * An application and a bot have the same name.
> * The application specifies a [valid certificate in its manifest file](https://docs.developers.symphony.com/building-extension-applications-on-symphony/app-configuration/application-manifest-bundle-file-reference).
> * The application is enabled and not marked for deletion. For more information about enabling and deleting applications, see the _Symphony Administration Guide_.

_Note that the Session Authenticate endpoint may return an authorizationToken (short lived access token built from a user session) in addition to the session token. Please note this has been introduced as beta and should not be used until further notice; please continue using the returned "token" instead._
