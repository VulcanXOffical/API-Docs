## GetWithdrawTickets

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Returns a limited array of withdrawal tickets from the specified Order Management System and account.

**GetWithdrawTickets** is usable with Operator and Trading permissions. It returns tickets from a single account. A similar call, **GetAllWithdrawTickets,** can be used only with Operator permission and returns tickets from all accounts.

### Request

```json
{
    "OMSId": 1,
    "AccountId": 1,
    "StartIndex": 0,
    "Limit": 200
}
```

The key-value pairs *StartIndex* and *Limit* are optional. The oldest ticket is ticket *0*. This differs from other calls where the newest ticket is ticket *0.* The value of *StartIndex* is a pointer into the stream of withdrawal tickets, and the value of *Limit* shows how far into the past (towards ticket *0*) to return tickets. For example, if there are 1500 current tickets (oldest ticket *0* through newest ticket *1499*), *StartIndex* = 100, and *Limit* = 100; then **GetWithdrawTickets** would return ticket numbers 1399 through 1300.

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| OMSId      | **integer.** The ID of the Order Management System where the withdrawal tickets reside. |
| AccountId  | **integer.** The ID of the account from which the withdrawals were made. A user with Operator permission can return withdrawal tickets for any account; a user with Trading permission can return withdrawal tickets only for an account with which that user is associated. |
| StartIndex | **integer.** OPTIONAL A pointer into the stream of withdrawal tickets. The oldest ticket is ticket *0.* The default value for *StartIndex* is *0.* |
| Limit      | **integer.** OPTIONAL The number of withdrawal tickets to return, beginning at the ticket marked by *StartIndex.* The default value for *Limit* is 200. |

### Response

```json
[
    {
        "assetManagerId": 0,
        "accountId": 0,
        "assetId": 0,
        "assetName": "",
        "amount": 0.0,
        "templateForm": "{
            “TemplateType”: “TetherRPCWithdraw”,
            “Comment”: “TestWithdraw”,
            “ExternalAddress”: “ms6C3pKAAr8gRCcnVebs8VRkVrjcvqNYv3”, 
            }",
        "templateFormType": "ThetherRPCWithdraw",
        "omsId": 0,
        "requestCode": "490b4fa3-53fc-44f4-bd29-7e16be86fba3",
        "requestIP": "",
        "requestUserId": 0,
        "requestUserName": "",
        "operatorId": 0,
        "Status": 0,
        "feeAmt": 0.0,
        "updatedByUser": 0,
        "updatedByUserName": "",
        "ticketNumber": 0,
        "createdTimestamp": "0001-01-01T00:00:00",
        "lastUpdateTimestamp": "0001-01-01T00:00:00",
        "Comments": "[
                {
                "commentId": 0,
                "enteredBy": 0,
                "enteredDateTime": "0001-01-01T00:00:00",
                "comment": "",
                "operatorId": 0,
                "omsId": 0,
                "ticketCode": "",
                "ticketId": 0
                }
            ]",
		"Attachments": "[
                {
                "attachmentId": 0,
                "submittedByUserId": 0,
                "submittedByUserName": "",
                "uploadDate": "0001-01-01T00:00:00",
                "uploadIP": "",
                "ticketNumber": 0
                }
			]",
		"AuditLog": "[]"
	}
]
```

