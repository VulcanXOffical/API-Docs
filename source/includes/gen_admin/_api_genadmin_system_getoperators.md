## GetOperators

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns a list of operators for the Order Management System on which the call is issued. The call cannot be issued for an Order Management System other than the one where the issuing operator is logged in.

### Request

```json
{}
```

There is no Request payload for this call.

### Response

```json
[
    {
        "OperatorId": 2,
        "OperatorGuid": "e420b702-b7e9-43f6-82f1-8fc442c3329d",
        "OperatorName": "CME Operator",
        "DefaultOMSId": 1,
        "Website": "",
        "VerifyURL": "",
        "UseEmailVerify": true,
        "UseRecaptcha": true,
        "RecaptchaPrivateKey": null,
        "RecaptchaPublicKey": null
    },
]
```

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| OperatorId          | **integer.** The ID of the operator.                         |
| OperatorGuid        | **string.** The globally unique ID (GUID) for the operator.  |
| OperatorName        | **string.** The user name of the operator.                   |
| DefaultOMSId        | **integer.** The ID of the Order Management System that the operator primarily administers. |
| Website             | **string.** The URL of the venue operator's website. This website URL is used to populate email templates.  |                                                 |
| VerifyURL           | **string.**                                                  |
| UseEmailVerify      | **Boolean.** A *true* value tells the Exchange to verify withdrawals using an email and two-factor authentication. A *false* value requires neither email verification nor 2FA.      |
| UseRecaptcha        | **Boolean.** Turns on (*true*) or off (*false*) use of Recaptcha for this operator. Recaptcha is a commercial bot detector. |
| RecaptchaPrivateKey | **string.** An alphanumeric string that is is the operator's private key for the Recaptcha bot detector. |
| RecaptchaPublicKey  | **string.** An alphanumeric string that is the operator's public key for the Recaptcha bot detector. |




