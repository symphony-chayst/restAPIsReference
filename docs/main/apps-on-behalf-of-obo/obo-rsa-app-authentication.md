# App Authentication

Released in 1.53. Authenticates an OBO app using the application saved RSA public key.

{% swagger src="../../.gitbook/assets/login-api-public.yaml" path="/pubkey/app/authenticate" method="post" expanded="true" fullWidth="true" %}
[login-api-public.yaml](../../.gitbook/assets/login-api-public.yaml)
{% endswagger %}

> #### 📘 Requirements
>
> This authentication requires the app to be enabled and to have at least one RSA Public key registered. For more information, refer to [Create an RSA Key Pair](https://docs.developers.symphony.com/building-bots-on-symphony/authentication/rsa-authentication#1-create-an-rsa-key-pair).
