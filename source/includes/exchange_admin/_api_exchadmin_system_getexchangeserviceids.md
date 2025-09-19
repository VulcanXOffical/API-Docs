## GetExchangeServiceIds

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** **Synchronous**

Retrieves an array of the matching engine

### Request

```json
{
}
```
No payload for GetExchangeServiceIds

### Response

```json
[
    {
        "Name": "V2ExchangeCore|1",
        "ServiceId": "Matching Engine"
        "URI": null
    }
]
```
| Key                      | Value                                                        |
| ------------------------ | ------------------------------------------------------------ |
| Name             | **string.** Name of exchange |
| ServiceId		   | **string.** Always Matching Engine |
| URI              | **string.** Exchange ID, otherwise *null.*  |

