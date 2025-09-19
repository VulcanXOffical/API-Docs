## AddEditOMS

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Adds a new logical Order Management System or allows an existing one to be edited.

### Request

```json
{
    "id": 0,
    "ownerId": 0,
    "omsName": "",
    "instanceGUID": "",
    "assetManagerCoreId": "",
    "assetManagerCoreUser": "",
    "assetManagerCorePassword": "",
    "assetManagerId": 0,
    "omsRiskMode": 0,
    "marginEnabled": true,
    "marginMarketType": 0,
    "permissionedMarketData": true,
    "permissionedInstrument": true,
    "permissionedProduct": true,
    "normalizedProductId": 0,
    "feeAccountId": 0,
    "depositContraAccountId": 0,
    "lendingAccountId": 0
}
```

| Key                      | Value                                                        |
| ------------------------ | ------------------------------------------------------------ |
| id                       | **integer.** The ID of the Order Management System. When creating an OMS, you can assign this number directly (it must be unique among OMSs) or you can leave this value set to 0 and allow the system to assign the ID. |
| ownerId                  | **integer.** The ID of the owner of the trading venue.       |
| instanceGUID             | **string.** A globally unique ID (GUID) that identifies this specific Order Management System. When creating an OMS, you can assign this GUID directly (it must be unique) or you can leave this value set to an empty string and allow the system to assign the GUID. |
| assetManagerCoreId       | **string.** This is a name that is set during configuration of the venue. |
| assetManagerCoreUser     | **string.** The named user who has access to the asset manager *core* for the Order Management System. This name is set during configuration of the venue. |
| assetManagerCorePassword | **string.** The password that allows the *assetManagerCoreUser* access to the asset manager *core* for this Order Management System. This password is set during configuration of the venue. |
| assetManagerId           | **integer.** The ID for the asset manager for this Order Management System (different from the asset manager *core.*) |
| omsRiskMode              | **integer.** An integer that describes the risk mode for the Order Management System. One of:<br />**0** Unknown<br />**1** NoRiskChecks<br />**2** Standard<br />**3** Mode1<br /><br />Currently *Mode1* is not used.  |
| marginEnabled            | **Boolean.** If this value is *true,* then margin trading is enabled on this Order Management System. **Note:** Margin trading calls are a future feature of the AlphaPoint Exchange. Setting this value to *true* signifies that margin trading is enabled for when it becomes available, not that margin trading can take place now. |
| marginMarketType         | **integer.** An integer that describes the margin market type available on this Order Management System. One of:<br />**0** None<br />**1** Provider &mdash; The venue extends credit to the investor for trading.<br />**2** SwapMarket &mdash; A *swap* is a derivative contract. Two parties exchange cash flows or liabilities from two different instruments.<br /><br />Margin functionality is a future expansion for the AlphaPoint Exchange. You should set this value to 0 until that function is available.  |
| permissionedMarketData   | **Boolean.** If *true,* the Order Management System requires a user to have permission to receive market data. This value is set during configuration. See the call **AddUserMarketDataPermissions.** |
| permissionedInstrument   | **Boolean.** If *true,* the Order Management System requires a user to have permission to trade in a given instrument. This value is set during configuration. See the call **AddUserInstrumentPermissions.** |
| permissionedProduct      | **Boolean.** If *true,* the Order Management System requires a user to have permission to trade in a given product. This value is set during configuration. See the call **AddUserProductPermissions.** |
| normalizedProductId      | **integer.** In order to facilitate calculating the values for margin-related key-value pairs, the Order Management System rolls an account's complete holdings together into a "normalized product" &mdash; a concept product the incorporates the value of all products held by an account. The Exchange assigns an ID to the "normalized product." The value of *normalizedProductId* is this ID. |
| feeAccountId             | **integer.** The ID of the account into which all fees collected by the Order Management System and Exchange are deposited. Usually, this is Account ID 1. |
| depositContraAccountId   | **integer.** The OMS Deposit Account (described in the Admin Guide). This account holds deposits made through the exchange. Usually, this is Account ID 2. |
| lendingAccountId         | **integer.** The ID of the account in the Order Management System that lends to users so that they can trade on margin. |

### Response

```json
{
    "Id": 1
}
```

| Key  | Value                                                        |
| ---- | ------------------------------------------------------------ |
| Id   | **integer.** The system responds by returning the value for the ID of the Order Management System. |
