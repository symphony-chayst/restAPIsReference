---
description: Welcome, Symphony Developer!
---

# Symphony API Reference documentation

This is the API reference documentation page for the following Symphony APIs: Pod, Agent, Key Manager, DLP, Audit Trail, Malware Scanner and Groups.&#x20;

An overview of the API is available [here](https://docs.developers.symphony.com/bots/overview-of-rest-api) on our developer doc website.

{% hint style="info" %}
**New API portal.** Please note that we migrated our documentation to a different provider to improve the quality of the documentation. In this transition period you may notice missing information or an inconsistent look and feel. Please reach out to the Symphony support or your usual point of contact at Symphony if you encounter any issue.  \
Thank you for your understanding.
{% endhint %}

### URL paths

The URLs paths are specific to your company. They also depend on the type of deployment (in-cloud vs. on premise).

Please get in touch with your Symphony point of contact to know more.

#### In-Cloud deployments

In-cloud deployments of Symphony use the following formats as both the Agent URL and the Key Auth URL are the same as your pod subdomain:

* Session Auth URL: YOUR-POD-SUBDOMAIN-api.symphony.com
* Key Auth URL: YOUR-POD-SUBDOMAIN-api.symphony.com
* Pod Url: YOUR-POD-SUBDOMAIN.symphony.com
* Agent Url: YOUR-POD-SUBDOMAIN.symphony.com

#### On-premise deployments

For enterprise deployments of Symphony, the Agent URL and the Key Auth URL may differ from your pod subdomain because the Symphony software is deployed on premise. Therefore, enterprise deployments use the following formats:

* Session Auth URL: YOUR-POD-SUBDOMAIN-api.symphony.com
* Key Auth URL: YOUR-KEYAUTH-URL-api.symphony.com
* Pod Url: YOUR-POD-SUBDOMAIN.symphony.com
* Agent Url: YOUR-AGENT-URL.symphony.com

Contact your Symphony administrator for details.
