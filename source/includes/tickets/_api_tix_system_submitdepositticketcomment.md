## SubmitDepositTicketComment

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Creates a comment and attaches that comment to a specific deposit ticket.

### Request

```json
{
    "commentId": 0,
    "enteredBy": 0,
    "enteredDateTime": "0001-01-01T00:00:00",
    "comment": "",
    "operatorId": 0,
    "omsId": 0,
    "ticketCode": "43d1a9f0-8dc3-46f9-b457-297c800d8c9c",
    "ticketId": 0
}
```

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| commentId       | **integer.** The ID of this specific comment. In the Request, set this to 0. The Response supplies the system-assigned value for *commentId.* |
| enteredBy       | **integer.** The user ID of the user making the comment. If an operator (admin) is making the request, this should be the generic user ID of the admin (not the operator ID). |
| enteredDateTime | **string.** The date and time that the comment was created, in Microsoft Ticks format and UTC time. |
| comment         | **string.** The comment string itself.                       |
| operatorId      | **integer.** The ID of an operator (admin) making the comment. The value for *operatorId* should be available programmatically from the ticket being commented. |
| omsId           | **integer.** The ID of the Order Management System on which the deposit is being made. |
| ticketCode      | **string.** A GUID (globally unique identifier) that identifies the deposit ticket to which the comment is attached. The value for *ticketCode* should be available programmatically from the ticket being commented. |
| ticketId        | **integer.** An ID assigned by the system to the ticket. You can obtain this value from the calls **CreateDepositTicket,** **GetAllDepositTickets,** **GetDepositTicket,** and **GetDepositTickets.** In all these calls, the key is named *ticketNumber.* |

### Response

```json
{
    "success": true,
    "commentid": 10000002
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| success   | **Boolean.** A *true* value means that the comment has been successfully attached to the deposit ticket; *false* means that it has not been attached. |
| commentId | **integer.** The ID assigned by the system to this specific comment. |


