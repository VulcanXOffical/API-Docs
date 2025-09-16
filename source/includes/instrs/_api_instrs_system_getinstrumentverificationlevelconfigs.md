## GetInstrumentVerificationLevelConfigs

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns an array of all Verification Level configurations for all instruments on the Exchange, arranged by Verification Level.

### Request

```json
{
    "OMSId": 1
}
```

| Key   | Value                                                        |
| ----- | ------------------------------------------------------------ |
| OMSId | **integer.** The Order Management System whose instrument Verification Level configurations will be returned. |

### Response

```json
[
    {
        "Level": 1,
        "OMSId": 1,
        "Instruments": [
            {
                "verificationLevel": 1,
                "omsId":1,
                "instrumentId": 1,
                "instrumentName": "BTCUSD",
                "dailyBuyLimit": 0.0,
                "dailySellLimit": 0.0,
                "monthlyBuyLimit": 0.0,
                "monthlySellLimit": 0.0
            }
        ]
    }
]
```

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| Level             | **integer.** The Verification Level.                         |
| OMSId             | **integer.** The Order Management System where the Verification Level is operational. |
| Instruments       | **Array of JSON objects** Each object is the configuration for a single instrument at the given Verification Level. |
| verificationLevel | **integer.** The Verification Level for this instrument configuration. |
| omsId             | **integer.** The ID of the Order Management System where the Verification Level is operational. |
| instrumentId      | **integer.** The ID of the instrument whose Verification Level configuration is returned. |
| instrumentName    | **string.** The trading name of the instrument, for example, BTCUSD. |
| dailyBuyLimit     | **real.** The daily limit in units of the instrument that any account assigned this Verification Level can buy. |
| dailySellLimit    | **real.** The daily limit in units of the instrument that any account assigned this Verification Level can sell. |
| monthlyBuyLimit   | **real.** The monthly limit in units of the instrument that any account assigned this Verification Level can buy. |
| monthlySellLimit  | **real.** The monthly limit in units of the instrument that any account assigned this Verification Level can sell. |


