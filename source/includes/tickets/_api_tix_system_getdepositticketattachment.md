## GetDepositTicketAttachment

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Returns a single specific deposit ticket attachment based solely on the attachment ID.

A user with Trading permission can return an attachment only from a deposit made to that user's associated account; a user with Operator permission can return any attachment.

### Request

```json
{
    "attachmentId": 0
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| attachmentId | **integer.** The ID of an attachment that is part of a deposit ticket associated with the account of the issuing user (if Trading permission) or any account or user (if Operator permission). |

### Response

```json
{
    "base64Attachment": null,
    "attachmentId": 0,
    "submittedByUserId": 0,
    "submittedByUserName": null,
    "uploadDate": "0001-01-01T00:00:00",
    "uploadIP": null,
    "ticketNumber": 0,
    "description": null
}
```

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| base64Attachment    | **string.** Any attachment file; PDF, spreadsheet, blob.     |
| attachmentId        | **integer.** The ID of the attachment. The system assigned the attachment ID when the attachment was uploaded. |
| submittedByUserId   | **integer.** The user ID of the submitting user.             |
| submittedByUserName | **string.** The user name of the submitting user, for example, Jsmith. |
| uploadDate          | **string.** The time and date that the attachment was uploaded, in Microsoft Ticks format. All times and dates are UTC. |
| uploadIP            | **string.** The IP address from which the attachment was uploaded. |
| ticketNumber        | **long integer.** The ID number of the deposit ticket to which the attachment was linked. |
| description         | **string.** A description of the attachment.                 |


