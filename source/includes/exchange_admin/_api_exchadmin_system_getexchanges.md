## GetExchanges

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** **Synchronous**

Retrieves an array with the matching engine

### Request

```json
{
}
```
No payload for GetExchanges

### Response

```json
[
    {
        "ExchangeServiceId": "V2ExchangeCore|1",
        "ExchangeId": "Matching Engine",
        "Instruments": [{
        	"ExchangeId": 1,
        	"InstrumentId": 1,
        	"ExchangeStatus": "Running",
        	"ProductPairType": "Standard",
        	"OrderBookType": "Standard",
        	"ProductPairId": 0,
        	"Product1Id": 2,
        	"Product2Id": 0,
        	"MinimumQuantity": 0,
        	"PriceIncrement": 0.00000001,
        	"Symbol": BTCUSD,
        	"PriceCollarThreshold": 10,
        	"PriceCollarPercent": 20,
        	"PriceCollarEnabled": false,
        	"PriceFloorLimit": 1,
        	"PriceFloorLimitEnabled": false,
        	"PriceCeilingLimit": 2,
        	"PriceCeilingLimitEnabled": false,
        	"SelfTradePrevention": true,
        	"MinimumPrice": 0,
        	"QuantityIncrement": 0.0000001,
        	"DisplaySymbol": "",
        	"IsDisable": false,
        	"MasterDataId": 0,
        	"CreateWithMarketRunning": true,
        }],
        "MarginProducts": [{
        	"ProductId": 1,
        	"MinimumQuantity": 0.01,
        	"Symbol": "" 
        }],
    }
]
```
Returns a list of Exchange Information, and the instruments and margin products.

| Key              |Value                                                        |
| ---------------- | ------------------------------------------------------------|
| ExchangeServiceId    | **string.** Name of exchange |
| ExchangeId		   | **string.** Always Matching Engine |
| Instruments          | **string.** List of instruments  |
| MarginProducts       | **string.** List of Margin Products  |
