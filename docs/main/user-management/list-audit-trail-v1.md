---
description: >-
  Returns a list of actions performed by a privileged account acting as
  privileged user, given a period of time.
---

# List Audit Trail

`Available on Agent 2.55.0 and above.`&#x20;

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v1/audittrail/privilegeduser" method="get" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

### Pagination

The `pagination` field will be returned (displayed) only if the response returns 50 or more items.

Pagination object definition:

• `before`: This is the opaque url-safe string that points to the start of the page of data that has been returned.\
• `after`: This is the opaque url-safe string that points to the end of the page of data that has been returned.

### Privileged Eligible Roles

Roles for which audit trail can be exported. It retrieves the audit trail of all writing actions performed by Admin and Compliance users acting as a privileged user, via privileged account audit trail APIs.

* User Provisioning (`USER_PROVISIONING`)
* Content Management (`CONTENT_MANAGEMENT`)
* Expression Filter Policy Management (`EF_POLICY_MANAGEMENT`)
* SCO (`SUPER_COMPLIANCE_OFFICER`)
* CO (`COMPLIANCE_OFFICER`)
* Super admin (`SUPER_ADMINISTRATOR`)
* Admin (`ADMINISTRATOR`)
* L1 (`L1_SUPPORT`)
* L2 (`L2_SUPPORT`)
* Scope Manager (`SCOPE_MANAGEMENT`).

> #### 🚧 Required Roles and Permissions
>
> Calling this endpoint requires a **Service Account** with the **Audit Trail Management** role.\
> See [Permissions](ref:permissions) for a list of roles and associated privileges.

### Examples of Usage

### before and after

