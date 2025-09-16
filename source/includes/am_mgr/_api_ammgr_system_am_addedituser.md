## AM_AddEditUser

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Connects the Asset Manager to an external service.

### Request

```json
{
    "id": "00000000-0000-0000-0000-000000000000",
    "assetManagerId": 0,
    "userName": "",
    "password": "",
    "permissionList": [],
    "omsId": 0,
    "action": 0,
    "messageType": 6014,
    "messageSequenceNumber": 0
}
```

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| Id                    | **string.** Globally unique ID that identifies the outside user. |
| assetManagerId        | **integer.** The ID of the Asset Manager that you want an external service to be able to access. |
| userName              | **string.** The Exchange user name of the external service that can access the Asset Manager. |
| password              | **string.** The Exchange password of the external service that can access the Asset Manager. |
| permissionList        | **array of strings.** An array of permission values assigned to the external service. |
| omsId                 | **integer.** The ID of the Order Management System associated with the Asset Manager. |
| action                | **integer.** enum                                            |
| messageType           | **integer.** enum                                            |
| messageSequenceNumber | **integer.**                                                 |

### Response

```json
{
    "id": "00000000-0000-0000-0000-000000000000",
    "assetManagerId": 0,
    "userName": "",
    "result": true,
    "errormsg": "",
    "statuscode": 0
}
```

| Key            | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| Id             | **string.** The globally unique ID for the external service accessing the Asset Manager. |
| assetManagerId | **integer.** The ID of the Asset Manager that the external service can access. |
| userName       | **string.** The Exchange user name for the external service. |
| result     | **Boolean.** If the call has been successfully received by the Order Management System, returns *true;* otherwise returns *false.* |
| errormsg   | **string.** A successful receipt of the call returns *null.* For an unsuccessful call, the value of *errormsg* can return:<br /><br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| statusCode | **integer.** If the value of *result* is *false,* *statusCode* can return:<br />**32** Not Authorized<br />**33** Asset_Manager_Not_Found |


