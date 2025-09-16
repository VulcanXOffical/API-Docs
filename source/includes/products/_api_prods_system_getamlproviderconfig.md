## GetAmlProviderConfig

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns an AML ("anti-money laundering") provider configuration.

All key-value pairs of the Request are required.

### Request

```json
{
    "OMSId": 0,
    "ProductId": 1
}
```

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| OmsId           | **integer.** The Order Management System on which the anti-money laundering service will function. |
| ProductId       | **integer.** The ID of the product for which this AML service provider will function. Each product ID may have its own AML service provider. |

### Response
```json
{
    "omsId": 0,
    "productId": 0,
    "url": "",
    "amlProviderType": 0,
    "apiToken": "",
    "enabled": true
}
```

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| omsId           | **integer.** The Order Management System on which the anti-money laundering service functions. |
| productId       | **integer.** The ID of the product for which this AML service provider functions. Each product ID may have its own AML service provider. |
| url             | **string.** The URL address of the AML service provider.     |
| amlProviderType | **integer.** There are three AML configuration settings, or *types:*<br />**0** PassThrough &mdash; Allows cryptocurrency to be freely deposited.<br />**1** ChainAnalysis &mdash; A third-party that scores cryptocurrency deposits according to configurations from the Blockchain.<br />**2** Manual &mdash; Used for fiat (national) currency deposits. |
| apiToken        | **string.** Token used by the Exchange to contact AML providers.   |
| enabled         | **Boolean.** If *true* the AML configuration is active for this product. If *false,* the configuration is not live. |


