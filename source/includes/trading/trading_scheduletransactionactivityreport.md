## ScheduleTransactionActivityReport

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Initiates the generation of an series of Transaction Activity reports for the specified accounts over a regular periodic time interval.

A user with Trading permission can only schedule generation of transaction reports for accounts with which he/she is associated to; a user with Operator permission can schedule generation of transaction reports for any account.

The actual Transaction Activity Report will be generated as a comma-separated (CSV) file according to the interval, if interval set is daily, a transaction report will be generated daily unless cancelled using the API [**CancelReport**](https://23harolds.github.io/slatedoc/#cancelreport). It can be downloaded using the API call [**DownloadDocument**](https://23harolds.github.io/slatedoc/#downloaddocument)

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("ScheduleTransactionActivityReport", {
  OMSId: 1,
  beginTime: "2023-03-30T16:00:00.000Z",
  Frequency: "Weekly",
  accountIdList: [185, 9],
});
```

```http
POST /AP/ScheduleTransactionActivityReport HTTP/1.1
Host: hostname goes here...
aptoken: 2bf2e45b-42aa-4448-9d6f-bb0a8fd020e4 //valid sessiontoken
Content-Type: application/json
Content-Length: 142

{
    "OMSId": 1,
    "beginTime": "2023-03-30T16:00:00.000Z",
    "Frequency": "Weekly",
    "accountIdList": [185, 9]
}
```

| Key           | Value                                                                                                                                                                                                                                                   |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| frequency     | **integer.** How often the report will run and a transaction report get generated. One of the following:<br />0 OnDemand<br />1 Hourly<br />2 Daily<br />3 Weekly<br />4 Monthly<br />5 Annually. If not defined, the default is **Hourly**._optional._ |
| accountIdList | **integer array.** Comma-separated integers; each element an account ID on the Order Management System whose transaction activity will be reported on. All accounts must be from the same OMS._required._                                               |
| omsId         | **integer.** The ID of the Order Management System on which the accounts named in the list reside._required._                                                                                                                                           |
| beginTime     | **string.** The time at which the periodic reports begin; the day and time when you want reporting to start, in Microsoft Ticks format._required._                                                                                                      |

### Response

```javascript
//Actual response
{
    "RequestingUser": 6,
    "OMSId": 1,
    "reportFlavor": "Transaction",
    "createTime": "2023-03-29T16:24:35.923Z",
    "initialRunTime": "2023-03-30T16:00:00.000Z",
    "intervalStartTime": "2023-03-30T16:00:00.000Z",
    "intervalEndTime": "2023-04-06T16:00:00.000Z",
    "RequestStatus": "Submitted",
    "ReportFrequency": "Weekly",
    "intervalDuration": 6048000000000,
    "RequestId": "ba20a1d1-7acb-48b9-89eb-df2787e65934",
    "lastInstanceId": "00000000-0000-0000-0000-000000000000",
    "accountIds": [
        9,
        185
    ]
}
```

```http
{
    "RequestingUser": 6,
    "OMSId": 1,
    "reportFlavor": "Transaction",
    "createTime": "2023-03-29T16:24:35.923Z",
    "initialRunTime": "2023-03-30T16:00:00.000Z",
    "intervalStartTime": "2023-03-30T16:00:00.000Z",
    "intervalEndTime": "2023-04-06T16:00:00.000Z",
    "RequestStatus": "Submitted",
    "ReportFrequency": "Weekly",
    "intervalDuration": 6048000000000,
    "RequestId": "ba20a1d1-7acb-48b9-89eb-df2787e65934",
    "lastInstanceId": "00000000-0000-0000-0000-000000000000",
    "accountIds": [
        9,
        185
    ]
}
```

| Key               | Value                                                                                                                                                                                                                                                                                                                        |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RequestingUser    | **integer.** The User ID of the person requesting the transaction activity report. This confirms the ID of the authenticated user who made the request by returning it as part of the response.                                                                                                                              |
| OMSId             | **integer.** The ID of the Order Management System on which the transaction activity report will be run.                                                                                                                                                                                                                     |
| reportFlavor      | **string.** The type of report to be generated. In the case of ScheduleTransactionActivityReport, report flavor will always be **Transaction**                                                                                                                                                                               |
| createTime        | **string.** The time and date on which the request for the transaction activity report was made, in Microsoft Ticks format.                                                                                                                                                                                                  |
| initialRunTime    | **string.** The time and date at which the transaction activity report was first run, in Microsoft Ticks format.                                                                                                                                                                                                             |
| intervalStartTime | **string.** The start of the period that the report will cover, in Microsoft Ticks format.                                                                                                                                                                                                                                   |
| intervalEndTime   | **string.** The end of the period that the report will cover, in Microsoft Ticks format.                                                                                                                                                                                                                                     |
| RequestStatus     | **enumerated string.** The status of the request for the transaction activity report. Each request returns one of:<br />Submitted<br />Validating<br />Scheduled<br />InProgress<br />Completed<br />Aborting<br />Aborted<br />UserCancelled<br />SysRetired<br />UserCancelledPending                                      |
| ReportFrequency   | **enumerated string.** When the report runs:<br />OnDemand<br />Hourly<br />Daily<br />Weekly<br />Monthly<br />Annually                                                                                                                                                                                                     |
| intervalDuration  | **long integer.** The period that the report covers relative to the run date, in POSIX format. The call specifies a start time and an _intervalDuration_.<br /><br />In scheduled a scheduled report, the interval duration depends on the frequency, if the frequency is **Weekly**, the interval duration will be 1 weeek. |
| RequestId         | **string.** The ID of the original request. Request IDs are long strings unique within the Order Management System.                                                                                                                                                                                                          |
| lastInstanceId    | **string.** For scheduled reports, the report ID of the most recent previously run report.                                                                                                                                                                                                                                   |
| accountIds        | **integer array.** A comma-delimited array of account IDs whose transactions are reported in the transaction activity report.                                                                                                                                                                                                |
