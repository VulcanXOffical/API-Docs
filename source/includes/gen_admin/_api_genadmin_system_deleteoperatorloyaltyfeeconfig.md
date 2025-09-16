## DeleteOperatorLoyaltyFeeConfig

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Deletes an existing operator loyalty configuration.

You can set one Loyalty Token per Order Management System. An OMS is not required to offer a Loyalty Token or fee.

Create an Operator Loyalty Fee using the call **CreateOperatorLoyaltyFeeConfig.**

### Request

```json
{
    "omsId": 0,
    "loyaltyProductId": 0,
    "loyaltyDiscount": 0.0,
    "referenceProductId": 0,
    "referenceProductPrice": 0.0,
    "isEnabled": true,
    "lastUpdated": "0001-01-01T00:00:00",
    "updatedBy": 0
}
```
Only the values for *omsId* and *loyaltyProductId* are required for deleting the specific loyalty fee configuration. Other values are optiona.

| Key                  | Value                                                        |
| -------------------- | ------------------------------------------------------------ |
| omsId                | **integer.** REQUIRED The ID of the Order Management System where the Loyalty Token exists. |
| loyaltyProductId     | **integer.** REQUIRED The ID of the loyalty product, a cryptocurrency. |
| loyaltyDiscount      | **real.** The discount from the standard transaction fee that you are willing to apply. |
| referenceProductId   | **integer.** The ID of the default base currency to use to calculate the exchange rate between regular fee products and the discount product. |
| referenceProductPrice | **real.** The default market value of a product expressed in a default base currency to use in the event there is no "last traded price" for the loyalty product market. |
| isEnabled            | **Boolean.** When *true,* allows transactions to use the Loyalty Token and Fee. |
| lastUpdated          | **string.** The date and time when the loyalty configuration was last updated, expressed in Microsoft Ticks format and UTC time zone. |
| updatedBy            | **integer.** The ID of the operator who made the most recent configuration change. |

### Response

```json
{
    "result": true,
    "errormsg": "",
    "errorcode": 0,
    "detail": ""
}
```
The Response is a standard response object.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| result    | **Boolean.** If the call has been successfully received by the Order Management System, *result* is *true;* otherwise it is *false.* |
| errormsg  | **string.** A successful receipt of the call returns *null.* The *errormsg* key for an unsuccessful call returns one of the following messages:<br />Not Authorized (errorcode 20)<br />Invalid Response (errorcode 100)<br />Operation Failed (errorcode 101)<br />Server Error (errorcode 102)<br />Resource Not Found (errorcode 104)<br />Operation Not Supported (errorcode 106) |
| errorcode | **integer.** A successful receipt of the call returns 0. An unsuccessful receipt of the call returns one of the *errorcodes* shown in the *errormsg* list. |
| detail    | **string.** Message text that the system may send.           |

