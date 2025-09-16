## GetWithdrawTemplateTypes

**Category:** System<br />**Permissions:** Operator, Withdraw<br />**Call Type:** Synchronous

Returns a list of template names that are appropriate to the product (asset) named in the Request. To obtain the key-value pairs of the template itself, call **GetWithdrawTemplate** with the template name you obtain here.

Users with Withdraw permission can get a withdraw template type suitable only for their accounts and permitted products. Users with Operator permission can get template types suitable for any account and product.

### Request

```json
{
    "OMSId": 1,
    "ProductId": 1
}
```

The system "knows" what Account Provider templates are suitable to your account and product permissions.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| OMSId     | **integer.** The ID of the Order Management System from which you plan to make the withdrawal. |
| ProductId | **integer.** The ID of the product (asset) that you plan to withdraw. |

### Response

```json
{
    "TemplateTypes": [
        "Standard"
    ],
    "AccountProviderName": "",
    "result": false,
    "errormsg": "",
    "statuscode": 0 
}
```

| Key           | Value                                                        |
| ------------- | ------------------------------------------------------------ |
| TemplateTypes | **array of strings.** An array of the names of the templates that are appropriate to the withdrawal of your asset, account, and Order Management System. If the call was unsuccessful, *TemplateTypes* may return an empty array. |
| AccountProviderName | **string.** The name of the account provider for the template. |
| result        | **Boolean.** If the call has been successfully received by the Order Management System, returns *true;* otherwise returns *false.* |
| errormsg      | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call can return:<br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode     | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| statuscode    | **integer.** If *result* is *false,* *statuscode* can return:<br />**32** Not Authorized<br />**33** Asset_Manager_Not_Found<br /><br />If not account provider is located, *statuscode* returns *null.* |


