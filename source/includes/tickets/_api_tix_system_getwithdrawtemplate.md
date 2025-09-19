## GetWithdrawTemplate

**Category:** System<br />**Permissions:** Operator, Withdraw<br />**Call Type:** Synchronous

Returns the text of the specific withdrawal template. To find out what templates are available to you, call **GetWithdrawTemplateTypes.**

### Request

```json
{
    "OMSId": 1,
    "ProductId": 1,
    "TemplateType": "Template Name",
    "AccountId": 1,
    "AccountProviderId": 1
}
```

The system "knows" which Account Provider's withdrawal template to return based on the product ID and the template name you provide. There is usually only one Account Provider per product on an Exchange. *AccountId* and *AccountProviderId* therefore are optional key-value pairs.

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| OMSId        | **integer.** REQUIRED The ID of the Order Management System on which the withdrawal will be made. |
| ProductId    | **integer.** REQUIRED The ID of the product (asset) about to be withdrawn. |
| TemplateType | **string.** REQUIRED The name of the withdrawal template you want to return. |
| AccountId    | **integer.** OPTIONAL The ID of the account from which you plan to make the withrawal. |
| AccountProviderId | **integer.** OPTIONAL The ID of the Account Provider you plan to use for the withdrawal. |

### Response

```json
{
    "Template": "",
    "result": true,
    "errormsg": "",
    "statuscode": 0
}
```

The Response returns the key-value pairs of the template, along with any error messages about the call. The text of the template will vary from Account Provider to Account Provider.

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| Template   | **string.** The key-value pairs of the template inside a JSON string. |
| result     | **Boolean.** Returns *true* if the call is successfully received; otherwise *false.* |
| errormsg   | **string.** A successful receipt of the call returns *null.* The *errormsg* for an unsuccessful call returns one of:<br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorvode 104)<br />Operation Not Supported (errorcode 106) |
| statuscode | **integer.** If *result* is *false*, *statuscode* can return:<br />**32** Not Authorized<br />**33** AssetManager_Not_Found<br /><br />If no Account Provider is located, *statuscode* returns *null.* |


