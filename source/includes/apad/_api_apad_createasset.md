## CreateAsset

**Category:** APAD<br />**Permissions:** PlatformAdmin<br />**Call Type:** Asynchronous

Creates a new asset in the system and defines its attributes. An asset is the same as a product. The same call creates this product on the AlphaPoint exchange and associates that product with the company named in *CompanyName* so that CompanyName can supply the asset to the exchange &mdash; for example, they can offer shares in the &ldquo;Windmill Farms&rdquo; enterprise.

### Request

```json
{
    "sessionId":GUID,
    "assetName":"WMFS",
    "assetFullName":"Windmill Farm Shares",
    "decimals":2,
    "assetType":"Contract",
    "companyName":"Windmill Farm, Inc.",
    "boardApprovalDate":"2018-08-17T17:57:56Z",
    "comments":""
}
```

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| sessionId         | **string.** The globally unique identifier for the current user's logged-in session. |
| assetName         | **string.** The short name, or nickname, of the asset. For example, WMFS for Windmill Farm Shares. Must be a non-empty string, for example "&nbsp;". |
| assetFullName     | **string.** The full name of the asset (not the company creating the asset). For example, Windmill Farm Shares. Must be a non-empty string, for example "&nbsp;". |
| decimals          | **integer.** DEPRECATED. The number of decimal places to which the asset is traded. For example, the US Dollar is traded to two decimal places. The maximum number of decimal places is eight. |
| assetType         | **string.** DEPRECATED. The nature of the asset or product. One of:<br />0 Unknown (an error condition)<br />1 NationalCurrency<br />2 CryptoCurrency<br />3 Contract<br /><br />Must be a non-empty string, for example "&nbsp;". |
| companyName       | **string.** DEPRECATED. The name of the company supplying the asset. Must be a non-empty string, for example "&nbsp;". |
| boardApprovalDate | **string.** DEPRECATED. The time and date of board approval to add the asset to the exchange, in Microsoft Ticks format. The time and date are always given as UTC. |
| comment           | **string.** DEPRECATED. Any comment appended to the new asset. |

### Reply

```json
{
    "AssetName":"WMFS",
    "AssetFullName":"Windmill Farm Shares",
    "CompanyName":"Windmill Farm, Inc.",
    "AssetId":GUID,
    "Decimals":2,
    "TotalIssued":10000,
    "BoardApprovalDate":"2018-08-17T17:57:56Z",
    "Comments":""
}
```

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| AssetName         | **string.** The short name of the asset that is being created and associated with a company. For example, WMFS for Windmill Farm Shares. |
| AssetFullName     | **string.** A longer version of the name of the asset being created. For example, Windmill Farm Shares. |
| CompanyName       | **string.** The name of the company associated with the newly created product, for example, Windmill Farm, Inc. |
| AssetId           | **string.** A globally unique identifier for the asset assigned by the system. |
| Decimals          | **integer.** DEPRECATED. The number of decimals in which the asset may be traded. For example, the US Dollar is divided into two decimals. The maximum number of decimals is eight. |
| TotalIssued       | **real.** The total number of asset items added to the exchange for trading. (Not the monetary value.) |
| BoardApprovalDate | **string.** DEPRECATED. The time and date of board approval to add the asset to the exchange, in Microsoft Ticks format. The time and date are always given as UTC. |
| Comments          | **string.** DEPRECATED. Any comments appended to adding the new asset. |


