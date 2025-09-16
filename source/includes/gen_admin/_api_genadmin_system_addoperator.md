## AddOperator

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Adds a new operator to a running Order Management System. Operators are the top-level logical entity under which one or more OMS logical instances exist.

### Request

```json
{
    "OperatorId": 0,
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
| OperatorId          | **integer.** The ID of the operator you are creating. You can assign an explicit value for *OperatorId,* which *must* be unique, or you can enter 0 and allow the system to assign one for you. |
| OperatorGuid        | **string.** The globally unique ID (GUID) for the operator. You can assign a GUID to *OperatorGuid,* which *must* be unique, or you can enter a null and allow the system to assign one for you. |
| OperatorName        | **string.** The user name of the operator.                   |
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
    "Id": 6
}
```

| Key  | Value                                                        |
| ---- | ------------------------------------------------------------ |
| Id   | **integer.** The value for *operatorId,* either as assigned by the system or echoing back your assignment. |


