## SetUserConfig

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Sets the key-value pair configuration for a user. You can set multiple key-value pairs with a single call.

Users with Trading permission can set user configuration only for a user associated with their default account; users with Operator permission can set user configuration for any user.

You can check what user configurations have already been set by using **GetUserConfig.** 

### Request

```json
{
    "userId": 0,
    "userName": "",
    "config": {
        [
        	{"Key”: “Config1”,
             “Value”: Config1Val”},
        	{“Key”: “Config2”,
             “Value”: Config2Val”}
        ]
    }
}
```

| Key      | Value                                                        |
| -------- | ------------------------------------------------------------ |
| userId   | **integer.** The ID of the user for whom you're making configuration settings. |
| userName | **string.** The name of the user for whom you're making configuration settings. |
| config   | **array of json objects.** Configurations are key-value pairs of strings, usually named *key* and *value,* The value of *config* is an array of a variable number of json objects, each element of the array a key and a value. |
| Key      | **string.** The value of *Key* is the name of the configuration item. |
| Value    | **string.** The value of *Value* is the content of the configuration item. *Value* is always a string, even when it contains numbers. |

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
