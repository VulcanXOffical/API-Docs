## GetDepositInfo

**Category:** System<br />**Permissions:** Operator, Deposit<br />**Call Type:** Synchronous

Retrieves deposit key information so that the user can send cryptocurrency funds, and optionally generates new keys. The **GetDepositInfo** call is only for depositing cryptocurrency into an account.

Users with Deposit permission can deposit only to their own accounts; users with Operator permission can deposit to any account.

### Request

```json
{
    "OMSId": 1,
    "AccountId": 1,
    "ProductId": 1,
    "GenerateNewKey": true
}
```

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| OMSId           | **integer.** The ID of the Order Management System on which the deposit ticket was created. |
| AccountId    	  | **integer.** The ID of the account into which the deposit was made. |
| ProductId       | **integer.** The ID of the product (asset) of the Exchange that caused the generation of a ticket. |
| GenerateNewKey  | **Boolean.** If GenerateNewKey has a *true* value, the two crypto deposit keys wil be new; if GenerateNewKey has a *false* value, these will be the last two keys that were generated.|

### Response

```json
{
	"AssetManagerId": 1,
	"ACcountId": 1,
	"AssetId": 1,
	"ProviderId": 1,
	"DepositInfo": [],
	"result": true,
	"errormsg": null,
	"statuscode": 0
}
```

| Key                 | Value                                                        |
| ------------------- | ------------------------------------------------------------ |
| assetManagerId      | **integer.** The ID of the Asset Manager on which the deposit was made. |
| accountId           | **integer.** The ID of the account into which the deposit was made. |
| assetId             | **integer.** The ID of the asset (product) that was deposited. |
| ProviderId          | **integer.**  The ID of the Account Provider that handles this specific product (asset) |
| DepositInfo         | **array.** Array of two crypto deposit keys, each a long integer. |
| result     		  | **Boolean.** If the call has been successfully received by the Order Management System, returns *true,* otherwise returns *false.* |
| errormsg  		  | **String.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call can return:<br /><br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| statusCode 		  | **integer.** If *result* is *false,* *statusCode* can return: <br /><br />**32** Not Authorized<br />**33** Asset_Manager_Not_Found<br /><br />If no Account Provider is located, *statusCode* returns *null.* |