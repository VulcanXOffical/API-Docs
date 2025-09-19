## CancelAllOrders

**Category:** User<br />
**Permissions:** Operator, Trading<br />
**Call Type:** Synchronous

Cancels all open matching orders for the specified account on an Order Management System. 

A user with Trading permission can cancel orders for himself; a user with Operator permissions can cancel orders for any account, instrument, or user.

<aside class="warning"><strong>Warning:</strong> <strong>CancelAllOrders</strong> will cancel all existing orders on an OMS when sending AccountID = 0 or when AccountID is ommited.</aside>

<aside class="notice"><strong>Note:</strong> Multiple users may have access to the same account.</aside>


### Request

```json
{
  "AccountId": 0,
  "OMSId": 0
}
```

| Key       | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| AccountId    | **integer.** The account for which all orders are being canceled. *Conditionally optional.* |
| OMSId        | **integer.** The Order Management System under which the account operates. *Required*. |
| IntrumentId        | **integer.** The instrument for which all orders are being canceled. *Conditionally optional*. |

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