The Response is an array of detail information about the withdrawal.

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| assetManagerId      | **integer.** The ID of the Asset Manager through which the withdrawal was made. |
| accountId           | **integer.** The ID of the account that made the withdrawal. |
| assetId             | **integer.** The ID of the asset (product) that was withdrawn. Withdrawal fees (if any) are usually assessed in the same asset that was withdrawn. |
| assetName           | **string.** The short name of the asset. For example, BTC for BitCoin or USD for US Dollars. |
| amount              | **real.** The number of units or fractions of units of the asset that were withdrawn (not the asset's monetary value). For example, 2.5 BitCoin or 2018.00 US Dollars. |
| templateForm        | **JSON string object.** The contents of the template form vary from Account Provider to Account Provider depending on the asset being withdrawn and the identity of the Account Provider. The Response returns this information as a string. |
| templateFormType    | **string.** The name of the template being used. Templates vary from Account Provider to Account Provider. |
| omsId               | **integer.** The ID of the Order Management System on which the withdrawal was made. |
| requestCode         | **string.** A globally unique identifier (GUID) that identifies this specific withdrawal. |
| requestIP           | **string.** The IP address from which the withdrawal was initiated. |
| requestUserId       | **integer.** The user ID of the user who submitted the withdrawal. |
| requestUserName     | **string.** The user name of the user who submitted the withdrawal. For example, jsmith. |
| operatorId          | **integer.** The ID of the administrator (operator) who processed the withdrawal. Withdrawals of cryptocurrency are handled automatically; withdrawals of fiat (national) currency are approved by a human operator. |
| Status              | **integer.** The current status of the withdrawal ticket. Some of these statuses are valid only for cryptocurrency withdrawals, which uses an automated withdrawal process, and some are valid for fiat currency withdrawals, which requires a human admin (operator).  Some of these statuses are used by AlphaPoint internally, yet they may appear on a returned Withdraw Ticket.<br /><br />**Withdraw ticket statuses:**<br />**0** New (awaiting operator review)<br />**1** AdminProcessing (An admin is looking at the ticket)<br />**2** Accepted (withdrawal will proceed)<br />**3** Rejected (admin or automatic rejection)<br />**4** SystemProcessing (automatic processing underway)<br />**5** FullyProcessed (the withdrawal has concluded)<br />**6** Failed (the withdrawal failed for some reason)<br />**7** Pending (the admin has placed the withdrawal in pending status)<br />**8** Pending2Fa (user must click 2-factor authentication confirmation link)<br />**9** AutoAccepted (withdrawal will be automatically processed)<br />**10** Delayed (waiting for funds to be allocated for the withdrawal)<br />**11** UserCanceled (withdraw canceled by user or Superuser)<br />**12** AdminCanceled (withdraw canceled by Superuser)<br />**13** AmlProcessing (anti-money-laundering process underway)<br />**14** AmlAccepted (anti-money-laundering process complete)<br />**15** AmlRejected (withdrawal did not stand up to anti-money-laundering process)<br />**16** AmlFailed (withdrawal did not complete anti-money-laundering process)<br />**17** LimitsAccepted (withdrawal meets limits for fiat or crypto asset)<br />**18** LimitsRejected (withdrawal does not meet limits for fiat or crypto asset)<br />**19** Submitted (withdrawal sent to Account Provider; awaiting blockchain confirmation)<br />**20** Confirmed (Account Provider confirms that withdrawal is on the blockchain)<br />**21** ManuallyConfirmed (admin has sent withdrawal via wallet or admin function directly; marks ticket as FullyProcessed; debits account)<br />**22** Confirmed2Fa (user has confirmed withdraw via 2-factor authentication.) |
| feeAmt              | **real.** The amount of any fee that was charged for the withdrawal. *feeAmt* is always denominated in the asset or product that was withdrawn. |
| updatedByUser       | **integer.** The user ID of the most recent user who may have updated the withdrawal ticket. This user is usually an admin (operator). |
| updatedByUserName   | **string.** The user name of the most recent user who may have updated the withdrawal ticket. This user is usually an admin (operator). |
| ticketNumber        | **integer.** The number of the ticket, as assigned by the system. |
| createdTimeStamp    | **string.** The time and date when the withdrawal ticket was created, in Microsoft Ticks format. All times and dates are UTC. |
| lastUpdateTimeStamp | **string.** The time and date when the withdrawal ticket was last updated, in Microsoft Ticks format. All times and dates are UTC. |
| Comments            | **array of JSON string objects.** An array of key-value pairs appended as comments to the withdrawal ticket. See *Comments* example. |
| Attachments         | **array of JSON string objects.** An array of any attachments appended to the withdrawal ticket. See *Attachments* example. |
| AuditLog            | **array of JSON string objects.** Reserved for future use.   |

#### Comments Example

> Comments Example

```json
"Comments":"[
  {
    "commentId": 0,
    "enteredBy": 0,
    "enteredDateTime": "0001-01-01T00:00:00",
    "comment": "",
    "operatorId": 0,
    "omsId": 0,
    "ticketCode": "",
    "ticketId": 0
  }
]",
```

Comments appear as an array.

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| commentId       | **integer.** The ID assigned to the comment by the system.   |
| enteredBy       | **integer.** The ID of the user who entered the comment.     |
| enteredDateTime | **string.** The time and date that the comment was entered, in Microsoft Ticks format. All times and dates are UTC. |
| comment         | **string.** The text of the comment.                         |
| operatorId      | **integer.** The ID of the admin (operator) making the comment. |
| omsId           | **integer.** The ID of the Order Management System where the withdrawal ticket and comment were created. (They are unlikely to be different). |
| ticketCode      | **string.** A globally unique ID (GUID) assigned by the system that identifies the ticket. |
| ticketId        | **integer.** The ID of the ticket as assigned by the system. |

#### Attachments Example

> Attachments Example

```json
"Attachments":"[
  {
    "attachmentId":0,
    "submittedByUserId":0,
    "submittedByUserName":"",
    "uploadDate":"0001-01-01T00:00:00",
    "uploadIP":"",
    "ticketNumber":0
  }
]",
```

Any attachments appear as an array.

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| attachmentId        | **integer.** The ID assigned to the attachment by the system. |
| submittedByUserId   | **integer.** The user ID of the person who added the attachment to the withdrawal ticket. |
| submittedByUserName | **integer.** The user name of the person who submitted the attachment. |
| uploadDate          | **string.** The date and time that the attachment was uploaded, in Microsoft Ticks format. All times and dates are UTC. |
| uploadIP            | **string.** The IP address from which the attachment was uploaded. |
| ticketNumber        | **long integer.** The number of the withdrawal ticket, as assigned by the system. |


