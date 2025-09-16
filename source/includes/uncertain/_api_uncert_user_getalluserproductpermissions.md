## GetAllUserProductPermissions

**Category:** User<br />**Permissions:** Operator, Company<br />**Call Type:** Synchronous

Retrieves an array of product permissions (permission to trade) for a specific user.

### Request

```json
{
    "userIds":1
}
```

| Key    | Value                                                        |
| ------ | ------------------------------------------------------------ |
| userIds | **integer.** The ID of the single user whose product permissions will be returned. The call assumes the current Order Management System. |

### Response

```json
[
    {"userId":0,
     "omsId":0,
     "productId":0
    },
]
```

Returns an array listing the products that a given user is able to trade on a given OMS.

| Key          | Value                                                        |
| ------------ | ------------------------------------------------------------ |
| userId       | **integer.** The ID of the user whose product permission is being returned. |
| omsId        | **integer.** The ID of the Order Management System on which the product permission is granted to the user. |
| instrumentId | **integer.** The ID of the product whose permission to trade is granted to the user. |


