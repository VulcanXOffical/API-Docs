## GetProductAttributes  

**Category:** User<br />
**Permissions:** Operator, Company<br />
**Call Type:** Synchronous

Retrieves the set of key-value attributes for a product.

### Request

```json
{
    "OMSId": 1,
    "ProductId": 1
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| OMSId     | **integer.** The ID of the Order Management System where the product is listed. |
| ProductId | **Integer.** The ID of the product whose attributes the call returns. |

### Response

```json
[
    {
        "omsId":0,
        "productId":0,
        "keyName":"",
        "keyValue":""
    },
]
```

The response returns an array of information about the key-value pair attributes associated with the product.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| omsId     | **integer.** The ID of the Order Management System returning the product attributes. |
| productId | **integer.** The ID of the product whose attributes are being returned. |
| keyName   | **string.** The key portion of the key-value pair that describes the attribute. |
| keyValue  | **string.** The value portion of the key-value pair that describes the attribute. |


