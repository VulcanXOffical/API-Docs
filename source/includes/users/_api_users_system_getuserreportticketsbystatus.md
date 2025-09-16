## GetUserReportTicketsByStatus

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Retrieves a list of *all* user report tickets according to the list of statuses submitted in the Request.

Users with Trading permission can return report tickets that meet status criteria only for their default accounts; users with Operator permission will return all report tickets that meet the status criteria.

### Request

```json
["Scheduled", "InProgress"]
```

The payload is not a KVP, but a comma-separated array of strings that describe one or more report statuses that will be reported.

Possible status values are:<br />Submitted<br />Validating<br />Scheduled<br />InProgress<br />Completed<br />Aborting<br />Aborted<br />UserCancelled<br />SysRetired<br />UserCancelPending

### Response

```json
[
    {
        "RequestingUser": 1,
        "OMSId": 1,
        "reportFlavor": "Transaction",
        "createTime": "2018-08-15T18:42:15Z",
        "initialRunTime": "2018-08-08T04:00:00Z",
        "intervalStartTime": "2018-08-08T16:00:00Z",
        "intervalEndTime": "2018-08-08T17:00:00Z",
        "RequestStatus": "Scheduled",
        "ReportFrequency": "Hourly",
        "intervalDuration": 36000000000,
        "RequestId": "9DJjUGNpj0CvOcIxRZuaUg==",
        "lastInstanceId": "AAAAAAAAAAAAAAAAAAAAAA==",
        "accountIds": [1]
    },
]
```

The Response is an array of users, their reports, and the status of each report.

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| RequestingUser    | **integer.** The ID of the user who requested the report.    |
| OMSId             | **integer.** The ID of the Order Management System on which the report runs. |
| reportFlavor      | **string.** The type of report. One of:<br />TradeActivity<br />Transaction<br />Treasury |
| createTime        | **string.** The time that the report request was created, in Microsoft Ticks format and UTC time zone. |
| initialRunTime    | **string.** The time that the report was first run, in Microsoft Ticks format and UTC time zone. |
| intervalStartTime | **string.** The start of the period that the report covers, in Microsoft Ticks format and UTC time zone. |
| intervalEndTime   | **string.** The end of the period that the report covers, in Microsoft Ticks format and UTC time zone. |
| RequestStatus     | **string.** The status of the request for the report. One of:<br />Submitted<br />Validating<br />Scheduled<br />InProgress<br />Competed<br />Aborting<br />Aborted<br />UserCancelled<br />SysRetired<br />UserCancelledPending |
| ReportFrequency   | **string.** How often the report runs. One of:<br />OnDemand<br />Hourly<br />Daily<br />Weekly<br />Monthly<br />Annually |
| intervalDuration  | **long integer.** The period that the report covers relative to the run date, in POSIX format and UTC time zone. For example, if you specify a 90 days in *intervalDuration,* whenever the report runs it "looks back" 90 days. |
| RequestId         | **string.** The ID of the original report request.           |
| lastInstance      | **string.** The ID of the most recent previously run report. |
| accountIds        | **array of integers.** A comma-delimited array of account IDs whose information is reported. |


