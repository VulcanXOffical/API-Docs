## TransferAsset

**Category:** APAD<br />**Permissions:** PlatformAdmin, CompanyAdmin<br />**Call Type:** Asynchronous

Transfers an asset from one account to another account on the AlphaPoint Exchange. Both accounts must already exist. On the exchange, an "account" is different from a "user," and both are different from a "company."

The **TransferAsset** call is used to grant assets from a company to a user. The "from" name must be an APAD company name.

A user with CompanyAdmin permission can transfer an asset only between accounts or users associated with the company of the CompanyAdmin; the CompanyAdmin cannot transfer an asset to an unassociated account, for example. A PlatformAdmin can transfer an asset between any two accounts and users.

```json
{
    "sessionId":GUID,
    "assetName":"WMFS",
    "fromAccountType":"Asset",
    "fromName":"Windmill Farm, Inc.",
    "toAccountType":"Asset",
    "toName":"jsmith",
    "amount":2000,
    "certificateName?":"John Smith",
    "grantDate?":"2018-08-17T17:57:56Z",
    "comments?":""
}
```
###Request

| Key              | Value                                                        |
| ---------------- | ------------------------------------------------------------ |
| sessionId        | **string.** The globally unique identifier (GUID) for the logged-in session by the calling user. |
| assetName        | **string.** The short name of the asset that is being granted. |
| fromAccountType  | **string.** The type of account from which the grant is being made. Generally, one of:<br />Asset<br />Liability<br />ProfitLoss. However, this field currently is not used except to verify that it is non-empty. It must contain at least "&nbsp;". |
| fromName         | **string.** The name of the company or user from whom the asset is being granted. |
| toAccountType    | **string.** The type of account to which the grant is being made. Generally, one of:<br />Asset<br />Liability<br />ProfitLoss.<br />&nbsp;<br />
This field currently is not used except to verify that it is non-empty. It must contain at least "&nbsp;". |
| toName           | **string.** The name of the company or user to whom the asset is being granted. |
| amount           | **real.** The unit amount of the grant (not the dollar value). |
| certificateName? | **string.** The name of the grantee on the grant certificate. Used for grants only. |
| grantDate?       | **string.** The time and date stamp of the grant, in Microsoft Ticks format. Time and date are always given as UTC. Used for grants only. |
| comments?        | **string.** Any comments appended to the grant transfer. Used for grants only. |

### Reply

```json
{
    "AssetName":"WMFS",
    "ComanyName":"Windmill Farm, Inc.",
    "FromOwnerName":"Windmill Farm, Inc.",
    "ToOwnerName":"jsmith",
    "Amount":2000,
    "TransactionId":"A47wqe09",
    "CertificateName?":"John Smith",
    "GrantDate?":"2018-08-17T17:57:56Z",
    "Comments?":""
}
```

| Key              | Value                                                        |
| ---------------- | ------------------------------------------------------------ |
| AssetName        | **string.** The short name of the asset being transferred. For example, Windmill Farm Shares might be WMFS. |
| CompanyName      | **string.** The name of the company associated with and granting the asset. |
| FromOwnerName    | **string.** The company name or user name of the previous owner of the assets. The *from* owner must be a Company. |
| ToOwnerName      | **string.** The company name or user name of the new owner of the assets. |
| Amount           | **real.** The unit amount of the grant (not the dollar value). |
| TransactionId    | **string.** An ID assigned by the system to identify the asset transfer. |
| CertificateName? | **string.** The name of the grantee on the grant certificate. Used for grants only. |
| GrantDate?       | **string.** The time and date stamp of the grant, in Microsoft Ticks format. Time and date are always given as UTC. Used for grants only. |
| Comments?        | **string.** Any comments appended to the grant transfer. Used for grants only. |


