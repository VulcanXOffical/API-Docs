## AddEditAccountBadge

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Adds (creates) or edits (changes) an account badge for an account. An account badge provides an alternate way to refer to an account so that both parties of a block trade can refer to the account by its badge rather than the account name.

<aside class="notice"><strong>Note: </strong>There is no corresponsing call to remove an existing account badge, although a badge can be set to null.</aside>

### Request

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
| OMSId     | **integer.** The ID of the Order Management System on which the account operates. |
| AccountId | **integer.** The ID of the account receiving the badge.      |
| BadgeId   | **string.** A short designation for the account &mdash; usually two or three letters and numbers. |
| Badge     | **string.** The alphanumeric badge name.                     |
| Active    | **Boolean.** The value is *true* if the badge is currently active; *false* if it is not.  |


### Response

```json
{
    "Success": "true"
}
```

| Key     | Value                                                        |
| ------- | ------------------------------------------------------------ |
| Success | **Boolean.** A value of *true* means that the account badge has been added or changed; a value of *false* means that the account badge has not bee successfully added or changed. |


