## GetOMS

**Category:** Trading<br />
**Permissions:** Operator<br />
**Call Type:** Synchronous

Retrieves details for a logical OMS.

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetOMS", {
  OMSId: 1
});
```

```http
POST /AP/GetOMS HTTP/1.1
Host: hostname goes here...
aptoken: d0d93fa5-e899-45a4-b08e-b539ec597796
Content-Type: application/json
Content-Length: 14

{
    "OMSId": 1
}
```

| Key          | Value                                                                                            |
| ------------ | ------------------------------------------------------------------------------------------------ |
| OMSId        | **integer**. The ID of the Order Management System that you wish to retrieve details for._required._ |
_                                                |

### Response

```javascript
{
    "Id": 1,
    "OwnerId": 0,
    "OMSName": "AlphapointUniversity",
    "InstanceGUID": "",
    "AssetManagerCoreId": "",
    "AssetManagerCoreUser": "",
    "AssetManagerCorePassword": "",
    "AssetManagerId": 1,
    "OMSRiskMode": "Unknown",
    "SystemMarginEnabled": false,
    "PermissionedMarketData": false,
    "PermissionedInstrument": false,
    "PermissionedProduct": false,
    "FeeAccountId": 2,
    "DepositContraAccountId": 3,
    "LendingAccountId": 0,
    "VenueTimeZone": "Dateline Standard Time",
    "BaseNotionalProductSymbol": "USD",
    "OmsVersion": "4.3.65.1063",
    "StandardAccountId": 0,
    "TradeSettlementAccountId": 0,
    "LendingInterestAccountId": 0
}
```

```http
{
    "Id": 1,
    "OwnerId": 0,
    "OMSName": "AlphapointUniversity",
    "InstanceGUID": "",
    "AssetManagerCoreId": "",
    "AssetManagerCoreUser": "",
    "AssetManagerCorePassword": "",
    "AssetManagerId": 1,
    "OMSRiskMode": "Unknown",
    "SystemMarginEnabled": false,
    "PermissionedMarketData": false,
    "PermissionedInstrument": false,
    "PermissionedProduct": false,
    "FeeAccountId": 2,
    "DepositContraAccountId": 3,
    "LendingAccountId": 0,
    "VenueTimeZone": "Dateline Standard Time",
    "BaseNotionalProductSymbol": "USD",
    "OmsVersion": "4.3.65.1063",
    "StandardAccountId": 0,
    "TradeSettlementAccountId": 0,
    "LendingInterestAccountId": 0
}
```

| Key                                 | Value                                                                                                                                                                                                                                                                                                       |
| ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Id                               | **integer.** The numerical ID of the Order Management System.                                                                                                                                                                                                                       |
| OwnerId                        | **integer.** The identifier assigned to the creator of the OMS.                                                                                                                                                                                                                                                                      |
| OMSName                              | **string.** The name of the Order Management System.                                                                                                                                                                                                                                     |
| InstanceGUID                            | **integer.** A unique identifier for a particular instance of the Alphapoint trading system                                                                                                                                                                                                                                        |
| AssetManagerCoreId                      | **integer.** The identifier of the core asset management system used to manage the assets traded on the platform.                                                                                                                                                                                                                              |
| AssetManagerCoreUser                            | **integer.** The user of the core asset management system used to manage the assets traded on the platform.                                                                                                                                                                                                                                        |
| AssetManagerCorePassword                      | **string.** The password of the core asset management system user.                                                                                                                                                                                                                              |
| AssetManagerId                            | **integer.** The numerical id of the Asset Manager.                                                                                                                                                                                                                                      
| OMSRiskMode                             | **integer.** The risk mode of the OMS, which can be used to set different risk limits for different trading scenarios.                                                                                                                                                                                                                               |
| SystemMarginEnabled                           | **boolean.** A flag that indicates whether or not margin trading is enabled for the OMS.                                                                                                     |
| PermissionedMarketData                       | **boolean.**   This specifies the level of market data access that is allowed for the OMS.                                                                                                                 |
| PermissionedInstrument               | **boolean.** This specifies the level of access that is allowed for the OMS with respect to the instruments that it can trade.                                                                                                                                                   |
| PermissionedProduct               | **boolean.** This specifies the level of access that is allowed for the OMS with respect to the products that it can trade.                                                                                                                                                                                                         |
| FeeAccountId                | **integer.** The ID of the account that is used to collect fees associated with trading on the OMS.                                                                                            |
| DepositContraAccountId                   | **integer.** the id of the account used to receive deposits from clients who wish to trade on the platform.                                                                                                                        |
| LendingAccountId                      | **integer.** The ID of the account that is used for lending activities associated with the OMS.                                                                                        |                                                                          
| VenueTimeZone      | **string.** The time zone in which the trading venue is located.                                                                                                                                                                                                                                     |
| BaseNotionalProductSymbol | **string.**  The symbol of the base notional product that is set on the OMS. An example would be USD.                                                                                                                                                                            |
| OmsVersion    | **int.**  The current version of the Order Management System.                                                                                                                                         |
| StandardAccountId    | **integer.** The identifier of the specific trading account that is used for standard trading activities on the platform.                                                                                                                    |
| TradeSettlementAccountId               | **integer.**  the account that is used for settlement of trades executed on the platform.                                                                                                                                                                        |
| LendingInterestAccountId             | **integer.** The account that is used for managing the interest payments associated with lending activities.                                                                                                                                                                |

