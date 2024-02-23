# Datahose - Read Events

Creates and reads real time messages / events streams.&#x20;

The datahose API provides messages and events from all conversations in the pod, even the ones the service user is not part of. The types of events surfaced can be found in the [Real Time Events](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/real-time-events) list.

`Not yet available in production. Dependency on Agent 22.6+.`

{% hint style="info" %}
**Add-on:** The Datahose API is an add-on to the Symphony Services, and is subject to additional charges. Prior to using Datahose in your Symphony environment(s), you will need to enter into a specific contract. Please reach out to [sales@symphony.com](mailto:sales@symphony.com) to discuss the offering, its pricing or for any further information.
{% endhint %}

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v5/events/read" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

###

{% hint style="info" %}
Datahose is not yet available in production.
{% endhint %}

{% hint style="warning" %}
**Entitlements:** The service account user needs to have both the **Can read from datahose feeds** and **Can create datahose feeds** entitlements enabled to call this endpoint.
{% endhint %}

### Configuration

The credentials of the Content Export service need to be setup in the Agent configuration for datahose to work.&#x20;

The description of the configuration fields for the Content Export service is available in the [Agent configuration guide](https://docs.developers.symphony.com/admin-guide/agent-guide/agent-configuration-fields#agent-configuration-fields) (look for `agent.privatekey.ceservice` and `agent.certificate.ceservice`).&#x20;

To check that the Content Export is correctly setup, you can test the Agent [health check extended endpoint](../info-health-check/health-check-extended-v3.md) (/agent /v3/health/extended).&#x20;

The value of `users.ceservice.status` should be "UP", see example below.

<pre class="language-json"><code class="lang-json">{
    "services": {
        "datafeed": {
            "status": "UP",
            "version": "2.11.2"
        },
        "key_manager": {
            "status": "UP",
            "version": "20.16.3"
        },
        "pod": {
            "status": "UP",
            "version": "20.16.74-216-100b3be"
        }
    },
    "status": "UP",
    "users": {
        "agentservice": {
            "authType": "RSA",
            "status": "UP"
        },
        "ceservice": {
            "authType": "RSA",
           <a data-footnote-ref href="#user-content-fn-1"> "status": "UP"</a>
        }
    },
    "version": "23.11.1-716"
}
</code></pre>

### Using ackId

The Datahose - Read Events endpoint returns the [Real Time Events](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/real-time-events) happening in the pod, either since the time the datahose feed was created or since the previous feed was read by the bot. The `ackId` has an essential role in retrieving the right events for the bot.

The ackId should indeed be null or empty for the first call. Then, for subsequent requests, the ackId from the previous payload should be reused to confirm the reading of previous events already retrieved by the bot.\
_Please note that you can very easily access this API via our BDKs in Java and Python._

_If a batch of messages is not confirmed by sending the `ackId`, the messages that are there will be returned in the subsequent readings and may blend into the newer messages._

### Fair use policy

Datahose API is subject to a fair use policy of **5** active feeds.&#x20;

If your integration or workflow require more than 5 feeds active at the same time, please contact Symphony.

[^1]: Status of ceservice should be UP
