## AddWithdrawTicketAttachment

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Adds an attachment to a withdraw ticket.

Users with Trading permission can add an attachment only to their own withdraw tickets; users with Operator permission can add an attachment to any withdraw ticket.

### Request

```json
{
    "base64Attachment": "",
    "attachmentId": 0,
    "submittedByUserId": 0,
    "submittedByUserName": "",
    "uploadDate": "0001-01-01T00:00:00",
    "uploadIP": "",
    "ticketNumber": 0,
    "description": ""
}
```

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| base64Attachment    | **string.** Any attachment file; PDF, spreadsheet, blob, or other format. |
| attachmentId        | **long integer.** The ID of the attachment. Assign a 0 value to this key. The system will assign an ID to the attachment and return it in the response when it receives this call. |
| submittedByUserId   | **integer.** The user ID of the user submitting the attachment. |
| submittedByUserName | **string.** The user name of the user submitting the attachment; for example, Jsmith. |
| uploadDate          | **string.** The date and time stamp showing when the attachment was uploaded, in Microsoft Ticks format. All date and time stamps are in UTC. |
| uploadIp            | **string.** The IP address from which the attachment was uploaded. |
| ticketNumber        | **long integer.** The number of the withdraw ticket to which the attachment is being attached. |
| description         | **string.** A description of the attachment.                 |

### Response

```json
{
    "success": true,
    "attachmentid": 100000002
}
```

Unlike many responses, a *true* response in the *success* field indicates that the attachment was received and attached to the withdraw  ticket.

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| success      | **Boolean.** A *true* value means that the attachment was received and attached to the withdraw ticket specified in the Request. A *false* value indicates that it was not. |
| attachmentid | **long integer.** The ID for the attachment, supplied by the system. |

