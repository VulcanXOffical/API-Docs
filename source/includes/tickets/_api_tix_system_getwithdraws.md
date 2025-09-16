## GetWithdraws

**Category:** System<br />**Permissions:** Operator, Trading<br />**Call Type:** Synchronous

Returns a list of withdrawals for a given account ID.

Users with Trading permission can return withdrawals only for an account with which they are associated; users with Operator permission can return withdrawals for any account.

### Request

```json
{
    "OMSId": 1,
    "AccountId": 1
}
```

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| OMSId     | **integer.** The ID of the Order Management System on which the withdrawal was issued. |
| AccountId | **integer.** The ID of the account for which withdrawal information will be returned. |

### Response

```json
[
	{
		"amount": 0.0,
        "feeAmount": 0.0,
        "notionalValue": 0.0,
        "withdrawId": 0,
        "assetManagerId": 0,
        "accountId": 0,
        "assetId": 0,
        "templateForm": "{
			“TemplateType”: “TetherRPCWithdraw”,
            “Comment”: “TestWithdraw”,
            “ExternalAddress”: “ms6C3pKAAr8gRCcnVebs8VRkVrjcvqNYv3” 
 			}",
        "templateFormType": "TetherRPCWithdraw",
        "omsId": 0,
        "TicketStatus": 0,
        "ticketNumber": 0,
        "WithdrawTransactionDetails": "",
        "withdrawType": "",
        "withdrawCode": "490b4fa3-53fc-44f4-bd29-7e16be86fba3",
        "AssetType": 0,
        "reaccepted": true,
        "notionalProductId": 0
        
    },
]
```

The Response is an array of withdrawals made on the specified Order Management System for the specified account.

| Key                        | Value                                                        |
| -------------------------- | ------------------------------------------------------------ |
| amount                     | **real.** The amount of product or fractions of product being withdrawn (not the dollar value, unless the products being withdrawn are dollars). |
| feeAmount                  | **real.** The amount of withdrawal fee charged. Withdrawal fees usually are charged in the product being withdrawn. |
| notionalValue              | **real.** In some regions, withdrawals in cryptocurrency must first be converted to the local currency. Thus, the "notional value" of a withdrawal is the value of the cryptocurrency expressed in the local fiat currency. |
| withdrawId                 | **integer.** The ID of this withdrawal, assigned by the system. |
| assetManagerId             | **integer.** The ID of the Asset Manager through which the withdrawal was made. |
| accountId                  | **integer.** The ID of the account from which the withdrawal was made. |
| assetId                    | **integer.** The ID of the asset (product) being withdrawn.  |
| templateform               | **string.** The contents of the withdrawal template (key-value pairs). Templates vary from Account Provider to Account Provider, depending on the asset being withdrawn and the identity of the Account Provider. |
| templateFormType           | **string.** The name of the withdrawal template. The template controls the destination of the asset being withdrawn. To get a list of withdrawal templates available to you, call **GetWithdrawTemplateTypes.** |
| omsId                      | **integer.** The ID of the Order Management System on which the withdrawal occurred. |
| TicketStatus               | **integer.** The current status of the withdrawal ticket. Some of these statuses are valid only for cryptocurrency withdrawals (which uses an automated withdrawal process), and some are valid for fiat currency withdrawals (which requires a human admin operator). Some of these statuses are used by the AlphaPoint Exchange internally, yet they may appear on a returned withdrawal ticket.<br/ ><br />**Withdraw ticket statuses:**<br />**0** New (awaiting operator review)<br />**1** AdminProcessing (An admin is looking at the ticket)<br />**2** Accepted (withdrawal will proceed)<br />**3** Rejected (admin or automatic rejection)<br />**4** SystemProcessing (automatic processing underway)<br />**5** FullyProcessed (the withdrawal has concluded)<br />**6** Failed (the withdrawal failed for some reason)<br />**7** Pending (the admin has placed the withdrawal in pending status)<br />**8** Pending2Fa (user must click 2-factor authentication confirmation link)<br />**9** AutoAccepted (withdrawal will be automatically processed)<br />**10** Delayed (waiting for funds to be allocated for the withdrawal)<br />**11** UserCanceled (withdraw canceled by user or Superuser)<br />**12** AdminCanceled (withdraw canceled by Superuser)<br />**13** AmlProcessing (anti-money-laundering process underway)<br />**14** AmlAccepted (anti-money-laundering process complete)<br />**15** AmlRejected (withdrawal did not stand up to anti-money-laundering process)<br />**16** AmlFailed (withdrawal did not complete anti-money-laundering process)<br />**17** LimitsAccepted (withdrawal meets limits for fiat or crypto asset)<br />**18** LimitsRejected (withdrawal does not meet limits for fiat or crypto asset)<br />**19** Submitted (withdrawal sent to Account Provider; awaiting blockchain confirmation)<br />**20** Confirmed (Account Provider confirms that withdrawal is on the blockchain)<br />**21** ManuallyConfirmed (admin has sent withdrawal via wallet or admin function directly; marks ticket as FullyProcessed; debits account)<br />**22** Confirmed2Fa (user has confirmed withdraw via 2-factor authentication.) |
| ticketNumber               | **integer.** The number of the ticket, as assigned by the system (different from the ID of the withdrawal). |
| withdrawTransactionDetails | **JSON string object.** Dynamic information that changes from Account Provider to Account Provider. The values of *withdrawTransactionDetails* may (but do not have to) include key-value pairs for:<br />**TxId** transaction ID<br />**ExternalAddress**<br />**Amount**<br />**Confirmed**<br />**LastUpdated**<br />**TimeSubmitted**<br />**AccountProviderName** |
| withdrawType               | **string.** Shows whether the withdrawal is cryptocurrency or fiat (national) currency.                                            |
| withdrawCode               | **string.** A GUID that uniquely identifies the withdrawal (as opposed to the ticket representing the withdrawal). The value for *widrawCode* is the same as *requestCode* as returned by **GetWithdrawTicket** and **GetWithdrawTickets.**                                          |
| AssetType                  | **integer.** Describes the nature of the product. One of:<br />**0** Unknown (an error condition)<br />**1** NationalCurrency<br />**2** CryptoCurrency<br />**3** Contract                                          |
| reaccepted                 | **Boolean.** If a ticket was initially rejected, but later accepted for withdrawal, *true* shows that the ticket was re-accepted for processing after an initial rejection.                                          |
| notionalProductId          | **integer.** In those regions where withdrawal of cryptocurrency must be expressed in terms of local fiat currency, the *notionalProductId* expresses that local currency. |


