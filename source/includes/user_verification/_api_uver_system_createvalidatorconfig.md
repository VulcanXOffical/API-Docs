## CreateValidatorConfig (DEPRECATED)

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Creates a new validator configuration for an external validation service for user info. The call is part of AlphaPoint's KYC ("Know Your Customer") process.

<aside class="warning"><strong>Note: This call is DEPRECATED. Do not use.</strong></aside>

### Request

```json
{
    "omsId": 0,
    "requestIdentifier": "",
    "username": "",
    "password": "",
    "uri": "",
    "websiteUrl": "",
    "enabled": true,
    "lastSequenceProcessed": 0
}
```

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| omsId                 | **integer.** The ID of the Order Management System on which you are creating the validator configuration. |
| requestIdentifier     | **string.** A globally unique identifier (GUID) that identifies this request to configure a validator. Leave this as an empty string on validator creation. |
| userName              | **string.** The name of the operator creating the validator configuration. |
| password              | **string.** The password to the validator's processes.       |
| uri                   | **string.** Uniform Resource Identifier; identifies the entry point to the validator on the internet. |
| websiteUrl            | **string.** The URL of the validator's website.              |
| enabled               | **Boolean.** If *true,* this validator is able to process KYC information. If *false,* the validator is not sent KYC information. |
| lastSequenceProcessed | **integer.** The ID of the most recent batch of KYC information sent to this validator. Since this call creates a validator configuration, there is no previous sequence. Leave this value set to 0. |

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
