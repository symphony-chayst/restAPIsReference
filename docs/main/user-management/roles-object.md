# Roles Object

The `roles` object consists of the following possibilities:

* For end-user accounts (`NORMAL`), roles are:
  * `INDIVIDUAL`
  * `ADMINISTRATOR`
  * `SUPER_ADMINISTRATOR`
  * `L1_SUPPORT`
  * `L2_SUPPORT`
  * `COMPLIANCE_OFFICER`
  * `SUPER_COMPLIANCE_OFFICER`
* For service accounts (`SYSTEM`), roles are:
  * `INDIVIDUAL`
  * `USER_PROVISIONING`
  * `SCOPE_MANAGEMENT`
  * `CONTENT_MANAGEMENT`
  * `MALWARE_SCAN_MANAGER`
  * `MALWARE_SCAN_STATE_USER`
  * `AUDIT_TRAIL_MANAGEMENT`

_Please note that, for end-user accounts, if no role is specified at creation, then the `INDIVIDUAL` value is assigned._

**Note**: Users with the `COMPLIANCE_OFFICER` role may also be entitled to perform other actions. These optional entitleable actions display in a response as:

* `COMPLIANCE_OFFICER.MONITOR_WALL_POSTS`
* `COMPLIANCE_OFFICER.MONITOR_ROOMS`
* `COMPLIANCE_OFFICER.LOCK_AND_UNLOCK_ROOM`
* `COMPLIANCE_OFFICER.BAN_AND_UNBAN_ROOM_MEMBER`.
