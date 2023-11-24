# Datafeed v2

### Introduction to Datafeed

[Datafeed](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed) is a service that transmits encrypted messages that come from the end users to the bot (e.g. service account). The datafeed provides messages and events from all conversations that the user is in. The types of events surfaced in the datafeed can be found in the [Real Time Events](https://docs.developers.symphony.com/building-bots-on-symphony/datafeed/real-time-events) list.

#### Datafeed version 2

**Datafeed 2.0** infrastructure uses a _long polling protocol_ for users to retrieve events, unlike the previous **Datafeed 1.0** which used _SSE (Server Sent Event) protocol_. This change not only ensures that maintaining connectivity is easier from both a client and server perspective, but also that the service is more reliable and performant for users as well.

Datafeed 1.0 is deprecated. If you are still using it, please consider upgrading.

As a last resort, you can enable the datafeed bridge in the Agent config in order to automatically map the calls you make on the Datafeed 1.0 APIs towards the Datafeed 2.0 infrastructure. This however does not allow you to benefit from all the reliability improvements of the Datafeed 2.0 service.

#### Changes required to upgrade to Datafeed 2.0

Datafeed 2.0 endpoints are different from the Datafeed 1.0 ones, so migrating requires changes in your code.\
If you are using our BDKs in Java or Python, migrating to Datafeed 2.0 is a simple configuration change.

Otherwise, the mapping between the API endpoints is the following:

* Datafeed 1.0 is accessible via the path /agent/v4/datafeed
  * Via a POST on the endpoint /agent/v4/datafeed/create, the datafeed is created and then the ID is persisted in a file, which is by default datafeed.id on the bot side
  * The bot subscribes to this ID to retrieve datafeed events; if it cannot be retrieved by using this ID, a new datafeed is created
  * Via a GET on the endpoint /agent/v4/datafeed/{id}/read, the list of events within the specific datafeed identified with {id} is returned
  * Deleting a datafeed is not supported
* Datafeed 2.0 is accessible via the path /agent/v5/datafeeds
  * Via a GET on the endpoint /agent/v5/datafeeds, is returned the list of already created IDs for a service account
  * Via a POST on the endpoint /agent/v5/datafeeds, the datafeed is created and the ID is not persisted on the bot side _→ Even if the bot is stale, a GET on the same endpoint will retrieve the ID to which the service account is subscribed_
  * Via a POST on the endpoint /agent/v5/datafeeds/{id}/read with a parameter ackId (empty string at the first query), the endpoint returns: the list of events, a new ackId string _→ This ackId permits acknowledgement of the last query and retrieve all events since the last one. All events received between the last payload and the new request are queued and therefore retrieved._
  * Via a DELETE on /agent/v5/datafeeds/{id}, the datafeed specified with the {id} is deleted _→ Deletion is enabled via datafeed 2.0 and not via datafeed 1.0_

> 📘 See also
>
> More details on how to do the queries can be found on the description of these endpoints here after:\
> [Datafeed 1.0](../../../endpoints-reference/datafeed/datafeed-v1/)\
> [Datafeed 2.0](./)
