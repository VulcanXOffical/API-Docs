## GetAllBadges

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns an array of all account badges for an Order Management System, each element consisting of badge information.

Account badges cannot be deleted, but can be edited with **AddEditAccountBadge** and inactivated by setting the value of *Active* to *false.*

An account badge provides an alternate way to refer to an account so that both parties of a block trade (for example) can refer to the account by its badge rather than its account name.

### Request

```json
{
    "OMSId": 1
}
```

| Key   | Value                                                        |
| ----- | ------------------------------------------------------------ |
| OMSId | **integer.** The ID of the Order Management System on which the accounts have badges. |

### Response

```json
[
    {
        "OMSId": 1,
        "AccountId": 1,
        "BadgeId": 0,
	"Badge": "AP",
	"Active": false
    },
    {
        "OMSId": 1,
        "AccountId": 2,
        "BadgeId": 0,
	"Badge": "AP",
	"Active": false
    }
]
```
The Response returns an array of badges, each element consisting of badge information. This example shows two badges being returned.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| OMSId     | **integer.** The Order Management System on which the account operates and on which the account badge is available. |
| AccountId | **integer.** The ID of the account associated with the badge. |
| BadgeId   | **integer.** The ID of the badge.                     |
| Badge     | **string.** The alphanumeric name of the badge.   |
| Active    | **Boolean.** The value is *true* if the badge is currently active; *false* if it is not.  |


