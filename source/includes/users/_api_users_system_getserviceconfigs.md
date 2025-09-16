## GetServiceConfigs

**Category:** System<br />**Permissions:** Operator<br />**Call Type:** Synchronous

Get the configurations for a particular service.
### Request

```json
{
	"ServiceName": ""
}
```

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| ServiceName      	  | **string.**  Name of the service to get configurations from. |

### Response

```json
[
	{
		"ServiceName": "",
		"ConfigKey": "",
		"ConfigValue": "",
		"ConfigValueType": "",
		"PreviousConfigValue": "",
		"ConfigUpdateTime": "",
		"IsMaskedOnResponse" false,
	}
]
```
Returns a list of services and their configurations associated with the service name.

| Key         | Value                                                        |
| ----------- | ------------------------------------------------------------ |
| ServiceName      	  | **string.**  Name of the service to get configurations from. |
| ConfigKey      	  | **string.**  Service name associated with the configuration. |
| ConfigValue      	  | **string.**  Configuration of service. |
| ConfigValueType     | **string.**  Data type of ConfigValue |
| PreviousConfigValue | **string.**  Previous configuration of service, "void" if no previous configuration |
| ConfigUpdateTime    | **string.**  Last time that configuration was updated. |
| IsMaskedOnResponse  | **Boolean.**  Should always be false if showing up in response. |
