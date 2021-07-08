# SignInGroup

调用SignInGroup坐席签入。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=SignInGroup&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SignInGroup|系统规定参数。取值：SignInGroup。 |
|DeviceId|String|是|ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90|座席端提供的唯一ID，用来表示一个座席工作台。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|UserId|String|否|user-test@ccc-test|呼叫中心实例的用户ID，实例内唯一。 |
|SignedSkillGroupIdList|String|否|\["skg-test1@ccc-test","skg-test2@ccc-test"\]|签入的技能组ID列表。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|BreakCode|String|Warm-up|小休状态码。 |
|DeviceId|String|ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90|座席端提供的唯一ID，用来表示一个座席工作台。 |
|Extension|String|80326034|分机号码。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|无|在呼叫状态时的通话ID。 |
|OutboundScenario|Boolean|false|是否进外呼。 |
|SignedSkillGroupIdList|List|\["skg-test1@ccc-test","skg-test2@ccc-test"\]|签入的技能组ID列表。 |
|UserId|String|user-test@ccc-test|呼叫中心用户ID。 |
|UserState|String|BREAK|座席状态。 |
|WorkMode|String|ON\_SITE|工作模式。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|响应参数。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=SignInGroup
&DeviceId=ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90
&InstanceId=ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Params>无</Params>
<Data>
    <Extension>80326034</Extension>
    <UserState>BREAK</UserState>
    <InstanceId>ccc-test</InstanceId>
    <UserId>user-test@ccc-test</UserId>
    <DeviceId>ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90</DeviceId>
    <BreakCode>Warm-up</BreakCode>
    <OutboundScenario>false</OutboundScenario>
    <WorkMode>ON_SITE</WorkMode>
    <SignedSkillGroupIdList>["skg-test1@ccc-test","skg-test2@ccc-test"]</SignedSkillGroupIdList>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
	"Message": "无",
	"HttpStatusCode": "200",
	"Params": "无",
	"Data": {
		"Extension": "80326034",
		"UserState": "BREAK",
		"InstanceId": "ccc-test",
		"UserId": "user-test@ccc-test",
		"DeviceId": "ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90",
		"BreakCode": "Warm-up",
		"OutboundScenario": "false",
		"WorkMode": "ON_SITE",
		"SignedSkillGroupIdList": "[\"skg-test1@ccc-test\",\"skg-test2@ccc-test\"]"
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

