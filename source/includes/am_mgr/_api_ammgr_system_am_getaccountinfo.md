## AM_GetAccountInfo

**Category:** System<br />**Permissions:** SUPERUSER<br />**Call Type:** Synchronous

Collects the account state for a single account based on account ID, Asset Manager ID, and Order Management System ID.

### Request

```json
{
    "assetManagerId": 0,
    "accountId": 0,
    "omsId": 0
}
```

| Key            | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| assetManagerId | **integer.** The ID of the Asset Manager used by the account. |
| accountId      | **integer.** The ID of the account for which you want to collect the account state information. |
| omsId          | **integer.** The ID of the Order Management System on which the account and the Asset Manager function. |

### Response

```json
{
    "AccountState": {
        {
            "assetManagerId":0,
            "accountId":0,
            "isFrozen":false,
            "assetStates":{
        		{
                    "messageVersion":0,
                    "isFrozen":true,
                    "accountId":0,
                    "assetId":0,
                    "totalBalance":0.0,
                    "totalHold":0.0,
                    "holds":{
        				{
                            "ownerId":"00000000-0000-0000-0000-000000000000",
                            "sequenceId":0,
                            "accountId":0,
                            "assetId":0,
                            "holdAmount":0.0,
                            "holdId":"00000000-0000-0000-0000-000000000000"
    					}
					},
				"balances":{
                	{
                        "accountId":0,
                        "assetId":0,
                        "providerId":0,
                        "sequenceId":0,
                        "balanceAmount":0.0,
                        "totalReceived":0.0,
                        "depositInfos":[],
                        "depositReceivedTxIds":[],
                        "withdrawSubmittedTxIds":[],
                        "withdrawConfirmedTxIds":[]
                	}
				},
            "messageType":6009,
            "messageSequenceNumber":0,
            "availableBalance":0.0
			}
		},
    "messageType":6008,
    "stateObjectId":"32fc0c75-7863-45b4-bade-6bf424b9db3b",
    "messageSequenceNumber":0
	}
	}
	},
    "result":false,
    "errormsg":"",
    "statuscode":0
}
```

The Response is a json object that contains several key-value pairs and arrays. The following tables build them up from their components.

### *holds* array

Each element of the *holds* array shows any asset hold for the account.

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| ownderId   | **string.** The globally unique ID (GUID) that identifies the owner of the trading venue. |
| sequenceId | **integer.** An integer that both identifies and shows the order in which any holds were placed. |
| accountId  | **integer.** The ID of the account whose asset is being held. |
| assetId    | **integer.** The ID of the asset (product) being held.       |
| holdAmount | **real.** The quantity of product being held (not the dollar-equivalence). For example 2.5 BitCoin or 1.005 Ethereum or 10.50 USD. |
| holdId     | **string.** The globally unique ID (GUID) that identifies the specific hold. |

### *balances* array

Each element of the *balances* array holds a balance for a specific asset held by the account.

| Key                    | Value                                                        |
| ---------------------- | ------------------------------------------------------------ |
| accountId              | **integer.** The ID of the account holding the balance in the specified asset. |
| assetId                | **integer.** The ID of the asset (product) whose balance is held by the specified account. |
| providerId             | **integer.** The ID of the Account Provider that handles the asset specified in *assetId.* |
| sequenceId             | **integer.** An integer that both identifies and shows the order in which these balances were returned. |
| balanceAmount          | **real.** The balance that the specified account holds in the specified asset. |
| totalReceived          | **real.**                                                    |
| depositInfos           | **array of *depositInfo* objects.** An array of *depositInfo* objects, each element of which describes a single deposit into the Asset Manager from the specified account using the specified Account Provider. The key-value pairs of a *depositInfo* object vary from Account Provider to Account Provider. |
| depositReceivedTxIds   | **array of deposit transaction IDs.** An array of deposit-received transaction ID values for the transactions that the specified account made of the specified asset using the specified Account Provider. |
| withdrawSubmittedTxIds | **array of submitted withdrawal transaction IDs.** An array of transaction IDs identifying submitted withdrawal transactions that the specified account made for the specified asset using the specified Account Provider. |
| withdrawConfirmedTxIds | **array of confirmed withdrawal transaction IDs.** An array of transaction IDs identifying completed and confirmed withdrawal transactions that the specified account made for the specified asset using the specified Account Provider. |

### *assetStates* array

Each element of the *assetStates* array shows the state of a different asset held by the account.

| Key            | Value                                                        |
| -------------- | ------------------------------------------------------------ |
| messageVersion | **integer.**                                                 |
| isFrozen       | **integer.** If the value of *isFrozen* is *true,* then this account cannot trade in this asset. |
| accountId      | **integer.** The ID of the account whose information is being returned. |
| assetId        | **integer.** The ID of the asset (product)                   |
| totalBalance   | **real.** The total quantity of specified asset held by the account , taking into consideration the array of balances, deposits, and withdrawals. |
| totalHold      | **real.** The total quantity of specified asset currently under hold for the account. |
| holds          | **array of *holds* objects.** See the description of the *holds* array, above. |
| balances       | **array of *balances* objects.** See the description of the *balances* array, above. |

### *AccountState* object

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| assetManagerId        | **integer.** The ID of the Asset Manager associated with the specified account. |
| accountId             | **integer.** The ID of the account associated with the Asset Manager. |
| isFrozen              | **Boolean.** Is the account allowed to trade? If the value of *isFrozen* is *true,* the account cannot trade. If the value of *isFrozen* is *false,* the account can trade. |
| assetStates           | **array of *assetStates* objects.** See the explanation of the key-value pairs of the *assetStates* array, above. |
| messageType           | **integer.**                                                 |
| messageSequenceNumber | **integer.**                                                 |
| availableBalance      | **real.**                                                    |

### Overall Response

| Key                   | Value                                                        |
| --------------------- | ------------------------------------------------------------ |
| AccountState          | **json object.** See the description of the *AccountState* object, above. |
| messageType           | **integer.**                                                 |
| stateObjectId         | **string.** A globally unique ID (GUID) that identifies this specific set of state information. |
| messageSequenceNumber | **integer.**                                                 |
| result     | **Boolean.** If the call has been successfully received by the Order Management System, returns *true;* otherwise returns *false.* |
| errormsg   | **string.** A successful receipt of the call returns *null.* For an unsuccessful call, the value of *errormsg* can return:<br /><br />Not Authorized (errorcode 20)<br />Invalid Request (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| statusCode | **integer.** If the value of *result* is *false,* *statusCode* can return:<br />**32** Not Authorized<br />**33** Asset_Manager_Not_Found |


