# ResetAgentState

调用接口ResetAgentState重置坐席状态。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ResetAgentState&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ResetAgentState|系统规定参数。取值：ResetAgentState。 |
|DeviceId|String|是|ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90|座席端提供的唯一ID，用来表示一个座席工作台，一个座席可以有多个不同类型的座席台，比如浏览器，iOS, Android等， 但是在同一时间，只能有一个生效。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|UserId|String|否|user-test@ccc-test|用户ID，格式为username@domain。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|BreakCode|String|无|小休状态码 |
|DeviceId|String|无|设备标示 |
|Extension|String|80011112|座席分机号，一共8位 如果一个用户账号有多种设备，则多个设备用一个分机号，且同一时间只有一个设备可用 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|无|在呼叫状态时的通话ID。 |
|OutboundScenario|Boolean|false|仅外呼。 |
|SignedSkillGroupIdList|List|无|签入的技能组ID列表。 |
|UserId|String|user-test@ccc-test|用户ID。 |
|UserState|String|OFFLINE|用户状态。 |
|WorkMode|String|ON\_SITE|工作模式。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|参数信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ResetAgentState
&DeviceId=ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90
&InstanceId=ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <Extension>80011112</Extension>
    <UserState>OFFLINE</UserState>
    <InstanceId>ccc-test</InstanceId>
    <UserId>user-test@ccc-test</UserId>
    <OutboundScenario>false</OutboundScenario>
    <WorkMode>ON_SITE</WorkMode>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
	"HttpStatusCode": "200",
	"Data": {
		"Extension": "80011112",
		"UserState": "OFFLINE",
		"InstanceId": "ccc-test",
		"UserId": "user-test@ccc-test",
		"OutboundScenario": "false",
		"WorkMode": "ON_SITE"
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|404|NotExists.UserId|The user %s does not exist in instance %s.|呼叫中心实例中不存在指定的用户。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

