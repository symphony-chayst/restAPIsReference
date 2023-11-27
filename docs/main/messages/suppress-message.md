# Suppress Message

Released prior to 1.43. Suppress a message, preventing its contents from being displayed to users.

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/messagesuppression/{id}/suppress" method="post" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

### Suppressed Message Example

The following image shows how the UI represents a suppressed message.\
The image on the left shows the original message before being suppressed. The image on the right shows how the message will be displayed after being suppressed.

![](https://files.readme.io/a92e02e-suppressed.png)

As of Release v1.45, if the user attempts to suppress a message that has already been suppressed at an earlier point in time, the returned `suppressionDate` will have a value of 0, as shown below:

```json
{
    "messageId":"_Gj13MiR-5IrVtrmPNl6fn___qvWCYI_dA"
    "suppressed":true
    "suppressionDate":0
}
```

In addition, be aware that although the message is suppressed, the data from the original message will be in the Content Export (CE). When the CE exports a suppressed message, the following information are returned:

• Suppressed Message Content -> the content of the suppressed message.\
• Suppressed Message Sent From -> user that sent the suppressed message.\
• Suppressed Message Timestamp -> date when the message was suppressed.

> #### 🚧 Restricted Endpoint
>
> * Users can suppress their own messages only.
> * Users with the Content Management role can suppress any messages.
> * OBO: Please note that the SUPPRESS\_MESSAGES permission is needed for Apps to call this endpoint via OBO.
> * Starting with SBE 20.16, Messages in External rooms can also be suppressed. Please note however that if the counterpart does not yet have SBE 20.16, the message will only be suppressed on your end.
>
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
