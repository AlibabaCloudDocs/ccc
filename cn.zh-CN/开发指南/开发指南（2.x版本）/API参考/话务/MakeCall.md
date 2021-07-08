# MakeCall

调用接口MakeCall进行外呼。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=MakeCall&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|MakeCall|系统规定参数。取值：MakeCall。 |
|Callee|String|是|13188888888|被叫号码。 |
|DeviceId|String|是|ACC-YUNBS-1.0.10-bsd87c04aaa8f7000176ad354b1c|座席端提供的唯一ID，用来表示一个座席工作台，一个座席可以有多个不同类型的座席台，比如浏览器，iOS, Android等， 但是在同一时间，只能有一个生效。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|UserId|String|否|user-test@ccc-test|用户ID，格式为username@domain。 |
|Caller|String|否|0109898989|主叫号码，如果是内部呼叫，这此参数无效，如果是外部呼叫，此参数是主叫PSTN号码。 |
|TimeoutSeconds|Integer|否|10|超时时间，呼叫在经过该参数指定的时间仍然未接通的情况下，则主动挂断。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|CallContext|Struct| |话务上下文环境。 |
|CallType|String|OUTBOUND|呼叫类型, 最初发起呼叫时的类型。 |
|ChannelContexts|Array of ChannelContext| |通话上下文。 |
|AssociatedData|Map|无|随路数据。 |
|CallType|String|OUTBOUND|呼叫类型, 最初发起呼叫时的类型。 |
|ChannelFlags|String|\[\]|通道标志，比如监听，辅助，静音等。 |
|ChannelId|String|ch:user:1318888888-\>80011474:1609225718294:job-65700074013925376|通道ID。 |
|ChannelState|String|NONE|状态。 |
|Destination|String|80011474|接收方。 |
|JobId|String|job-65700074013925376|话务ID。 |
|Originator|String|13188888888|发起方。 |
|ReleaseInitiator|String|无|挂断方。 |
|ReleaseReason|String|无|挂断原因。 |
|Timestamp|Long|1609225718295|状态数据上次变更时间戳。 |
|UserExtension|String|80011474|座席是否发起方。 |
|UserId|String|user-test@ccc-test|该Channel的用户ID，如果是客户通道，则userId为空。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|job-65700074013925376|话务ID。 |
|UserContext|Struct| |用户上下文环境。 |
|BreakCode|String|Warm-up|小休状态码。 |
|DeviceId|String|ACC-YUNBS-1.0.10-bsd87c04aaa8f7000176ad354b1c|设备标示。 |
|Extension|String|80011474|座席分机号，一共8位 如果一个用户账号有多种设备，则多个设备用一个分机号，且同一时间只有一个设备可用。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|job-65700074013925376|在呼叫状态时的通话ID。 |
|OutboundScenario|Boolean|false|仅外呼。 |
|SignedSkillGroupIdList|List|\["skill-group@ccc-test"\]|签入的技能组ID列表。 |
|UserId|String|user-test@ccc-test|用户ID，格式为username@domain。 |
|UserState|String|READY|座席状态码。包括：

 -   OFFLINE（离线）
-   BREAK（小休）
-   READY（就绪，空闲）
-   DIALING（拨号）
-   RINGING（振铃）
-   TALKING（通话）
-   WORKING（话后处理） |
|WorkMode|String|ON\_SITE|工作模式。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|返回参数。 |
|RequestId|String|26A34338-5CD9-4C95-A7A6-5BDCE76C6B94|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=MakeCall
&Callee=13188888888
&DeviceId=ACC-YUNBS-1.0.10-bsd87c04aaa8f7000176ad354b1c
&InstanceId=ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>26A34338-5CD9-4C95-A7A6-5BDCE76C6B94</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Params>无</Params>
<Data>
    <UserContext>
        <Extension>80011474</Extension>
        <UserState>READY</UserState>
        <InstanceId>ccc-test</InstanceId>
        <UserId>user-test@ccc-test</UserId>
        <DeviceId>ACC-YUNBS-1.0.10-bsd87c04aaa8f7000176ad354b1c</DeviceId>
        <BreakCode>Warm-up</BreakCode>
        <OutboundScenario>false</OutboundScenario>
        <WorkMode>ON_SITE</WorkMode>
        <JobId>job-65700074013925376</JobId>
        <SignedSkillGroupIdList>["skill-group@ccc-test"]</SignedSkillGroupIdList>
    </UserContext>
    <CallContext>
        <InstanceId>ccc-test</InstanceId>
        <CallType>OUTBOUND</CallType>
        <JobId>job-65700074013925376</JobId>
        <ChannelContexts>
            <Destination>80011474</Destination>
            <ChannelState>NONE</ChannelState>
            <ReleaseInitiator>无</ReleaseInitiator>
            <CallType>OUTBOUND</CallType>
            <AssociatedData>无</AssociatedData>
            <ChannelId>ch:user:1318888888-&gt;80011474:1609225718294:job-65700074013925376</ChannelId>
            <Timestamp>1609225718295</Timestamp>
            <ReleaseReason>无</ReleaseReason>
            <Originator>13188888888</Originator>
            <ChannelFlags>[]</ChannelFlags>
            <UserId>user-test@ccc-test</UserId>
            <UserExtension>80011474</UserExtension>
            <JobId>job-65700074013925376</JobId>
        </ChannelContexts>
    </CallContext>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "26A34338-5CD9-4C95-A7A6-5BDCE76C6B94",
	"Message": "无",
	"HttpStatusCode": "200",
	"Params": "无",
	"Data": {
		"UserContext": {
			"Extension": "80011474",
			"UserState": "READY",
			"InstanceId": "ccc-test",
			"UserId": "user-test@ccc-test",
			"DeviceId": "ACC-YUNBS-1.0.10-bsd87c04aaa8f7000176ad354b1c",
			"BreakCode": "Warm-up",
			"OutboundScenario": "false",
			"WorkMode": "ON_SITE",
			"JobId": "job-65700074013925376",
			"SignedSkillGroupIdList": "[\"skill-group@ccc-test\"]"
		},
		"CallContext": {
			"InstanceId": "ccc-test",
			"CallType": "OUTBOUND",
			"JobId": "job-65700074013925376",
			"ChannelContexts": [{
				"Destination": "80011474",
				"ChannelState": "NONE",
				"ReleaseInitiator": "无",
				"CallType": "OUTBOUND",
				"AssociatedData": "无",
				"ChannelId": "ch:user:1318888888->80011474:1609225718294:job-65700074013925376",
				"Timestamp": "1609225718295",
				"ReleaseReason": "无",
				"Originator": "13188888888",
				"ChannelFlags": "[]",
				"UserId": "user-test@ccc-test",
				"UserExtension": "80011474",
				"JobId": "job-65700074013925376"
			}]
		}
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.UserId|The user %s does not exist in instance %s.|呼叫中心实例中不存在指定的用户。|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|UserBusy|The user %s you called was busy. Please try again later.|您呼叫的用户正忙，请稍后再试。|
|404|NotExists.Extension|No available extension number exists.|没有可分配的分机号。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

