## RemoveUserConfig

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Removes a key-value pair from a user's config.

### Request

```json
{
    "userId": 0,
    "userName": "",
    "key": ""
}
```

| Key      | Value                                                        |
| -------- | ------------------------------------------------------------ |
| userId   | **integer.** The ID of the user whose config key-value pair you want to remove. |
| userName | **string.** The name of the user whose config key-value pair you want to remove. |
| key      | **string.** The name of the key that you want to remove.     |

### Response

```json
{
    "result": true
}
```

| Key    | Value                                                        |
| ------ | ------------------------------------------------------------ |
| result | **Boolean.** A *true* response means that the Exchange has successfully removed the config key-value pair. A *false* response means that the Exchange has not successfully removed the config key-value pair. |


