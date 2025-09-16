## RemoveUserProductPermissions

**Category:** User<br />
**Permissions:** Operator, Company<br />
**Call Type:** Synchronous

Removes a single product permission from a user. A product permission is a permission to trade in the product.

### Request

```json
{
    "OMSId": 1,
    "ProductId": 1,
    "UserId": 1
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| OMSId     | **integer.** The ID of the Order Management System on which the user operates. |
| ProductId | **integer.** The ID of the product whose permission you are removing from the user. |
| UserId    | **integer.** The ID of the user for whom you are removing the product permission. |

###Response

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
| result    | **Boolean.** *True* signifies that the server has received the request to associate the affiliate tag with a specific user (not that it has done so); *false* signifies an error. |
| errormsg  | **string.** A successful response returns *null*; the *errormsg* parameter for a successful response returns on of the following messages:<br />Not Authorized (*errorcode* 20)<br />Invalid Request (*errorcode* 100)<br />Operation Failed (*errorcode* 102)<br />Resource Not Found (*errocode* 104) |
| errorcode | **integer.** A successful response returns *0*. An unsuccessful response returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send. Usually *null.* |


