---
description: >-
  This endpoint returns the possible distinct values for each of the filter
  names provided in the "filters" parameter.
---

# Get distinct values of a list of filters

The scope of the filter values is restricted with the same type of filters we use to restrict the list of Audit Trail Events we retrieve in the /audits endpoint. Beware that a given filter may be included, rather in the list of filters, rather included in the filter restrictions.E.g: we can search the distinct "action" values, or we can search for the values of other filters for a given "action=sentMessage"

{% swagger src="../../.gitbook/assets/audit-trail-api-public.yaml" path="/v1/filters/values" method="get" expanded="true" fullWidth="true" %}
[audit-trail-api-public.yaml](../../.gitbook/assets/audit-trail-api-public.yaml)
{% endswagger %}
