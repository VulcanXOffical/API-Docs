## AddUserProductPermissionsBulk

**Category:** User<br />**Permissions:** Operator, Company<br />**Call Type:** Synchronous

Adds multiple product permissions to multiple users. 

### Request

```json
{
    "omsid": 0,
    "productids": [1,2],
    "userids": [1,2]
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| omsId      | **integer.** The ID of the Order Management System where the users operate and the products trade. |
| productIds | **integer array.** A comma-separated list of the IDs of the products whose permission to trade is being added to the list of users. |
| userIds    | **integer array.** A comma-separated list of the IDs of the users who are gaining the permissions to trade in the list of products. |

### Response

```json
{
  "result": true,
  "errormsg": null,
  "errorcode": 0,
  "detail": null
}
```

A successful response means that the system has received **AddUserProductPermissionsBulk**, not that the product permissions have been successfully added. To find out if the permission has been added, use **GetUserPermissions.**


| Key    | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean**. A successful receipt returns *true*; an unsuccessful receipt (an error condition) returns *false*. |
| errormsg  | **string**. A successful receipt returns null; the *errormsg* parameter for an unsuccessful receipt returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer**. A successful receipt returns *0*. An unsuccessful receipt returns one of the errorcodes shown in the *errormsg* list. |
| detail    | **string**. Message text that the system may send. Usually *null*. |




