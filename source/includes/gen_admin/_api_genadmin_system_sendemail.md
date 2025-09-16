## SendEmail

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Allows the SUPERUSER (only) to send a broadcast message to the email addresses of one or more people on the Exchange. The **SendMail** call is used for testing.

Each email address on the Exchange must be unique.

### Request

```json
{
    "operatorId": 0,
    "operatorName": "",
    "templateName": "",
    "language": "",
    "fromAddress": "",
    "replyTo": "",
    "function": "",
    "dateTimeFormat": "",
    "defaultTimeZone": "",
    "isEnabled": true,
    "toAddresses": [],
    "bccAddresses": [],
    "templateTokens": {},
    "template": ""
}
```

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| operatorId      | **integer.** The ID of the SUPERUSER sending the email.      |
| operatorName    | **string.** The user name of the SUPERUSER sending the email. |
| termplateName   | **string.** The name of the email template.                  |
| language        | **string.** The language in which the email is written. This setting allows the SUPERUSER, for example, to compose and identify one email in English and the same email in Spanish, and to differentiate between the two. |
| fromAddress     | **string.** The email address from which the email will be sent. |
| replyTo         | **string.** The email address that any "Reply" or "Reply All" email will automatically be sent to. |
| function        | **string.** Another instance of the template name, present for backwards-compatibility. |
| dateTimeFormat  | **string.** The date&ndash; and time-format of the timestamp of the email. The AlphaPoint Exchange allows two such formats: *POSIX* and *Microsoft Ticks.* |
| defaultTimeZone | **string.** The default time zone in which the email is date-and-time-stamped, regardless of where the SUPERUSER is logged in. This can be any time zone. However, all date&ndash; and time-stamps in the AlphaPoint exchange are recorded as UTC. |
| isEnabled       | **Boolean.** If the template is enabled, this is *true.* If the template is not enabled, this is *false.* |
| toAddresses     | **array of strings.** This is an array of email addresses to which the email will be sent. |
| bccAddresses    | **array of strings.** This is an array of email addresses to which the email will be sent without a record in the message header. |
| templateTokens  | **json object.** A set of key-value pairs; tokens that tie the template to application data. For example, in a Deposit Request Template, the value for *DepositAmount* would be filled with the amount of a deposit. |
| template        | **string.**                                                  |

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


