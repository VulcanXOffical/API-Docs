## RegisterNewDevice

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

**RegisterNewDevice** is the device register confirmation call. It will take the hashcode and validation code sent in an email to verify a device as trusted**RegisterNewDevice.** 

### Request

```json
{
    "HashCode": "",
    "PendingEmailCode": ""
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| HashCode      	  | **string.** Hash code associated with the device. |
| PendingEmailCode    | **string.** Email code to register device |

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
| result    | **Boolean.** If the hash code and validation code have successfully verified a device, *result* is *true;* otherwise it is *false.* |
| errormsg  | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send.           |


