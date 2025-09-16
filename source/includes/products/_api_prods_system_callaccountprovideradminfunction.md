## CallAccountProviderAdminFunction

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Executes a custom function on a specific Account Provider and Asset Manager, and passes in any necessary parameters. A list of functions and their parameter descriptions can be returned for each Account Provider by calling **GetAccountProviderAdminFunctions.**

### Request

```json
{
    "omsId": 1,
    "assetManagerId": 1,
    "accountProviderId": 1,
    "functionName": "Function1",
    "functionParams": [
        "Name": "String",
        "ParamType": 0,
        "Value": 1
    ]
}
```

| Key               | Value                                                        |
| ----------------- | ------------------------------------------------------------ |
| omsId             | **integer.** The ID of the Order Management System on which the Account Provider and Asset Manager operate. |
| assetManagerId    | **integer.** The ID of the Asset Manager. Different Order Management Systems may link to different Asset Manager IDs. |
| accountProviderId | **integer.** The ID of the Account Provider whose function you want to execute. |
| functionName      | **string.** The name of the function you want to execute.    |
| functionParams    | **array** The array holds the function parameters and their values *in a specific order* that are passed to the Account Provider's function. Example KVPs follow. |
| Name              | **string.** EXAMPLE The name of the first parameter          |
| ParamType         | **integer.** EXAMPLE An integer defining the type of paramater being passed. One of:<br />**0** StringValue<br />**1** IntegerValue<br />**2** DecimalValue<br />**3** Selection<br />**4** LongValue  |
| Value             | **variable.** EXAMPLE The value of the parameter being passed. This value may be string, integer, real, or any other value required by the Account Provider's function. It must conform to the value of *ParamType.* |

### Response

```json
{
    "Successful": true,
    "Function": "Function1",
    "Result": "Response of the call",
    "ErrorMsgs": ""
}
```

| Key        | Value                                                        |
| ---------- | ------------------------------------------------------------ |
| Successful | **Boolean.** If the function call was transmitted to the Account Provider successfully, this value is *true.* If not, this value is *false.* |
| Function   | **string.** The name of the function called, echoed from the Request. |
| Result     | **variable** The result of the call, passed back. This may be a string, integer, or other value as determined by the Account Provider's function. |
| ErrorMsgs  | **string.** If the function call to the Account Provider produced an error, this message provides an explanation. |


