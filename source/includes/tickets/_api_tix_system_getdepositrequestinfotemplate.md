## GetDepositRequestInfoTemplate

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Returns a single object describing a single deposit form template that is available to the caller and the caller's account, and appropriate to the product being deposited.

### Request

```json
{
    "OMSId": 1,
    "ProductId": 1,
    "AccountId": 1,
    "TemplateType": "TrustPay"
}
```
| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| OMSId     | **integer.** The ID of the Order Management System on which the product is traded. |
| ProductId | **integer.** The ID of the product to be deposited.          |
| AccountId | **integer.** The ID of the account into which the deposit will be made. |
| TemplateType | **string.** The name of the deposit template you want to return.  |


### Response

```json
{
    "Template": {
        "ProviderType":"BitcoinRpc",
        "Template": "{}",
        "ProcessInfo": "",
        "UseGetDepositWorkflow": true,
        "DepositWorkflow": "CryptoWallet"
    },
    "result": true,
    "errormsg": null,
    "statuscode": 0
}
```

The Response is a single template appropriate to the product specified in the Request and available to the caller, along with fields that show whether the Response successfully returned the Template information. The key-value pairs of the inner Template object vary from Account Provider to Account Provider.

#### Template object

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| ProviderType          | **String.** The type of asset handled by the Account Provider. Possible values are:<br /><br />BitcoinRpc<br />BitGoRpc<br />Internal Accounting<br />WsAccountingProvider<br />EthereumERC20<br />EthereumRPC |
| Template              | **JSON object.** The key-value pairs of *Template* vary from Account Provider to Account Provider. |
| ProcessInfo           | **String.** The *ProcessInfo* string varies with the Account Provider and the asset being deposited. In a generic deposit template, the *ProcessingInfo* key-value pair is empty; in other cases it is an address for processing the deposit. |
| UseGetDepositWorkflow | **Boolean.** A *true* value causes the deposit to use the deposit workflow named in *DepositWorkflow.* A *false* value causes the deposit not to use that defined workflow. |
| DepositWorkflow       | **String.** A set of defined workflows for this template. The workflows are defined and named during the installation of the Exchange. Choices are:<br /><br />CryptoWallet<br />ManualDeposit<br />MerchantForm<br />MerchantRedirect<br />Custom |

#### Response fields

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| result     | **Boolean.** If the call has been successfully received by the Order Management System, returns *true,* otherwise returns *false.* |
| errormsg   | **String.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call can return:<br /><br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| statusCode | **integer.** If *result* is *false,* *statusCode* can return: <br /><br />**32** Not Authorized<br />**33** Asset_Manager_Not_Found<br /><br />If no Account Provider is located, *statusCode* returns *null.* |

