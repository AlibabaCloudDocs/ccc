# MuteCall

调用接口MuteCall使得通话静音。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=MuteCall&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|MuteCall|系统规定参数。取值：MuteCall。 |
|DeviceId|String|是|ACC-YUNBS-1.0.10-bs736efb521810000176aef6e955|座席端提供的唯一ID，用来表示一个座席工作台，一个座席可以有多个不同类型的座席台，比如浏览器，iOS, Android等， 但是在同一时间，只能有一个生效。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|JobId|String|是|job-65815360847228928|话务ID。 |
|UserId|String|是|user-test@ccc-test|用户ID，格式为username@domain。 |
|ChannelId|String|否|ch:user:13188888888-\>80011474:1609253204816:job-65815360847228928|待静音的通道ID，如果此参数为空，则表示操作自己所在的通道。 |

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
|ChannelId|String|ch:user:13188888888-\>80011474:1609253204816:job-65815360847228928"|通道ID。 |
|ChannelState|String|ANSWERED|状态。 |
|Destination|String|80011474|接收方。 |
|Index|Integer|1|记录这个Channel在通话过程中创建的顺序。 |
|JobId|String|job-65815360847228928|话务ID。 |
|Originator|String|13188888888|发起方。 |
|ReleaseInitiator|String|无|挂断方。 |
|ReleaseReason|String|无|挂断原因。 |
|Timestamp|Long|1609253212511|状态数据上次变更时间戳。 |
|UserExtension|String|80011474|座席是否发起方。 |
|UserId|String|user-test@ccc-test|该Channel的用户ID，如果是客户通道，则userId为空。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|job-65815360847228928|话务ID。 |
|UserContext|Struct| |用户上下文环境。 |
|BreakCode|String|Warm-up|小休状态码。 |
|DeviceId|String|ACC-YUNBS-1.0.10-bs736efb521810000176aef6e955|设备标示。 |
|Extension|String|80011474|座席分机号，一共8位 如果一个用户账号有多种设备，则多个设备用一个分机号，且同一时间只有一个设备可用。 |
|Heartbeat|Long|1609253205896|上次操作时间。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|job-65815360847228928|在呼叫状态时的通话ID。 |
|Mobile|String|13900000001|座席手机号码，场外座席情况下通过此号码联系座席。 |
|OutboundScenario|Boolean|false|仅外呼。 |
|Reserved|Long|1609253204811|座席处于预定状态，说明马上有电话给TA. 该参数记录收到预定请求的时间。 |
|SignedSkillGroupIdList|List|\["skill-group@ccc-test"\]|签入的技能组ID列表。 |
|UserId|String|user-test@ccc-test|用户ID，格式为username@domain。 |
|UserState|String|TALKING|座席状态码。 |
|WorkMode|String|ON\_SITE|工作模式。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|返回参数。 |
|RequestId|String|A275B008-A25B-494D-AB53-93CE253815B6|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=MuteCall
&DeviceId=ACC-YUNBS-1.0.10-bs736efb521810000176aef6e955
&InstanceId=ccc-test
&JobId=job-65815360847228928
&UserId=user-test@ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>A275B008-A25B-494D-AB53-93CE253815B6</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Params>无</Params>
<Data>
    <UserContext>
        <UserState>TALKING</UserState>
        <InstanceId>ccc-test</InstanceId>
        <DeviceId>ACC-YUNBS-1.0.10-bs736efb521810000176aef6e955</DeviceId>
        <BreakCode>Warm-up</BreakCode>
        <OutboundScenario>false</OutboundScenario>
        <Mobile>13900000001</Mobile>
        <SignedSkillGroupIdList>["skill-group@ccc-test"]</SignedSkillGroupIdList>
        <Extension>80011474</Extension>
        <UserId>user-test@ccc-test</UserId>
        <Heartbeat>1609253205896</Heartbeat>
        <WorkMode>ON_SITE</WorkMode>
        <JobId>job-65815360847228928</JobId>
        <Reserved>1609253204811</Reserved>
    </UserContext>
    <CallContext>
        <InstanceId>ccc-test</InstanceId>
        <CallType>OUTBOUND</CallType>
        <JobId>job-65815360847228928</JobId>
        <ChannelContexts>
            <Destination>80011474</Destination>
            <ChannelState>ANSWERED</ChannelState>
            <ReleaseInitiator>无</ReleaseInitiator>
            <CallType>OUTBOUND</CallType>
            <Index>1</Index>
            <AssociatedData>无</AssociatedData>
            <ChannelId>ch:user:13188888888-&gt;80011474:1609253204816:job-65815360847228928"</ChannelId>
            <Timestamp>1609253212511</Timestamp>
            <ReleaseReason>无</ReleaseReason>
            <Originator>13188888888</Originator>
            <ChannelFlags>[]</ChannelFlags>
            <UserId>user-test@ccc-test</UserId>
            <UserExtension>80011474</UserExtension>
            <JobId>job-65815360847228928</JobId>
        </ChannelContexts>
    </CallContext>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "A275B008-A25B-494D-AB53-93CE253815B6",
	"Message": "无",
	"HttpStatusCode": "200",
	"Params": "无",
	"Data": {
		"UserContext": {
			"UserState": "TALKING",
			"InstanceId": "ccc-test",
			"DeviceId": "ACC-YUNBS-1.0.10-bs736efb521810000176aef6e955",
			"BreakCode": "Warm-up",
			"OutboundScenario": "false",
			"Mobile": "13900000001",
			"SignedSkillGroupIdList": "[\"skill-group@ccc-test\"]",
			"Extension": "80011474",
			"UserId": "user-test@ccc-test",
			"Heartbeat": "1609253205896",
			"WorkMode": "ON_SITE",
			"JobId": "job-65815360847228928",
			"Reserved": "1609253204811"
		},
		"CallContext": {
			"InstanceId": "ccc-test",
			"CallType": "OUTBOUND",
			"JobId": "job-65815360847228928",
			"ChannelContexts": [{
				"Destination": "80011474",
				"ChannelState": "ANSWERED",
				"ReleaseInitiator": "无",
				"CallType": "OUTBOUND",
				"Index": "1",
				"AssociatedData": "无",
				"ChannelId": "ch:user:13188888888->80011474:1609253204816:job-65815360847228928\"",
				"Timestamp": "1609253212511",
				"ReleaseReason": "无",
				"Originator": "13188888888",
				"ChannelFlags": "[]",
				"UserId": "user-test@ccc-test",
				"UserExtension": "80011474",
				"JobId": "job-65815360847228928"
			}]
		}
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.ChannelId|The specified channel %s does not exist in call %s.|通话中不存在指定的Channel信息。|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|404|NotExists.JobId|The call %s does not exist.|指定的通话信息不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

