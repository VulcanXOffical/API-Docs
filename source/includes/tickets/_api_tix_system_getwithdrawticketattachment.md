## GetWithdrawTicketAttachment

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Retrieves an attachment from a withdrawal ticket.

### Request

```json
{
    "attachmentId": 0
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| attachmentId | **integer.** The ID of the specific attachment you want to retrieve. You can use the call **GetWithdrawTicket** to return any attachments appended to a specific ticket and learn the *attachmentId* if you don't already have it. |

### Response

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
| base64Attachment    | **string.** The attachment file. May be PDF, spreadsheet, blob, or other. |
| attachmentId        | **integer.** The ID assigned to the attachment by the system. Echoes the ID in the Request. |
| submittedByUserId   | **integer.** The user ID of the person who added the attachment to the withdrawal ticket. |
| submittedByUserName | **string.** The user name of the person who submitted the attachment. |
| uploadDate          | **string.** The date and time that the attachment was uploaded, in Microsoft Ticks format. All dates and times are UTC. |
| uploadIP            | **string.** The IP address from which the attachment was uploaded. |
| ticketNumber        | **long integer.** The number of the withdrawal ticket, as assigned by the system. |


