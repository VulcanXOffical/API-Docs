## MarketPause

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Pauses the market for a specified Exchange and instrument. The identification of the instrument is based not on the *instrumentID* but on the definition of the *venue instrument,* a template that operates at the Exchange level.

A market may be paused while adjustments are made to the instrument's fee structure, for example, thus assuring that orders placed *before* time X and orders placed *after* time X are handled appropriately. A paused market can be restarted using the call **MarketResume.** 

### Request

```json
{
    "omsId": 0,
    "venueAdapterId": 0,
    "venueInstrumentId": 0,
    "action": 0,
    "requestedAt": 0,
    "requestedBy": 0
}
```

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| omsId             | **integer.** The ID of the Order Management System that hosts the Exchange and market for the instrument whose market you're about to halt. |
| venueAdapterId    | **integer.** INTERNAL USE. A construct that matches the OMS to the venue definitions. |
| venueInstrumentId | **integer.** The ID of the venue instrument definition for the instrument whose market you want to halt. |
| action            | **integer.**   The value of *action* confirms the expected action of the call. One of:<br />**0** Pause<br />**1** Resume<br />**2** Halt<br />**3** ReOpen<br />**4** ReSync   |
| requestedAt       | **integer.** Date-and-timestamp of the request, in POSIX format and UTC time zone. |
| requestedBy       | **integer.** The ID of the operator requesting the market halt. |

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






