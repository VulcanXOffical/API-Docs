## UpdateOperator

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Updates an operator configuration.

### Request

```json
{
    "OperatorId": 5,
    "OperatorGuid": "",
    "OperatorName": "",
    "DefaultOMSId": 0,
    "Website": "",
    "VerifyURL": "",
    "UseEmailVerify": true,
    "UseRecaptcha": true,
    "RecaptchaPrivateKey": "",
    "RecaptchaPublicKey": ""
}
```

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| OperatorId          | **integer.** The ID of the operator whose configuration you are updating. |
| OperatorGuid        | **string.** The globally unique ID (GUID) of the operator whose configuration you are updating. |
| OperatorName        | **string.** The user name of the operator whose configuration you are updating. |
| DefaultOMSId        | **integer.** The ID of the Order Management System that the operator primarily administers. |
| website             | **string.** The URL of the venue operator's website. This website URL is used to populate email templates.   |
| verifyURL           | **string.**                                                  |
| UseEmailVerify      | **Boolean.** A *true* value tells the Exchange to verify withdrawals using an email and two-factor authentication. A *false* value requires neither email verification nor 2FA.  |
| UseRecaptcha        | **Boolean.** Turns on (*true*) or off (*false*) use of Recaptcha for this operator. Recaptcha is a commercial bot detector. |
| RecaptchaPrivateKey | **string.** An alphanumeric string that is is the operator's private key for the Recaptcha bot detector. |
| RecaptchaPublicKey  | **string.** An alphanumeric string that is the operator's public key for the Recaptcha bot detector. |

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






