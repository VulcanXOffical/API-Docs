## GetAccountBadges

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Returns an array of account badges belonging to the specified account, each element consisting of badge information.

An account badge provides an alternate way to refer to an account so that both parties of a block trade (for example) can refer to the account by its badge rather than its account name.

Account badges cannot be deleted, but can be edited with **AddEditAccountBadge** and inactivated by setting the value of *Active* to *false.*

Users with Trading permission can return badges only for accounts with which they're associated; users with Operator permission can return badges for any account.

### Request

```json
{
    "OMSId": 1,
    "AccountId": 1
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| OMSId     | **integer.** The Order Management System on which the account operates whose badges you want to return. |
| AccountId | **integer.** The ID of the account whose badges you want to return. |

### Response

```json
[
    {
        "OMSId": 1,
        "AccountId": 1,
        "Badge": "AP",
        "BadgeId": 1,
	"Active": false
    },
]
```

The system returns an array of badge information for the account. An account can have more than one badge.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| OMSId     | **integer.** The Order Management System on which the account operates and on which the account badge is available. |
| AccountId | **integer.** The ID of the account associated with the badge. |
| Badge     | **string.** The alphanumeric badge name.                     |
| BadgeId   | **integer.** The ID of the badge, as assigned by the system. |
| Active    | **Boolean.** The value is *true* if the badge is currently active; *false* if it is not.  |


