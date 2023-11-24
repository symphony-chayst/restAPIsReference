# Introduction

In this page you will find the reference of our REST APIs and how to handle them:

* What the endpoints are and for which reason you can call them
* Which parameters should be included in your call
* What response you can get from your call
* Some small examples on the side column

## General remark

Among other informations present in this page, you will find the URLs you will need to get to our public endpoints. As you may already know, there are several physical interfaces in Symphony which have distinct functions (you can find more information in our Developer Guide under [REST API Architecture](https://docs.developers.symphony.com/building-bots-on-symphony/overview-of-rest-api/rest-api-architecture)).\
Moreover, and depending on the chosen deployment (in-cloud vs. enterprise), the URLs through which these interfaces are called can differ.

### In-Cloud Deployments

In-cloud deployments of Symphony use the following formats as both the Agent URL and the Key Auth URL are the same as your pod subdomain:

* Session Auth URL: YOUR-POD-SUBDOMAIN-api.symphony.com
* Key Auth URL: YOUR-POD-SUBDOMAIN-api.symphony.com
* Pod Url: YOUR-POD-SUBDOMAIN.symphony.com
* Agent Url: YOUR-POD-SUBDOMAIN.symphony.com

### Enterprise Deployments

For enterprise deployments of Symphony, the Agent URL and the Key Auth URL may differ from your pod subdomain because the Symphony software is deployed on premise. Therefore, enterprise deployments use the following formats:

* Session Auth URL: YOUR-POD-SUBDOMAIN-api.symphony.com
* Key Auth URL: YOUR-KEYAUTH-URL-api.symphony.com
* Pod Url: YOUR-POD-SUBDOMAIN.symphony.com
* Agent Url: YOUR-AGENT-URL.symphony.com

Contact your Symphony administrator for details.
