## GenerateTreasuryActivityReport

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Initiates the generation of a Treasury Activity report for the specified accounts over a specified time interval.

A user with Trading permission can only generate treasury reports for accounts with which he/she is associated to; a user with Operator permission can generate treasury reports for any account.

The actual Treasury Activity Report will be generated as a comma-separated (CSV) file. It can be downloaded using the API call [**DownloadDocument**](https://23harolds.github.io/slatedoc/#downloaddocument)

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GenerateTreasuryActivityReport", {
  OMSId: 1,
  startTime: "2023-03-01T16:00:00.000Z",
  endTime: "2023-03-02T16:00:00.000Z",
  accountIdList: [185, 9], //1 or more accounts
});
```

```http
POST /AP/GenerateTreasuryActivityReport HTTP/1.1
Host: hostname goes here...
aptoken: 2bf2e45b-42aa-4448-9d6f-bb0a8fd020e4 //valid sessiontoken
Content-Type: application/json
Content-Length: 142

{
    "OMSId": 1,
    "startTime": "2023-03-01T16:00:00.000Z",
    "endTime": "2023-03-02T16:00:00.000Z",
    "accountIdList": [185, 9]
}
```

| Key           | Value                                                                                                                                                                                                                   |
| ------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| accountIdList | **integer array.** A comma-delimited array of one ore more account IDs, each valid on a single Order Management System for the authenticated user. The account user may not be the only user of the account._required._ |
| omsId         | **integer.** The ID of the Order Management System on which the array of account IDs exist._required._                                                                                                                  |
| startTime     | **string.** _startTime_ identifies the time and date for the historic beginning of the treasury activity report._required._                                                                                             |
| endTime       | **string.** _endTime_ identifies the time and date for the historic end of the treasury activity report._required._                                                                                                     |

### Response

```javascript
//Actual response
{
  "RequestingUser": 6,
  "OMSId": 1,
  "reportFlavor": "Treasury",
  "createTime": "2023-03-29T09:27:08.352Z",
  "initialRunTime": "2023-03-29T09:27:08.352Z",
  "intervalStartTime": "2023-03-01T16:00:00.000Z",
  "intervalEndTime": "2023-03-02T16:00:00.000Z",
  "RequestStatus": "Submitted",
  "ReportFrequency": "onDemand",
  "intervalDuration": 864000000000,
  "RequestId": "125e3f2e-0f19-47ba-9248-dfb8b98a1fac",
  "lastInstanceId": "00000000-0000-0000-0000-000000000000",
  "accountIds": [9]
}
```

Similar objects are returned for **Generate~Report** and **Schedule~Report** calls. As a result, for an on-demand **Generate~Report** call, some string-value pairs such as _initialRunTime_ may return the current time and _ReportFrequency_ will always return _OnDemand_ because the report is only generated once and on demand.

| Key               | Value                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| RequestingUser    | **integer.** The User ID of the person requesting the treasury activity report. This confirms the ID of the authenticated user who made the request by returning it as part of the response.                                                                                                                                                                                                                                                                                                                                          |
| OMSId             | **integer.** The ID of the Order Management System on which the treasury activity report will be run.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| reportFlavor      | **string.** The type of report to be generated. In the case of GenerateTreasuryActivityReport, report flavor will always be **Treasury**                                                                                                                                                                                                                                                                                                                                                                                              |
| createTime        | **string.** The time and date on which the request for the treasury activity report was made.                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| initialRunTime    | **string.** The time and date at which the treasury activity report was first run.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| intervalStartTime | **string.** The start of the period that the report will cover.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| intervalEndTime   | **string.** The end of the period that the report will cover.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| RequestStatus     | **string.** The status of the request for the treasury activity report. A Generate~Report request will always return _Submitted_. Each request returns one of:<br />Submitted<br />Validating<br />Scheduled<br />InProgress<br />Completed<br />Aborting<br />Aborted<br />UserCancelled<br />SysRetired<br />UserCancelled<br />Pending                                                                                                                                                                                             |
| ReportFrequency   | **string.** When the report runs. For a **Generate~Report** call, this is always OnDemand. One of:<br />OnDemand<br />Hourly<br />Daily<br />Weekly<br />Monthly<br />Annually                                                                                                                                                                                                                                                                                                                                                        |
| intervalDuration  | **long integer.** The period that the report covers relative to the run date. The **Generate~Report** call requires a start time and an end time. The AlphaPoint software calculates the difference between them as _intervalDuration_.<br /><br />For example, say that you specify a 90-day start-date-to-end-date window for a report. The _intervalDuration_ value returns a value equivalent to 90 days. If you have called **Generate~Report**, that value simply confirms the length of time that the on-demand report covers. |
| RequestId         | **string.** The ID of the original request. Request IDs are long strings unique within the Order Management System.                                                                                                                                                                                                                                                                                                                                                                                                                   |
| lastInstanceId    | **string.** For scheduled reports, the report ID of the most recent previously run report. Will be _null_ for a **Generate~Report** call, because generated reports are on-demand.                                                                                                                                                                                                                                                                                                                                                    |
| accountIds        | **integer array.** A comma-delimited array of account IDs whose treasury activities are reported in the treasury activity report.                                                                                                                                                                                                                                                                                                                                                                                                     |
