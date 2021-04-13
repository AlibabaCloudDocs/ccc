# ReleaseCall

调用ReleaseCall结束通话。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ReleaseCall&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ReleaseCall|系统规定参数。取值：ReleaseCall。 |
|DeviceId|String|是|ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90|座席端提供的唯一ID，用来表示一个座席工作台。 |
|InstanceId|String|是|user-test@ccc-test|呼叫中心实例ID。 |
|JobId|String|是|job-65382141036853491|话务ID。 |
|UserId|String|否|user-test@ccc-test|呼叫中心实例的用户ID，实例内唯一。 |
|ChannelId|String|否|ch:user:139xxxx0501-\>80326034:1609138902226:job-65382141036853491|通道ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|CallContext|Struct| |话务上下文环境。 |
|ChannelContexts|Array of ChannelContext| |各个Channel的信息。 |
|AssociatedData|Map|无|随路数据。 |
|CallType|String|OUTBOUND|呼叫类型。 |
|ChannelId|String|ch:user:139xxxx0501-\>80326034:1609138902226:job-65382141036853491|通道ID。 |
|ChannelState|String|CREATED|状态。 |
|Destination|String|139xxxx0501|接收方。 |
|JobId|String|job-65382141036853491|话务ID。 |
|Originator|String|083xxxx0019|发起方。 |
|ReleaseInitiator|String|139xxxx0501|挂断方。 |
|ReleaseReason|String|404 - No destination|挂断原因。 |
|Timestamp|Long|1609138903315|状态数据上次变更时间戳。 |
|UserExtension|String|80326034|该Channel的座席的分机号。 |
|UserId|String|user-test@ccc-test|该Channel的用户ID。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|job-65382141036853491|话务ID。 |
|UserContext|Struct| |用户上下文环境。 |
|BreakCode|String|Warm-up|小休状态码。 |
|DeviceId|String|ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90|座席端提供的唯一ID，用来表示一个座席工作台。 |
|Extension|String|80326034|分机号码。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|job-65382141036853491|在呼叫状态时的通话ID。 |
|OutboundScenario|Boolean|false|是否只外呼。 |
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
http(s)://[Endpoint]/?Action=ReleaseCall
&DeviceId=ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90
&InstanceId=user-test@ccc-test
&JobId=job-65382141036853491
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
    <UserContext>
        <Extension>80326034</Extension>
        <UserState>BREAK</UserState>
        <InstanceId>ccc-test</InstanceId>
        <UserId>user-test@ccc-test</UserId>
        <DeviceId>ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90</DeviceId>
        <BreakCode>Warm-up</BreakCode>
        <OutboundScenario>false</OutboundScenario>
        <WorkMode>ON_SITE</WorkMode>
        <JobId>job-65382141036853491</JobId>
        <SignedSkillGroupIdList>["skg-test1@ccc-test","skg-test2@ccc-test"]</SignedSkillGroupIdList>
    </UserContext>
    <CallContext>
        <InstanceId>ccc-test</InstanceId>
        <JobId>job-65382141036853491</JobId>
        <ChannelContexts>
            <Destination>139xxxx0501</Destination>
            <ChannelState>CREATED</ChannelState>
            <ReleaseInitiator>139xxxx0501</ReleaseInitiator>
            <CallType>OUTBOUND</CallType>
            <AssociatedData/>
            <ChannelId>ch:user:139xxxx0501-&gt;80326034:1609138902226:job-65382141036853491</ChannelId>
            <Timestamp>1609138903315</Timestamp>
            <ReleaseReason>404 - No destination</ReleaseReason>
            <Originator>083xxxx0019</Originator>
            <UserId>user-test@ccc-test</UserId>
            <UserExtension>80326034</UserExtension>
            <JobId>job-65382141036853491</JobId>
        </ChannelContexts>
    </CallContext>
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
		"UserContext": {
			"Extension": "80326034",
			"UserState": "BREAK",
			"InstanceId": "ccc-test",
			"UserId": "user-test@ccc-test",
			"DeviceId": "ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90",
			"BreakCode": "Warm-up",
			"OutboundScenario": "false",
			"WorkMode": "ON_SITE",
			"JobId": "job-65382141036853491",
			"SignedSkillGroupIdList": "[\"skg-test1@ccc-test\",\"skg-test2@ccc-test\"]"
		},
		"CallContext": {
			"InstanceId": "ccc-test",
			"JobId": "job-65382141036853491",
			"ChannelContexts": [{
				"Destination": "139xxxx0501",
				"ChannelState": "CREATED",
				"ReleaseInitiator": "139xxxx0501",
				"CallType": "OUTBOUND",
				"AssociatedData": "",
				"ChannelId": "ch:user:139xxxx0501->80326034:1609138902226:job-65382141036853491",
				"Timestamp": "1609138903315",
				"ReleaseReason": "404 - No destination",
				"Originator": "083xxxx0019",
				"UserId": "user-test@ccc-test",
				"UserExtension": "80326034",
				"JobId": "job-65382141036853491"
			}]
		}
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

