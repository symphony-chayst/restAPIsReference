---
description: Returns the full set of Symphony features available for this pod.
---

# List Features

{% swagger src="../../.gitbook/assets/pod-api-public.yaml" path="/v1/admin/system/features/list" method="get" expanded="true" fullWidth="true" %}
[pod-api-public.yaml](../../.gitbook/assets/pod-api-public.yaml)
{% endswagger %}

Features entitlements definition:

* `postReadEnabled`: Allows the user to read wall posts.
* `postWriteEnabled`: Allows the user to write wall posts.
* `delegatesEnabled`: Allows the user to have delegates.
* `isExternalIMEnabled`: Allows the user to chat in external IM/MIMs.
* `canShareFilesExternally`: Allows the user to share files externally.
* `canCreatePublicRoom`: Allows the user to create internal public rooms.
* `canUpdateAvatar`: Allows the user to edit profile picture.
* `isExternalRoomEnabled`: Allows the user to chat in private external rooms.
* `canCreatePushedSignals`: Allows the user to create push signals.
* `canUseCompactMode`: Enables Lite Mode.
* `mustBeRecorded`: Must be recorded in meetings.
* `sendFilesEnabled`: Allows the user to send files internally.
* `canUseInternalAudio`: Allows the user to use audio in internal Meetings.
* `canUseInternalVideo`: Allows the user to use video in internal Meetings.
* `canProjectInternalScreenShare`: Allows the user to share screens in internal Meetings.
* `canViewInternalScreenShare`: Allows the user to view shared screens in internal Meetings.
* `canCreateMultiLateralRoom`: Allows the user to create multi-lateral room.
* `canJoinMultiLateralRoom`: Allows the user to join multi-lateral room.
* `canUseFirehose`: Allows the user to use Firehose.
* `canUseInternalAudioMobile`: Allows the user to use audio in internal meetings on mobile.
* `canUseInternalVideoMobile`: Allows the user to use video in internal meetings on mobile.
* `canProjectInternalScreenShareMobile`: Allows the user to share screens in internal meetings on mobile.
* `canViewInternalScreenShareMobile`: Allows the user to view shared screens in internal meetings on mobile.
* `canManageSignalSubscription`: Allows the user to manage signal subscriptions.
* `canCreateDatahose`: Can create datahose feeds.
* `canIntegrateEmail`: Can integrate email service.
* `canReadDatahose`: Can read from datahose feeds.
* `canSuppressMessage`: Can suppress own messages.
* `canSwitchToClient20`: Can switch to Client 2.0 experience.
* `canUpdateRoomHistoryProperty`: Can Toggle Room's Share History Property.
* `canUseEncryptAPI`: Allow user to use Agent Encrypt endpoints.
* `enableSwiftSearch`: Can Use Swift Search.
* `sdaDevtoolsEnabled`: Enable Developer Tools for SDA.
* `sdaPermissionsFullScreen`: Enable Full screen access on SDA.
* `sdaPermissionsGeoLocation`: Enable location access on SDA.
* `sdaPermissionsMedia`: Enable Media access on SDA.
* `sdaPermissionsMidiSysex`: Enable access to MIDI Sysex on SDA.
* `sdaPermissionsNotifications`: Allow notifications on SDA.
* `sdaPermissionsOpenExternalApp`: Allow Opening External Apps from SDA.
* `sdaPermissionsPointerLock`: Enable Pointer Lock on SDA.

> #### 🚧 Required Permissions
>
> Calling this endpoint requires the User Provisioning role with `ACCESS_USER_PROVISIONING_API` privilege.\
> See [Bot Permissions](https://docs.developers.symphony.com/building-bots-on-symphony/configuration/bot-permissions) for a list of roles and associated privileges.
