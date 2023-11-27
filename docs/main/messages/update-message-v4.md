# Update Message

Available on Agent 20.13.1+ with SBE 20.13.2+ in Beta. Starting with SBE 20.16, the feature is now in Controlled Availability. Update an existing message. Starting with Agent 23.6, this endpoint is OBO-enabled.

{% swagger src="../../.gitbook/assets/agent-api-public.yaml" path="/v4/stream/{sid}/message/{mid}/update" method="post" expanded="true" fullWidth="true" %}
[agent-api-public.yaml](../../.gitbook/assets/agent-api-public.yaml)
{% endswagger %}

* For authentication, you must either use the `sessionToken` that was created for delegated application access, or both the `sessionToken` and `keyManagerToken` together.

> #### 📘 Controlled Availability
>
> Message Update is currently released with **Controlled Availability** because of the following limitations:
>
> * This feature is not yet supported on **Mobile**, where updates are displayed as new messages instead of replacing the existing one.
> * The flag `silent=false`, that can be used to make an update be displayed as an unread message, is not fully supported yet.
>
> Both limits will be lifted in a future release.

> #### 🚧 Permissions and guidelines
>
> * Entitlement `canUpdateMessage` is required.
> * Wall posts cannot be updated.
> * It is not possible to update messages sent by other users (except when using OBO with the proper permissions)
> * There is no time limit to update old messages, however we discourage updating very old messages as this won't provide a good user experience.
> * There is no limit of how many times a message can be updated, but we discourage updating it more than a 1000 times.
> * When used as a OBO endpoint, the end user must have the `canUpdateMessage` entitlement enabled, and the App must have the `SEND_MESSAGES` permission.
