## Background: APAD Private Shares API

APAD (*AlphaPoint Asset Digitization*) allows organizations to create and monetize assets that are not national or cryptocurrencies, and to offer them on the AlphaPoint Exchange.

The Private Shares API (PSAPI) is a web socket server and API that augments the AlphaPoint Exchange API. It adds the concepts of *asset issuers* (essentially, companies) and provides different roles for the management of digital assets. For example, company admin, company agent, company shareholder, investor, or marketmaker.

### Requesting and Receiving a Reply

The PSAPI is an asynchronous Websocket API. All requests are formatted as remote procedure calls (RPC calls), as shown in Example 1 and Example 2.

> Example 1: Request Format

```json
{
    "MessageType":"RPCCall",
    "FunctionName":"<name of call>",
    "Parameter":"<payload>",
    "RequestUniqueId":GUID
}
```

#### Example 1 Fields

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| MessageType     | **string.** The type of message. Always "RPCCall" for calls. |
| FunctionName    | **string.** The name of the API call &mdash; for example "CreateUser" or "GetCompanies". |
| Parameter       | **string.** The key-value pairs of the call, as detailed in this API. |
| RequestUniqueId | **string.** The globally unique identifier (GUID) for this call. |

> Example 2: Reply Format

```json
{
    "MessageType":"RCPReply",
    "Parameter":"<stringified JSON>",
    "RequestUniqueId":GUID
}
```

#### Example 2 Fields

| Key             | Value                                                        |
| --------------- | ------------------------------------------------------------ |
| MessageType     | **string.** The type of message. Always "RCPReply" for replies. |
| Parameter       | **string.** Stringified JSON; usually key-value pairs, as detailed in this API. |
| RequestUniqueId | **string** An echo of the GUID sent in the request.          |

The reply parameter can indicate whether the system has received the Request. This does not indicate that the content of the Request has been acted on; only that the system has received it in good order. You may need to confirm the action of a Request. For example, after you issue **CreateCompany**, you may wish to issue **GetCompanies** to confirm that the company was created correctly. 

Example 3 shows a successful receipt of a call, and Example 4 shows an unsuccessful receipt of a call.

> Example 3: Successful receipt

```json
{
    "success":true,
    "payload":"<stringified JSON>"
}
```

> Example 4: Unsuccessful receipt

```json
{
    "success":false,
    "Err":""
}
```

### Authentication

To use the APAD API, a user first authenticates with the AlphaPoint Exchange, using the APEX API (for example, using **AuthenticateUser**) to obtain a *sessionId*. That session ID must be passed to the APAD API with every request. It uniquely identifies the user &mdash; and all of that user's permissions and roles &mdash; for the current session.
