## GetUserReportWriterResultRecords

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Queries the database for ReportWriterResultRecords that result from the execution of reports requested by the session User.

Users with Trading permission can request user report writer result records only for their own; users with Operator permission can request any user's report writer result records.

<aside class="notice"><strong>Note: </strong>"Depth" in this call is the count of records to be returned, not market depth.</aside>

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("GetUserReportWriterResultRecords", {
  UserId: 6,
});
```

```http
POST /AP/GetUserReportWriterResultRecords HTTP/1.1
Host: hostname goes here...
aptoken: d0260e4b-bf6e-4fcd-a8cd-ad1cb01f2235
Content-Type: application/json
Content-Length: 21

{
    "UserId": 6
}
```

| Key        | Value                                                                                                                                                                                          |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| UserId     | **integer.** The ID of the user whose report writer result records will be returned._required._                                                                                                |
| Depth      | **integer.** The count of records to be returned, beginning at _startIndex_ and working backwards into the past. If not defined, all report writer result records will be returned._optional._ |
| StartIndex | **integer.** The record number at which the call starts returning records; from there, record return moves into the past. The most recent record is record is at startindex 0._optional._      |

### Response

```json
[
  {
    "RequestingUser": 6,
    "urtTicketId": "c2186954-3549-4214-99de-17281b0b7b02",
    "descriptorId": "0d24a8bd-1017-4f5a-acbb-eb41316411ca",
    "resultStatus": "SuccessComplete",
    "reportExecutionStartTime": "2023-03-30T07:16:30.949Z",
    "reportExecutionCompleteTime": "2023-03-30T07:16:30.954Z",
    "reportOutputFilePathname": "",
    "reportDescriptiveHeader": "TradeActivity|onDemand|2023-03-03T16:00:00.000Z|2023-03-04T16:00:00.000Z|2023-03-30T06:16:26.381Z|2023-03-30T07:16:30.949Z|0.00535 seconds"
  }
]
```

| Key                         | Value                                                                                                                                                        |
| --------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| RequestingUser              | **Integer**. ID of the user requesting the report writer result records.                                                                                     |
| urtTicketId                 | **string**. An alphanumeric string containing the unique report ID of the report.                                                                            |
| descriptorId                | **string**. A GUID (globally-unique identifier) that describes the report separately from the report ticket.                                                 |
| resultStatus                | **string**. The status of each run of the reports. One of:<br />0 NotStarted<br />1 NotComplete<br />2 ErrorComplete<br />3 SuccessComplete<br />4 Cancelled |
| reportExecutionStartTime    | **string.** The time that the report writer began execution, in Microsoft Ticks format.                                                                      |
| reportExecutionCompleteTime | **string.** The time that the report writer completed the report, in Microsoft Ticks format.                                                                 |
| reportOutputFilePathname    | **string.** The pathname (location) of the report output file.                                                                                               |
| reportDescriptiveHeader     | **string**. A string describing the report.                                                                                                                  |
