## GetAccountMarginState

**Category:** User<br />**Permissions:** Operator, Trading, AccountReadOnly<br />**Call Type:** Synchronous

Retrieves the state of the margin for a specific account.

Users with Trading or AccountReadOnly permission can retrieve balances only for accounts with which they're associated; users with Operator permission can retrieve balances for any account.

### Request

```json
{
    "AccountId": 0,
    "OMSId": 0
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| AccountId | **integer.** The ID of the account for which margin state must be returned. |
| OMSId     | **integer.** The ID of the Order Management System where the account operates. |

### Response

```json
{
    "omsId": 0,
    "accountId": 0,
    "normalizedProductId": 0,
    "buyingPower": 0.0,
    "maintenanceRequirement": 0.0
}
```

| Key                    | Value                                                        |
| ---------------------- | ------------------------------------------------------------ |
| omsId                  | **integer.** The ID of the Order Management System where the account operates. |
| accountId              | **integer.** The ID of the account whose margin state is being returned. |
| normalizedProductId    | **integer.** In order to facilitate calculating the values for *buyingPower* and *maintenanceRequirement,* the AlphaPoint Exchange rolls an account's complete holdings together into a "normalized product" &mdash; a concept product incorporating the value of all products held by the account. The Exchange assigns an ID to the "normalized product." The value of *normalizedProductId* is this ID.  |
| buyingPower            | **real.** The value of *buyingPower* is the total value of product held by the account plus the value of all available margin across all products held by the account.                |
| maintenanceRequirement | **real.** An amount required to be held in the account to qualify for the account's current available margin. A low value for *maintenanceRequirement* will result in a margin call.  |


