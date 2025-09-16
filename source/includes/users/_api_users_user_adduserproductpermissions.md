## AddUserProductPermissions

**Category:** User<br />**Permissions:** Operator, Company<br />**Call Type:** Synchronous

Adds a single product permission to a user.

### Request

```json
{
    "OMSId": 1,
    "ProductId": 1,
    "UserId": 1
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System where the user operates and the product trades. |
| ProductId    | **integer.** The ID of the product whose permission to trade is being added to the user. |
| UserId       | **integer.** The ID of the user who is gaining the permission to trade in the product. |

### Response

```json
{
  "result":true,
  "errormsg":null,
  "errorcode":0,
  "detail":null
}
```

A successful response means that the system has received **AddUserProductPermissions**, not that the product permission has been successfully added. To find out if the permission has been added, use **GetUserPermissions.**


| Key    | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean**. A successful receipt returns *true*; an unsuccessful receipt (an error condition) returns *false*. |
| errormsg  | **string**. A successful receipt returns null; the *errormsg* parameter for an unsuccessful receipt returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104) |
| errorcode | **integer**. A successful receipt returns *0*. An unsuccessful receipt returns one of the errorcodes shown in the *errormsg* list. |
| detail    | **string**. Message text that the system may send. Usually *null*. |




