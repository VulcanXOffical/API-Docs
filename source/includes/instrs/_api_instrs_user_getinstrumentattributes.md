## GetInstrumentAttributes

**Category:** User<br />**Permissions:** Operator, Company<br />**Call Type:** Synchronous

Retrieves an array of instrument attributes.

### Request

```json
{
    "OMSId": 1,
    "InstrumentId": 1
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System on which the instrument is traded. |
| InstrumentId | **integer.** The ID of the instrument whose attributes will be returned. |

### Response

```json
[
    {
        "omsId":0,
        "instrumentId":0,
        "keyName":"keyValue":""
    },
]
```

The response returns an array, each element of which identifies the OMS, the instrument, and a single attribute value by name.

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| omsId        | **integer.** The ID of the Order Management System on which the instrument is traded. |
| instrumentId | **integer.** The ID of the instrument whose attributes are being returned. |
| keyName      | **string.** The name of the attribute that is returned in *keyValue*. |


