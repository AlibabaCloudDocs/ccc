# ChangeWorkMode

调用接口ChangeWorkMode来改变工作模式。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ChangeWorkMode&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ChangeWorkMode|系统规定参数。取值：ChangeWorkMode。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|WorkMode|String|是|ON\_SITE|工作模式代码 |
|UserId|String|否|user-test@ccc-test|用户ID，格式为username@domain。 |
|DeviceId|String|否|ACC-YUNBS-1.0.10-bs990cd82101cc000176af19ec8e|座席端提供的唯一ID，用来表示一个座席工作台，一个座席可以有多个不同类型的座席台，比如浏览器，iOS, Android等， 但是在同一时间，只能有一个生效。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|BreakCode|String|Warm-up|小休状态码。 |
|DeviceId|String|ACC-YUNBS-1.0.10-bs990cd82101cc000176af19ec8e|设备标示。 |
|Extension|String|80011474|座席分机号，一共8位 如果一个用户账号有多种设备，则多个设备用一个分机号，且同一时间只有一个设备可用。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|无|在呼叫状态时的通话ID。 |
|OutboundScenario|Boolean|false|仅外呼。 |
|SignedSkillGroupIdList|List|\["skill-group@ccc-test"\]|签入的技能组ID列表。 |
|UserId|String|user-test@ccc-test|用户ID，格式为username@domain。 |
|UserState|String|OFFLINE|座席状态码。 |
|WorkMode|String|ON\_SITE|工作模式。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|返回参数。 |
|RequestId|String|87731ED1-6224-48A5-99E3-6237FF9B1C00|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ChangeWorkMode
&InstanceId=ccc-test
&WorkMode=ON_SITE
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>87731ED1-6224-48A5-99E3-6237FF9B1C00</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Params>无</Params>
<Data>
    <Extension>80011474</Extension>
    <UserState>OFFLINE</UserState>
    <InstanceId>ccc-test</InstanceId>
    <UserId>user-test@ccc-test</UserId>
    <DeviceId>ACC-YUNBS-1.0.10-bs990cd82101cc000176af19ec8e</DeviceId>
    <BreakCode>Warm-up</BreakCode>
    <OutboundScenario>false</OutboundScenario>
    <WorkMode>ON_SITE</WorkMode>
    <JobId>无</JobId>
    <SignedSkillGroupIdList>["skill-group@ccc-test"]</SignedSkillGroupIdList>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "87731ED1-6224-48A5-99E3-6237FF9B1C00",
	"Message": "无",
	"HttpStatusCode": "200",
	"Params": "无",
	"Data": {
		"Extension": "80011474",
		"UserState": "OFFLINE",
		"InstanceId": "ccc-test",
		"UserId": "user-test@ccc-test",
		"DeviceId": "ACC-YUNBS-1.0.10-bs990cd82101cc000176af19ec8e",
		"BreakCode": "Warm-up",
		"OutboundScenario": "false",
		"WorkMode": "ON_SITE",
		"JobId": "无",
		"SignedSkillGroupIdList": "[\"skill-group@ccc-test\"]"
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Parameter.Enumeration|The parameter %s must be one of the value of enumeration %s.|该参数必须为系统限定的枚举值之一。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

