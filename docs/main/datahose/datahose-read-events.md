# Datahose - Read Events

`Not yet available in production. Dependency on Agent 22.6+.`\
Creates and reads real time messages / events streams.&#x20;

The datahose API provides messages and events from all conversations in the pod, even the ones the service user is not part of. The types of events surfaced can be found in the [Real Time Events](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/real-time-events) list.

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v5/events/read" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

> 🚧 Datahose is not yet available in production

> 📘 Add-on
>
> The Datahose API is an add-on to the Symphony Services, and is subject to additional charges. Prior to using Datahose in your Symphony environment(s), you will need to enter into a specific contract. Please reach out to [sales@symphony.com](mailto:sales@symphony.com) to discuss the offering, its pricing or for any further information.

### Using ackId

The Datahose - Read Events endpoint returns the [Real Time Events](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/real-time-events) happening in the pod, either since the time the datahose feed was created or since the previous feed was read by the bot. The `ackId` has an essential role in retrieving the right events for the bot.

The ackId should indeed be null or empty for the first call. Then, for subsequent requests, the ackId from the previous payload should be reused to confirm the reading of previous events already retrieved by the bot.\
_Please note that you can very easily access this API via our BDKs in Java and Python._

_If a batch of messages is not confirmed by sending the `ackId`, the messages that are there will be returned in the subsequent readings and may blend into the newer messages._

> 🚧 Required Entitlements
>
> The service account user needs to have both the **Can read from datahose feeds** and **Can create datahose feeds** entitlements enabled to call this endpoint.
