## UpdateAccount

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Updates and changes the values that define an account.

Users with Trading permission can update only the loyalty settings of their own accounts; a user with Operator permission can update any key-value pair value of any account.

### Request

```json
{
    "omsid": 0,
    "accountId": 0,
    "accountName": "",
    "accountHandle": "",
    "firmId": "",
    "firmName": "",
    "accountType": 0,
    "feeGroupID": 0,
    "parentID": 0,
    "riskType": 0,
    "verificationLevel": 0,
    "feeProductType": 0,
    "feeProduct": 0,
    "refererId": 0,
    "loyaltyProductId": 0,
    "loyaltyEnabled": false,
    "marginEnabled": false,
    "liabilityAccountId": 0,
    "lendingAccountId": 0,
    "profitLossAccountId": 0
}
```
In the Request, only the values for *omsId* and *accountId* are required to identify the account being changed. Include other key-value pairs only as they are necessary to change their values. Be aware that some key-value pairs work together, for example, *loyaltyProductId* and *loyaltyProductEnabled*; or *feeProductType* and *feeProduct.* Failure to change both can cause an error.

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| omsId               | **integer.** REQUIRED The ID of the Order Management System for the Exchange. |
| accountId           | **integer.** REQUIRED The ID of the  account being updated.  |
| accountName         | **string.** OPTIONAL A human-readable formal name for the account: Jones Trading, for example. |
| accountHandle       | **string.** OPTIONAL A unique, user-assigned name that is checked for uniqueness at create-time by the Order Management System. Occasionally used as an alternate to Account ID. |
| firmId              | **string.** OPTIONAL An arbitrary identifier assigned by a trading venue operator to a trading firm as part of the initial company, user, and account setup process. For example, Smith Financial Partners might have the *firmId* of SMFP. |
| firmName            | **string.** OPTIONAL A longer, non-unique version of the trading firm's name. For example, Smith Financial Partners, LLC. |
| accountType         | **integer.** OPTIONAL The type of account. One of:<br />**0** Asset<br />**1** Liability<br />**2** ProfitLoss |
| feeGroupId          | **integer.** OPTIONAL Defines account attributes relating to how fees are calculated and assessed for groups or categories of accounts. The exact values for *feeGroupId* are set by the operator of the trading venue. |
| parentId            | **integer.** OPTIONAL Reserved for future development.       |
| riskType            | **integer.** OPTIONAL Determines the Exchange's sense of risk for this account. One of: <br />**0** Unknown (an error condition)<br />**1** Normal<br />**2** NoRiskCheck (no checking is required)<br />**3** NoTrading (permits no trading)<br /><br />Virtually all market participants are set to Normal. Other types indicate account configurations assignable by the trading venue operator. In the Response for the call **GetUserAccountInfos**, the value of *riskType* is returned as a string. |
| verificationLevel   | **integer.** OPTIONAL Controls how much verification this account requires. Verification Levels start at 0. (Most new accounts are set to 0 until they have gone through the KYC &mdash; Know Your Customer &mdash; process). The number of and meaning of the values are set by the venue operator. |
| feeProductType      | **integer.** OPTIONAL One of:<br />**0** BaseProduct<br />**1** SingleProduct<br /><br />Transaction fees may be charged by a trading venue operator. This value shows whether fees for this account's trades are charged in the product being traded (*BaseProduct,* for example, BitCoin), or whether the account has a preferred fee-paying product (*SingleProduct,* for example USD) to use in all cases and regardless of product being traded. In the Response for the call **GetUserAccountInfos,** the value of *feeProductType* is returned as a string. |
| feeProduct          | **integer.** OPTIONAL The ID of the preferred fee product, if *SingleProduct* is the value of *feeProductType.* If the value of *feeProductType* is *0 BaseProduct,* this is set to 0 |
| refererId           | **integer.** OPTIONAL Captures the ID of the person who referred this account to the trading venue, usually for marketing purposes. |
| loyaltyProductId    | **integer.** OPTIONAL The Loyalty Token is a parallel fee structure that replaces the general set of transaction fees. An Exchange can promote activity on a specific cryptocurrency token by offering discounted transaction fees denominated in that token to customers who choose that fee structure. This key is the ID of the loyalty product chosen by the Exchange. There can be one Loyalty Token per OMS. |
| loyaltyEnabled      | **Boolean.** OPTIONAL If *true*, this account has accepted the Loyalty Token fee structure. If *false*, the account has not accepted it. The default setting is *false*. |
| marginEnabled       | **Boolean.** OPTIONAL If *true*, this account can trade on margin. If *false*, the account cannot trade on margin. The default is *false.* |
| liabilityAccountId  | **integer.** OPTIONAL The ID of the liability account associated with this account. A liability account is necessary for this account to trade on margin. Used internally. |
| lendingAccountId    | **integer.** OPTIONAL The ID of the lending account associated with the account named in the *accountId* key. A lending account is necessary for this account to trade on margin. Used internally. |
| profitLossAccountId | **integer.** OPTIONAL The ID of the profit-and-loss account associated with the account named in the *accountId* key. A profit-and-loss account is necessary for this account to trade on margin. Used internally. |

### Response

```
{
"Result": true
}
```

| Key    | Value                                                        |
| ------ | ------------------------------------------------------------ |
| Result | **Boolean.** If the value is *true,* then the account has been updated by the system. If *false,* the account has not been updated by the system. |




