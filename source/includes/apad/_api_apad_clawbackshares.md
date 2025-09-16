##ClawbackShares

**Category:** APAD<br />**Permissions:** CompanyAdmin<br />**Call Type:** Asynchronous

Reverses a transfer of shares. The caller must be the CompanyAdmin of the issuer (company) owning the shares.

### Request

```json
{
    "sessionId":GUID,
    "assetname":"WMFS",
    "user":"jsmith",
    "amount":200,
    "comments":""
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| sessionId | **string.** The globally unique identifier (GUID) for the current user's logged-in session. |
| assetName | **string.** The short name of the asset whose shares are being reversed, for example, "WMFS" for Windmill Farm Shares. |
| user      | **string.** The name of the user from whom the shares will be retrieved. |
| amount    | **real.** The number of shares being retrieved, not the monetary value. |
| comments  | **string.** Any comments about the reversal.        |

### Reply

```json
{
    "AssetName":"WMFS",
    "CompanyName":"Windmill Farms",
    "FromOwnerName":"jsmith",
    "ToOwnerName":"Windmill Farms",
    "Amount":200,
    "TransactionId":"",
    "CertificateName?":"John Smith",
    "GrantDate?":"2018-08-17T17:57:56Z",
    "Comments?":""
}
```

| Key              | Value                                                        |
| ---------------- | ------------------------------------------------------------ |
| AssetName        | **string.** The name of the asset that was transfered and is now being reversed. |
| CompanyName:     | **string.** The name of the company whose company admin is making the reversal request. |
| FromOwnerName    | **string.** The name of the company (or user) surrendering the shares. |
| ToOwnerName      | **string.** The name of the company (or user) receiving the shares. |
| Amount           | **real.** The amount of shares being reversed (not the monetary value). |
| TransactionId    | **string.** The ID of the transaction that reverses the share transfer. Assigned by the system. |
| CertificateName? | **string.** Name of the grantee on the grant certificate. Used for share grants only. |
| GrantDate?       | **string.** The date and time of the original grant, in Microsoft Ticks format. The date and time are always given as UTC. Used for share grants only. |
| Comments?        | **string.** Any comments appended to the transaction. Used for share grants only. |


