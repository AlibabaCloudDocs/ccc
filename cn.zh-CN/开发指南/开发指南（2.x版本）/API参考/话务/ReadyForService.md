# ReadyForService

调用接口ReadyForService就绪空闲。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ReadyForService&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ReadyForService|系统规定参数。取值：ReadyForService。 |
|DeviceId|String|是|ACC-YUNBS-1.0.10-bsd87c04aaa8f7000176ad354b1c|座席端提供的唯一ID，用来表示一个座席工作台，一个座席可以有多个不同类型的座席台，比如浏览器，iOS, Android等， 但是在同一时间，只能有一个生效。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|UserId|String|否|user-test@ccc-test|用户ID，格式为username@domain。 |
|OutboundScenario|Boolean|否|false|仅外呼模式。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|BreakCode|String|无|小休状态码。 |
|DeviceId|String|无|如果座席注册了SIP话机，则此参数是SIP话机设备的设备ID，否则为空。 |
|Extension|String|80011474|座席分机号，一共8位 如果一个用户账号有多种设备，则多个设备用一个分机号，且同一时间只有一个设备可用。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|无|在呼叫状态时的通话ID。 |
|OutboundScenario|Boolean|false|仅外呼。 |
|SignedSkillGroupIdList|List|无|签入的技能组ID列表。 |
|UserId|String|user-test@ccc-test|用户ID，格式为username@domain。 |
|UserState|String|OFFLINE|座席状态码。 |
|WorkMode|String|ON\_SITE|工作模式。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|返回参数。 |
|RequestId|String|CC49060B-87ED-489A-AD3D-00E57775DBFF|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ReadyForService
&DeviceId=ACC-YUNBS-1.0.10-bsd87c04aaa8f7000176ad354b1c
&InstanceId=ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>CC49060B-87ED-489A-AD3D-00E57775DBFF</RequestId>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <Extension>80011474</Extension>
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
	"RequestId": "CC49060B-87ED-489A-AD3D-00E57775DBFF",
	"HttpStatusCode": "200",
	"Data": {
		"Extension": "80011474",
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

