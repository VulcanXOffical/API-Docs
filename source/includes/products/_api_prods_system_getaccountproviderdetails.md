## GetAccountProviderDetails

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Returns the details for a specific Account Provider operating on a specific Asset Manager.

These details are returned in the Response as a dictionary, and vary from Account Provider to Account Provider. They populate a screen, so it is not necessary to parse the exact key-value pairs that are returned.

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
| AccountProviderId | **integer.** The ID of the Account Provider whose details you want to get. |

### Response

```json
{ "string1": "string", "string2": "string", "string3": "string" }
```

The Response is returned as a dictionary. Values vary from Account Provider to Account Provider. It is not necessary to parse the returned values.
