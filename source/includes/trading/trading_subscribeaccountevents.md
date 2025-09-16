## SubscribeAccountEvents

**Category:** Trading<br />
**Permissions:** Trading<br />
**Call Type:** Synchronous

Subscribe to account-level events, such as orders, trades, deposits and withdraws. Can be used to monitor account transactions real-time.

### Request

```javascript
const { APEX } = require("VulcanX-apex-api");
const apex = new APEX("websocket url goes here...");

await apex.RPCPromise("SubscribeAccountEvents", {
  OMSId: 1,
  AccountId: 1,
});
```

```http
//SubscribeAccountEvents is not available in HTTP. Subscription APIs is not supported in HTTP.
```

| Key       | Value                                                                                             |
| --------- | ------------------------------------------------------------------------------------------------- |
| OMSId     | **integer.** The ID of the OMS on which the snapshot of all instruments will be taken._required._ |
| AccountId | **integer.** The ID of the account to subscribe with._required._                                  |

### Response

```javascript
{
    Subscribed: true
}

//Example account event that can be received
{
  m: 3,
  i: 2,
  n: 'WithdrawTicketUpdateEvent',
  o: '{"AssetManagerId":1,"AccountProviderId":0,"AccountId":7,"AccountName":"harolds","AssetId":3,"AssetName":"TBTC","Amount":0.0010000000000000000000000000,"NotionalValue":0.0010000000000000000000000000,"NotionalProductId":1,"TemplateForm":"{\\"Fullname\\":\\"Harold\\"}","TemplateFormType":null,"OMSId":1,"RequestCode":"ef0ec64d-953b-477d-80b7-c3b0bf4cad64","RequestIP":null,"RequestUserId":1,"RequestUserName":"admin","OperatorId":1,"Status":"Pending2Fa","FeeAmt":0.0000000000000000000000000000,"UpdatedByUser":0,"UpdatedByUserName":null,"TicketNumber":292,"WithdrawTransactionDetails":"{\\"TxId\\":null,\\"ExternalAddress\\":null,\\"Amount\\":0,\\"Confirmed\\":false,\\"LastUpdated\\":\\"0001-01-01T00:00:00.000Z\\",\\"TimeSubmitted\\":\\"0001-01-01T00:00:00.000Z\\",\\"AccountProviderName\\":null,\\"AccountProviderId\\":0}","RejectReason":null,"CreatedTimestamp":"2023-03-23T12:48:31.067Z","LastUpdateTimestamp":"2023-03-23T12:48:31.067Z","CreatedTimestampTick":638151725110676052,"LastUpdateTimestampTick":638151725110676052,"Comments":[],"Attachments":[],"AuditLog":[]}'
}
{
  m: 3,
  i: 4,
  n: 'AccountPositionEvent',
  o: '{"OMSId":1,"AccountId":7,"ProductSymbol":"TBTC","ProductId":3,"Amount":1.1381543994360000000000000000,"Hold":1.1256211000000000000000000000,"PendingDeposits":0,"PendingWithdraws":0,"TotalDayDeposits":0,"TotalMonthDeposits":0,"TotalYearDeposits":0,"TotalDayDepositNotional":0,"TotalMonthDepositNotional":0,"TotalYearDepositNotional":0,"TotalDayWithdraws":0,"TotalMonthWithdraws":0,"TotalYearWithdraws":0,"TotalDayWithdrawNotional":0,"TotalMonthWithdrawNotional":0,"TotalYearWithdrawNotional":0,"NotionalProductId":1,"NotionalProductSymbol":"USD","NotionalValue":1.1381543994360000000000000000,"NotionalHoldAmount":1.1256211000000000000000000000,"NotionalRate":1,"TotalDayTransferNotional":0}'
}
```

```http
//SubscribeAccountEvents is not available in HTTP. Subscription APIs is not supported in HTTP.
```

Returns either Subscribed: true or false. If false, it means that you were not able to subscribe to events of the account. After successfully subscribing to account events, you will receive the events message for transactions that involves the account such as a withdraw transaction, the specific event name will be **WithdrawTicketUpdateEvent**
