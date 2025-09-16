## GetAllUserInstrumentPermissions

**Category:** User<br />**Permissions:** Operator, Company<br />**Call Type:** Synchronous

Retrieves instrument permissions (permission to trade) for a specific user.

### Request

```json
{
    "userId":0
}
```

| Key    | Value                                                        |
| ------ | ------------------------------------------------------------ |
| userId | **integer.** The ID of the single user whose instrument permissions you want to return. The call assumes the current Order Management System. |

### Response

```json
[
    {
     "userId":0,
     "omsId":0,
     "instrumentId":0
    },
]
```

Returns an array listing the instruments that a given user is able to trade on a given OMS.

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| userId       | **integer.** The ID of the user whose instrument permission is being returned. |
| omsId        | **integer.** The ID of the Order Management System on which the instrument permission is granted to the user. |
| instrumentId | **integer.** The ID of the instrument whose permission to trade is granted to the user. |


