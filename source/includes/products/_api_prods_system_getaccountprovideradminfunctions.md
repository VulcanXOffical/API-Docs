## GetAccountProviderAdminFunctions

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns a list of available permissions, API calls, and Admin functions (and parameters) exposed by a specific Account Provider.

You call these functions and permissions using **CallAccountProviderAdminFunctions.** 

### Request

```json
{
    "OMSId": 1,
    "AssetManagerId": 1,
    "AccountProviderId": 1
}
```

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| OMSId             | **integer.** The ID of the Order Management System with which the Account Provider is associated. |
| AssetManagerId    | **integer.** The ID of the asset manager with which the Account Provider is associated. |
| AccountProviderId | **integer.** The ID of the Account Provider whose functions you want to get. |

### Response

```json
[
    {
        "AssetManagerId": 1,
        "AccountProviderId": 1,
        "FunctionName": "GetHotBalance",
        "FunctionParams": [ ]
    },
    {
        "AssetManagerId": 1,
        "AccountProviderId": 1,
        "FunctionName": "GetColdBalance",
        "FunctionParams": [ ]
    }
]
```

The Response varies from Account Provider to Account Provider. It returns an array of functions and their parameters.

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| AssetManagerId    | **integer.** The ID of the asset manager with which the Account Provider is associated. |
| AccountProviderId | **integer.** The ID of the Account Provider that implements the function. |
| FunctionName      | **string.** The calling name of the function. Functions vary by Account Provider. |
| FunctionParams    | **array of key-value pairs.** The parameters required by the function, by name and in order. These parameters may be a mix of strings, integers, and reals. The parameters vary function-by-function and each consists of a key-value pair. See **CallAccountProviderAdminFunction** for an example of how a function and its parameters are called. |


