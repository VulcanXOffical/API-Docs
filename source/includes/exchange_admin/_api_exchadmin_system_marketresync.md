## MarketResync

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Resyncs a paused or halted market for a specified Exchange and instrument by requiring the Matching Engine to re-send the book state. Issue the **MarketResync** call before issuing **MarketReopen** or **MarketResume.**

The identification of the instrument is based not on the *instrumentID* but on the definition of the *venue instrument,* a template that operates at the Exchange level.

A market is paused using the call **MarketPause** and halted using **MarketHalt.**

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
| action            | **integer.**  The value of *action* confirms the expected action of the call. One of:<br />**0** Pause<br />**1** Resume<br />**2** Halt<br />**3** ReOpen<br />**4** ReSync    |
| requestedAt       | **integer.** Date-and-timestamp of the request, in POSIX format and UTC time zone. |
| requestedBy       | **integer.** The ID of the operator requesting the market halt. |

### Response

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
| action            | **integer.**  The value of *action* confirms the expected action of the call. One of:<br />**0** Pause<br />**1** Resume<br />**2** Halt<br />**3** ReOpen<br />**4** ReSync     |
| requestedAt       | **integer.** Date-and-timestamp of the request, in POSIX format and UTC time zone. |
| requestedBy       | **integer.** The ID of the operator requesting the market halt. |

