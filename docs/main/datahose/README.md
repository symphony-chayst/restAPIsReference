# Datahose - Event Stream

Datahose is a data streaming service, that gives access to all messages and events in real time.

> 🚧 Datahose is not yet available in Production

> 📘 Add-on
>
> The Datahose API is an add-on to the Symphony Services, and is subject to additional charges. Prior to using Datahose in your Symphony environment(s), you will need to enter into a specific contract. Please reach out to [sales@symphony.com](mailto:sales@symphony.com) to discuss the offering, its pricing or for any further information.

Similarly to [Datafeed 2.0](../datafeed/datafeed-v2/), Datahose allows a service user account (bot) to retrieve [Real Time Events](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/real-time-events) including all chat messages. However, with Datahose, there is no need for the service user to be part of a chat conversation to receive its messages: the service user will automatically receive **all events from all conversations** of the pod in real time.

Get more information on how to use Datahose with the [Datahose - Read Events](datahose-read-events.md) endpoint.
