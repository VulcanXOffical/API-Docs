## EditInstrumentVerificationLevelConfig

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Edits the Verification Level configuration for a single instrument at a single Level.

### Request

```json
{
    "verificationLevel": 0,
    "omsId": 0,
    "instrumentId": 0,
    "instrumentName": null,
    "dailyBuyLimit": 0.0,
    "dailySellLimit": 0.0,
    "monthlyBuyLimit": 0.0,
    "monthlySellLimit": 0.0
}
```

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| verificationLevel | **integer.** The Verification Level you are editing.         |
| omsId             | **integer.** The ID of the Order Management System where the Verification Level is operational. |
| instrumentId      | **integer.** The ID of the instrument whose Verification Level configuration you're editing. |
| instrumentName    | **string.** The trading name of the instrument, for example, BTCUSD. |
| dailyBuyLimit     | **real.** The daily limit in units of the instrument that any account assigned this Verification Level can buy. |
| dailySellLimit    | **real.** The daily limit in units of the instrument that any account assigned this Verification Level can sell. |
| monthlyBuyLimit   | **real.** The monthly limit in units of the instrument that any account assigned this Verification Level can buy. |
| monthlySellLimit  | **real.** The monthly limit in units of the instrument that any account assigned this Verification Level can sell. |

### Response

```json
{
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": ""
}
```
The Response is a standard response object.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** If the call has been successfully received by the Order Management System, *result* is *true;* otherwise it is *false.* |
| errormsg  | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send.           |
