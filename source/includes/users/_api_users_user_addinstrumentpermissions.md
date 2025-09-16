## AddUserInstrumentPermissions

**Category:** User<br />
**Permissions:** Operator, Company
**Call Type:** Synchronous

Adds permission to trade in a single instrument to a user, with the user and instrument specified by ID.

### Request

```json
{
  "OMSId": 1,
  "InstrumentId": 1,
  "UserId": 1
}
```

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** The ID of the Order Management System where the user operates and the instrument resides. |
| InstrumentId | **integer.** The ID of the instrument the user should have permission to trade. |
| UserId       | **integer.** The ID of the user being granted permission to trade in the instrument. |

### Response

```json
{
  "result":true,
  "errormsg":"",
  "errorcode":0,
  "detail":""
}
```
| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** *True* signifies that the server has received the request to add the instrument permission to a specific user (not that it has done so); *false* signifies an error. |
| errormsg  | **string.** A successful response returns *null*; the *errormsg* parameter for an unsuccessful response returns one of the following messages: Not Authorized (*errorcode* 20), Invalid Request (*errorcode* 100), Operation Failed (*errorcode* 101), Server Error (*errorcode* 102), Resource Not Found (*errorcode* 104) |
| errorcode | **integer.** A successful response returns 0. An unsuccessful response returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send. Usually *null*. |

