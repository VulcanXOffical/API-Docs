## CancelUserReport

**Category:** Trading<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Sends a request to DataService to Remove a User Report. If successful, changes the state of a UserReportTicket to **UserCancelled**. To get list of user reports that can be possibly cancelled, you can use the API [**GetUserReportTickets**](https://23harolds.github.io/slatedoc/#getuserreporttickets).

### Request

```javascript
const { APEX } = require("alphapoint-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("CancelUserReport", {
  UserReportId: "389f244a-b958-4545-a4a7-61a73205b59e",
});
```

```http
POST /AP/CancelUserReport HTTP/1.1
Host: hostname goes here...
aptoken: 250c3ff1-cfb2-488f-be88-dfaf12e4f975 //valid sessiontoken
Content-Type: application/json
Content-Length: 63

{
    "UserReportId":"389f244a-b958-4545-a4a7-61a73205b59e"
}
```

| Key          | Value                                                                                                                                                                                 |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| UserReportId | **string**. The GUID is a globally unique ID string that identifies the user report to be canceled. The Order Management System provides this ID when you create a report._required._ |

### Response

```json
{
  "result": true,
  "errormsg": "",
  "errorcode": 0,
  "detail": ""
}
```

The response to **CancelUserReport** verifies that the call was received, not that the user report has been canceled successfully. Individual event updates sent to the user show cancellations. To verify that a report has been canceled, call **GetUserReportTickets** or **GetUserReportWriterResultRecords**.

| Key       | Value                                                                                                                                                                                                                                                                                                                            |
| --------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| result    | **Boolean**. A successful receipt of the cancellation returns true; and unsuccessful receipt of the cancellation (an error condition) returns false.                                                                                                                                                                             |
| errormsg  | **string**. A successful receipt of the cancellation returns null; the _errormsg_ parameter for an unsuccessful receipt returns one of the following messages: Not Authorized (errorcode 20, Invalid Request (errorcode 100), Operation Failed (errorcode 101), Server Error (errorcode 102), Resource Not Found (errorcode 104) |
| errorcode | **integer**. A successful receipt of the cancellation returns 0. An unsuccessful receipt returns one of the _errorcodes_ shown in the _errormsg_ list.                                                                                                                                                                           |
| detail    | **string**. Message text that the system may send. Usually _null_.                                                                                                                                                                                                                                                               |
