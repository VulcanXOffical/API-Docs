## GetCompletedFourEyeRequests

**Category:** Four Eye <br />**Permissions:** Operator <br />**Call Type:** Synchronous

Retrieves completed Four Eye Requests, approved or denied.

### Request

```json
{
    "RequestId": 1,
    "RequesterUserId": 1,
    "SecondEyesUserId": "",
    "EndpointName": "",
    "EndpointType": 1,
    "RequestStartTime": 1531359834,
    "RequestEndTime": 1551359834,
    "CompletedStartTime": 1531359834,
    "CompletedEndTime": 1551359834,
    "StartIndex": 1,
    "Depth": 200
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| RequestId      	  | **integer.** A number assigned to identify this request. |
| RequesterUserID     | **integer.** The user ID of the user requesting the endpoint of the pending four eye requests. |
| SecondEyesUserID    | **integer.** The user ID of the user who reviewed the four eyes request. |
| EndpointName    	  | **integer.** The endpoint the user tried to call. |
| EndpointType     	  | **integer.** Endpoint type for the pending four eye request. Numbers correspond to the following endpoint types: <br />Parallel: 1 <br /> SystemSequential: 2 <br /> UserSequential: 3 <br />|
| RequestStartTime    | **integer.** Returned pending four eye requests start from this epoch time.  |
| RequestEndTime	  | **integer.** Returned pending four eye requests end at this epoch time. |
| CompletedStartTime    | **integer.** Returned pending four eye requests start from this epoch time.  |
| CompletedEndTime	  | **integer.** Returned pending four eye requests end at this epoch time. |
| StartIndex      	  | **integer.** Starting index for pending four eye requests return list. |
| Depth  	     	  | **integer.** Maximum number of pending four eye requests returned. |

### Response

```json
[
	{
	    "RequestId": 1,
	    "RequesterUserId": 3,
	    "EndpointName": "",
	    "Payload": "",
	    "EndpointType": 1,
	    "RequestTime": 1531359834,
	}
]
```
The Response is an array of pending Four Eyes Requests.

| Key       | Value                                                        |
| --------- | ------------------------------------------------------------ |
| RequestId      	  | **integer.** A number assigned to identify this request. |
| RequesterUserID     | **integer.** The user ID of the user requesting the endpoint of the pending four eye requests. |
| Payload    	  | **string.** GetPendingFourEyeRequests request payload  |
| EndpointType | **integer.** Endpoint type for the pending four eye request. Numbers correspond to the following endpoint types: <br />Parallel: 1 <br /> SystemSequential: 2 <br /> UserSequential: 3 <br /> |
| RequestTime    | **long integer.** Epoch time of call for GetPendingFourEyeRequests  |
