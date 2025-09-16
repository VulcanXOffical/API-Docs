## GetVenueInstruments

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Retrieves an array of information about instruments that are defined for use on Exchanges to which the specified Order Management System is connected.

A venue instrument acts as a template for instruments available on an Exchange.

### Request

```json
{
    "OMSId": 1
}
```

| Key   | Value                                                        |
| ----- | ------------------------------------------------------------ |
| OMSId | **integer.** The Order Management System for which you want to return the set of available pre-defined instruments. |

### Response

```json
[
    {
        "VenueInstrumentId": 15,
        "InstrumentId": 15,
        "InstrumentName": "XRPBTC",
        "VenueAdapterId": 1
    },
]
```

The Response is an array of instrument information; each element of the array is a single instrument. The instruments are defined for use on any Exchange connected to the specified OMS.

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| VenueInstrumentId | **integer.** The ID of the venue instrument definition.      |
| InstrumentId      | **integer.** The ID of the instrument available for this Order Management System that corresponds to the venue instrument definition. If an instrument does not yet exist on the OMS (but is available as a defined venue instrument), this value is 0. |
| InstrumentName    | **string.** The trading name of the instrument available for this Order Management System that corresponds to the venue instrument definition. If an instrument does not yet exist on the OMS (but is available as a defined venue instrument), this value is null. |
| VenueAdapterId    | **integer.** INTERNAL USE. A construct that matches the OMS to the venue definitions. |


