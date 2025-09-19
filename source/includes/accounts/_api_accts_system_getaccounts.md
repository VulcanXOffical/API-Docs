## GetAccounts

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns an array of account information for the specified Order Management System, controlled by the values of *StartIndex* and *Limit.* 

You can optionally include the key-value pair *RequestedKeys*, which currently can return those accounts that include values for *firmId* and *firmName* (some accounts may not include values for these keys, and would not be returned). *StartIndex* and *Limit* still are used and apply when returning accounts based on *firmId* and *firmName.* 

### Request

```json
{
    "OMSId": 1,
    "StartIndex": 0,
    "Limit": 100,
    "RequestedKeys": [ "firmid", "FirmName", "fsRegId" ]
}
```

| Key           | Value                                                        |
| ------------- | ------------------------------------------------------------ |
| OMSId         | **Integer.** The ID of the Order Management System on which the accounts operate. |
| StartIndex    | **integer.** The account ID at which to begin returning account information. The returns from the call begin at the value of *StartIndex* and move toward higher numbers. For example, if you have 100 accounts on an Exchange numbered 1&ndash;100 and set the value of *StartIndex* to 50, the accounts returned will be numbered 50 and higher. |
| Limit         | **integer.** The number of accounts to return in the Response array. For example, if you set the value of *Limit* to 50, you will return up to 50 accounts (you may return fewer if there are fewer accounts to return). |
| RequestedKeys | **array of strings.** OPTIONAL Tells the system to return accounts that include values for the keys *firmId* and *firmName* (some accounts may not include values for these keys). In the current version of AlphaPoint Exchange, *firmId*, *firmName* and *fsRegId* are the only keys that can be used in this way. fsRegId key values will be in *firmId*. |

### Response

```json
[
    {
        "OMSID": 1,
        "AccountId": 22,
        "AccountName": "",
        "AccountHandle": "",
        "FirmId": "",
        "FirmName": "",
        "AccountType": 0,
        "FeeGroupID": 0,
        "ParentID": 0,
        "RiskType": 0,
        "VerificationLevel": 0,
        "FeeProductType": "BaseProduct",
        "FeeProduct": 0,
        "RefererId": 0,
        "LoyaltyProductId": 0,
        "LoyaltyEnabled": true,
        "MarginEnabled": true,
        "LiabilityAccountId": 0,
        "LendingAccountId": 0,
        "ProfitLossAccountId": 0
    },
]
```


| Key                 | alue                                                         |
| ------------------- | ------------------------------------------------------------ |
| OMSId               | **integer.** The ID of the Order Management System on which the account resides. |
| AccountId           | **integer.** The ID of the account for which information was requested. |
| AccountName         | **string.** A non-unique name for the account assigned by the user. |
| AccountHandle       | **string.** *accountHandle* is a unique user-assigned name that is checked at create time by the Order Management System to assure its uniqueness. |
| FirmId              | **string.** An arbitrary identifier assigned by a trading venue operator to a trading firm as part of the initial company, user, and account set up process. For example, Smith Financial Partners might have the ID SMFP. |
| FirmName            | **string.** A longer, non-unique version of the trading firm’s name; for example, Smith Financial Partners. |
| AccountType         | **integer.** The type of the account for which information is being returned. One of:<br />**0** Asset<br />**1** Liability<br />**2** ProfitLoss<br /><br />Responses for this string/value pair for Market Participants are almost exclusively Asset. |
| FeeGroupID          | **integer.** Defines account attributes relating to how fees are calculated and assessed for groups or categories of accounts. The exact values for *FeeGroupId* are set by the operator of the trading venue. |
| ParentID            | **integer.** Reserved for future development.                |
| RiskType            | **integer.** Determines the Exchange's sense of risk for this account. One of: <br />**0** Unknown (an error condition)<br />**1** Normal<br />**2** NoRiskCheck (no checking is required)<br />**3** NoTrading (permits no trading)<br /><br />Virtually all market participants are set to Normal. Other types indicate account configurations assignable by the trading venue operator. In the Response for the call **GetUserAccountInfos**, the value of *riskType* is returned as a string. |
| VerificationLevel   | **integer.** Verification level limits the amounts of deposits and withdrawals. It is defined by and set by the trading venue operator for each account and is part of the KYC ("Know Your Customer") process, which may be automated or manual. An account can earn a higher Verification Level over time. |
| FeeProductType      | **string.** One of:<br />**0** BaseProduct<br />**1** SingleProduct<br /><br />Transaction fees may be charged by a trading venue operator. This value shows whether fees for this account's trades are charged in the product being traded (*BaseProduct,* for example, BitCoin), or whether the account has a preferred fee-paying product (*SingleProduct,* for example USD) to use in all cases and regardless of product being traded. |
| FeeProduct          | **integer.** The ID of the preferred fee product, if any. Defaults to 0. |
| RefererId           | **integer.** Captures the ID of the entity who referred this account to the trading venue, usually captured for marketing purposes. |
| LoyaltyProductId    | **integer.** The Loyalty Token is a parallel fee structure that replaces the general set of transaction fees. An exchange can promote activity on a specific cryptocurrency token by offering discounted transaction fees denominated in that token to customers who choose that fee structure. This key is the ID of the loyalty product chosen by the Exchange. There can be one Loyalty Token per OMS. |
| LoyaltyEnabled      | **Boolean.** If *true*, this account has accepted the Loyalty Token fee structure. If *false*, the account has not accepted it. The default setting is *false*. |
| MarginEnabled       | **Boolean.** If *true*, this account can trade on margin. If *false*, the account cannot trade on margin. The default is *false.* |
| LiabilityAccountId  | **integer.** The ID of the liability account associated with the account named in the *accountId* key. A liability account is necessary for this account to trade on margin. Used internally. |
| LendingAccountId    | **integer.** The ID of the lending account associated with the account named in the *accountId* key. A lending account is necessary for this account to trade on margin. Used internally. |
| ProfitLossAccountId | **integer.** The ID of the profit-and-loss account associated with the account named in the *AccountId* key. A profit-and-loss account is necessary for this account to trade on margin. Used internally. |
