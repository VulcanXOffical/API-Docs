## GetAllAccountPositions

**Category:** System<br />**Permissions:** Operator, AccountReadOnly, AccountOperator<br />**Call Type:** Synchronous

Returns an array of positions (balances) by account and product. All positions are *current positions,* that is, they are positions as of the time the **GetAllAccountPositions** Request is issued.

The value of *startIndex* points to account ID. For example, if you have 200 accounts on an Exchange numbered 1-200, and wished to begin with account ID 150 and move towards higher account numbers, the value of *startIndex* would be 150.

Users with AccountReadyOnly or AccountOperator permission will see positions only for accounts to which they're related; users with Operator permissions will see all positions for *all* accounts.

### Request

```json
{
    "omsId": 0,
    "startIndex": 0,
    "limit": 0
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| omsId      | **integer.** The ID of the Order Management System where the account(s) has its positions. |
| startIndex | **integer.** A pointer to the account ID in the records of all account positions to begin returning position information.  |
| limit      | **integer.** The number of positions to return, beginning at the position indicated by *startIndex* and moving towards higher account ID numbers. |

### Response

```json
[
    {
        "omsId": 0,
        "accountId": 0,
        "productSymbol": "",
        "productId": 0,
        "amount": 0.0,
        "hold": 0.0,
        "pendingDeposits": 0.0,
        "pendingWithdraws": 0.0,
        "totalDayDeposits": 0.0,
        "totalMonthDeposits": 0.0,
        "totalYearDeposits": 0.0,
        "totalYearDepositNotional": 0.0,
        "totalDayWithdraws": 0.0,
        "totalMonthWithdraws": 0.0,
        "totalYearWithdraws": 0.0,
        "totalYearWithdrawNotional": 0.0
    },
]
```

The Response is an array of positions for the account by product.

| Key                        | Value                                                        |
| -------------------------- | ------------------------------------------------------------ |
| omsId                      | **integer.** The ID of the Order Management System on which the account positions reside. |
| accountId                  | **integer.** The ID of the account that holds this position. |
| productSymbol              | **string.** The symbol of the position product, for example BTC for BitCoin. |
| productId                  | **integer.** The ID of the position product.                 |
| amount                     | **real.** The amount of the position product, in units and fractions (not dollar value). For example 2.5 BitCoin or 2018.12 dollars. |
| hold                       | **real.** Any amount of the position product currently being held against withdrawal by the Exchange. |
| pendingDeposits            | **real.** Any amount of the position product being deposited in which the deposit has not yet cleared. |
| pendingWithdraws           | **real.** Any amount of the position product where a withdrawal has been requested but where the withdrawal has not been completed. |
| totalDayDeposits           | **real** Total deposits of the position product on the current day. |
| totalMonthDeposits         | **real.** Total deposits of the position product in the current month |
| totalYearDeposits          | **real.** Total deposits of the position product during the current calendar year (not a running year). |
| totalYearDepositsNotional  | **real.** In some jurisdictions, deposits of cryptocurrency must be conducted in terms of the local fiat currency. The value for *totalYearDepositsNotional* is the value of *totalYearDeposits* expressed in the local fiat currency. |
| totalDayWithdraws          | **real.** Total withdrawals of the position product on the current day. |
| totalMonthWithdraws        | **real.** Total withdrawals of the position product during the current month. |
| totalYearWithdraws         | **real.** Total withdrawals of the position product during the current calendar year (not a running year). |
| totalYearWithdrawsNotional | **real.** In some jurisdictions, withdrawals of cryptocurrency must be conducted in terms of the local fiat currency. The value for *totalYearWithdrawsNotional* is the value of *totalYearWithdraws* expressed in the local fiat currency. |


