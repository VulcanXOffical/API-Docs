## GetBadgeAccount

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Returns the account ID associated with a specified account badge.

An account badge provides an alternate way to refer to an account so that both parties of a block trade (for example) can refer to the account by its badge rather than its account name.

Account badges cannot be deleted, but can be edited with **AddEditAccountBadge** and inactivated by setting the value of *Active* to *false.*

Users with Trading permission can return only account IDs with which they are associated; users with Operator permission can return any account ID.

### Request

```json
{
    "OMSId": 1,
    "Badge": "AP"
}
```

| Key   | Value                                                        |
| ----- | ------------------------------------------------------------ |
| OMSId | **integer.** The Order Management System where the account with the badge operates. |
| Badge | **string.** The badge name whose associated account ID you want to return. |

### Response

```json
{
    "OMSId": 1,
    "AccountId": 1,
    "BadgeId": 0,
    "Badge": "AP",
    "Active": false
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| OMSId     | **integer.** The ID of the Order Management System where the account with the badge operates. |
| AccountId | **integer.** The ID of the account with which the badge is associated. |
| BadgeId   | **integer.** The ID of the badge, as assigned by the system. |
| Badge     | **string.** The badge name associated with the account.      |
| Active    | **Boolean.** The value is *true* if the badge is currently active; *false* if it is not.  |