Suppose we have an initial call. It will be returned only after the response because there is no before records.\
\`[https://acme.symphony.com/agent/v1/audittrail/privilegeduser?startTimestamp=1553264312000\&limit=1](https://acme.symphony.com/agent/v1/audittrail/privilegeduser?startTimestamp=1553264312000\&limit=1)

```json
{
    "items": [
        {
            "action": "RSA Key Added",
            "actionName": "rsaKeyAdded",
            "initiatorId": 7215545057307,
            "initiatorUsername": "bob.smith",
            "initiatorEmailAddress": "bob.smith@symphony.com",
            "affectedId": 7215545222851,
            "affectedUsername": "account.test",
            "affectedEmailAddress": "account.test@symphony.com",
            "authorizationRoles": [
                "SUPER_ADMINISTRATOR"
            ],
            "timestamp": 1555510357831
        }
    ],
    "pagination": {
        "cursors": {
            "after": "1"
        },
        "next": "/agent/v1/audittrail/privilegeduser?&startTimestamp=1553264312000&limit=1&after=1"
    }
n
```

`after` (next)\
`https://acme.symphony.com/agent/v1/audittrail/privilegeduser?startTimestamp=1553264312000&limit=1&after=1`

```json
{
    "items": [
        {
            "action": "Service Account Created",
            "actionName": "createServiceAccount",
            "initiatorId": 7215545057307,
            "initiatorUsername": "bob.smith",
            "initiatorEmailAddress": "bob.smith@symphony.com",
            "affectedId": 7215545222851,
            "affectedUsername": "account.test",
            "affectedEmailAddress": "account.test@symphony.com",
            "authorizationRoles": [
                "SUPER_ADMINISTRATOR"
            ],
            "timestamp": 1555510357104
        }
    ],
    "pagination": {
        "cursors": {
            "before": "2",
            "after": "2"
        },
        "previous": "/agent/v1/audittrail/privilegeduser?&startTimestamp=1553264312000&limit=1&before=2",
        "next": "/agent/v1/audittrail/privilegeduser?&startTimestamp=1553264312000&limit=1&after=2"
    }
}
```

`after` (next again)\
`https://acme.symphony.com/agent/v1/audittrail/privilegeduser?startTimestamp=1553264312000&limit=1&after=2`

```json
{
    "items": [
        {
            "action": "Enabled EF Enforcement",
            "actionName": "enabledEfEnforcement",
            "initiatorId": 7215545057307,
            "initiatorUsername": "bob.smith",
            "initiatorEmailAddress": "bob.smith@symphony.com",
            "authorizationRoles": [
                "EF_POLICY_MANAGEMENT"
            ],
            "timestamp": 1555505109178
        }
    ],
    "pagination": {
        "cursors": {
            "before": "3",
            "after": "3"
        },
        "previous": "/agent/v1/audittrail/privilegeduser?&startTimestamp=1553264312000&limit=1&before=3",
        "next": "/agent/v1/audittrail/privilegeduser?&startTimestamp=1553264312000&limit=1&after=3"
    }
}
```

`before` (previous)\
`https://acme.symphony.com/agent/v1/audittrail/privilegeduser?startTimestamp=1553264312000&limit=1&before=3`

```json
{
    "items": [
        {
            "action": "Service Account Created",
            "actionName": "createServiceAccount",
            "initiatorId": 7215545057307,
            "initiatorUsername": "bob.smith",
            "initiatorEmailAddress": "bob.smith@symphony.com",
            "affectedId": 7215545222851,
            "affectedUsername": "account.test",
            "affectedEmailAddress": "account.test@symphony.com",
            "authorizationRoles": [
                "SUPER_ADMINISTRATOR"
            ],
            "timestamp": 1555510357104
        }
    ],
    "pagination": {
        "cursors": {
            "before": "2",
            "after": "2"
        },
        "previous": "/agent/v1/audittrail/privilegeduser?&startTimestamp=1553264312000&limit=1&before=2",
        "next": "/agent/v1/audittrail/privilegeduser?&startTimestamp=1553264312000&limit=1&after=2"
    }
}
```

Last page (aka no more records to fetch), before the response. Note that we did not set the limit on this example, so it is using the default limit=50\
`https://acme.symphony.com/agent/v1/audittrail/privilegeduser?startTimestamp=1553264312000&after=127`

```json
{
    "items": [
        {
            "action": "End-user account created",
            "actionName": "createUser",
            "initiatorId": 7215545069230,
            "initiatorUsername": "bob.smith",
            "initiatorEmailAddress": "bob.smith@symphony.com",
            "affectedId": 7215545221479,
            "affectedUsername": "account.test",
            "affectedEmailAddress": "account.test@symphony.com",
            "authorizationRoles": [
                "SUPER_ADMINISTRATOR"
            ],
            "timestamp": 1553277265644
        },
        {
            "action": "Added Member",
            "actionName": "addedMember",
            "attribute": "admin@symphony.com",
            "initiatorId": 7215545069230,
            "initiatorUsername": "bob.smith",
            "initiatorEmailAddress": "bob.smith@qa5.com",
            "affectedId": 7215545057281,
            "affectedUsername": "test@symphony.com",
            "affectedEmailAddress": "test@symphony.com",
            "threadId": "UX2HkxQ2B4vs5qFkqs8jFX%2F%2F%2FpZryRyXdA%3D%3D",
            "scope": "Internal",
            "authorizationRoles": [
                "SUPER_COMPLIANCE_OFFICER"
            ],
            "conversationType": "Room",
            "timestamp": 1553273839863
        }
    ],
    "pagination": {
        "cursors": {
            "before": "128"
        },
        "previous": "/agent/v1/audittrail/privilegeduser?&startTimestamp=1553264312000&before=128"
    }
}
```

### initiatorId

`https://acme.symphony.com/agent/v1/audittrail/privilegeduser?startTimestamp=1553264312000&limit=5&initiatorId=7215545057307`

The response will return only events generated by this initiatorId

### role

Returns only events generated by a particular role.\
´[https://acme.symphony.com/agent/v1/audittrail/privilegeduser?startTimestamp=1553264312000\&limit=5\&role=ADMNISTRATOR](https://acme.symphony.com/agent/v1/audittrail/privilegeduser?startTimestamp=1553264312000\&limit=5\&role=ADMNISTRATOR)

```json
{
    "items": [
        {
            "action": "Profile info update",
            "actionName": "profileInfoUpdate",
            "attribute": "roles",
            "newValue": "[Individual,Administrator]",
            "oldValue": "[Individual]",
            "initiatorId": 7215545222842,
            "initiatorUsername": "bob.smith",
            "initiatorEmailAddress": "bob.smith@symphony.com",
            "affectedId": 7215545222843,
            "affectedUsername": "account.test",
            "affectedEmailAddress": "account.test@symphony.com",
            "authorizationRoles": [
                "ADMINISTRATOR"
            ],
            "timestamp": 1555437274937
        },
        {
            "action": "Profile info update",
            "actionName": "profileInfoUpdate",
            "attribute": "roles",
            "newValue": "[Individual,Administrator]",
            "oldValue": "[Individual]",
            "initiatorId": 7215545222800,
            "initiatorUsername": "bob.smith_3",
            "initiatorEmailAddress": "bob.smith_3@symphony.com",
            "affectedId": 7215545222801,
            "affectedUsername": "account.test_3",
            "affectedEmailAddress": "account.test_3@symphony.com",
            "authorizationRoles": [
                "ADMINISTRATOR"
            ],
            "timestamp": 1555264469483
        }
    ],
    "pagination": {
        "cursors": {
            "after": "1"
        },
        "next": "/agent/v1/audittrail/privilegeduser?&startTimestamp=1553264312000&limit=3&role=ADMINISTRATOR&after=1"
    }
}
```

### startTimestamp

The API returns an error when the period (startTimestamp - endTimstamp) is greater than 30 days.

```json
{
  "code": 400,
  "message": "\"Max of 30 days is allowed per request.\"",
  "details": "Max of 30 days is allowed per request."
}
```
