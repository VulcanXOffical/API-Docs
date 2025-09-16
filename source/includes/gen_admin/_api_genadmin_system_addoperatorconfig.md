## AddOperatorConfig

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Adds a key-value pair to the set of configuration values for an Operator. The example shows adding a two-factor authentication value for Google2FA. AlphaPoint urges all operators and administrators to use 2FA.

Other configuration key-value pairs can be used for Google Application ID, and XP Ocp-Apim-Subscription-Key values.

The values of both *ConfigId* and *Config* must be strings.

### Request

```json
{
    "OperatorId": 1,
    "ConfigId": "Google2FA",
    "Config": "1234"
}
```

| Key        | Value                                                       |
| ---------- | ----------------------------------------------------------- |
| OperatorId | **integer.** The ID of the venue operator being configured. |
| ConfigId   | **string.** The name of the configuration key.              |
| Config     | **string.** The value of the configuration key.             |

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
