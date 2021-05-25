# ListIvrTrackingDetails

调用ListIvrTrackingDetails获取IVR轨迹。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListIvrTrackingDetails&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListIvrTrackingDetails|系统规定参数。取值：ListIvrTrackingDetails。 |
|ContactId|String|是|job-109634426711871319|通话ID。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|10|分页大小，范围1-100。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of IvrTracking| |IVR轨迹列表。 |
|Callee|String|053xxxx3128|被叫号码。 |
|Caller|String|133xxxx2315|主叫号码。 |
|ChannelId|String|65cp2c15-92ac-4e67-98b2-073a3c541c5d|通道ID。 |
|ChannelVariables|String|A=B;C=D|随路数据。 |
|ContactId|String|job-109634426711871319|通话ID。 |
|EnterTime|Long|1621910542876|进入该IVR节点的时间。 |
|FlowId|String|abc99462-1058-47d0-a114-f145ea7444ff|联系流ID。 |
|FlowName|String|测试IVR|联系流名称。 |
|Instance|String|ccc-test|呼叫中心实例ID。 |
|LeaveTime|Long|1621910545105|离开该IVR节点的时间。 |
|NodeExitCode|String|Success|节点的状态码。 |
|NodeId|String|e0bc19a3|节点ID。 |
|NodeName|String|放音|节点名称。 |
|NodeProperties|Map|\{"say":"您好。"\}|节点的属性集合。 |
|NodeType|String|PLAY\_OR\_SAY|节点类型。 |
|NodeVariables|Map|\{"digits":"2"\}|节点变量。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|10|分页大小。 |
|TotalCount|Integer|4|总条目数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|D2RB671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListIvrTrackingDetails
&ContactId=job-109634426711871319
&InstanceId=ccc-test
&PageNumber=1
&PageSize=10
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>D2RB671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <TotalCount>4</TotalCount>
    <PageSize>10</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <Callee>053xxxx3128</Callee>
        <NodeName>放音</NodeName>
        <Instance>ccc-test</Instance>
        <EnterTime>1621910542876</EnterTime>
        <NodeExitCode>Success</NodeExitCode>
        <ContactId>job-109634426711871319</ContactId>
        <ChannelId>65cp2c15-92ac-4e67-98b2-073a3c541c5d</ChannelId>
        <ChannelVariables>A=B;C=D</ChannelVariables>
        <FlowId>abc99462-1058-47d0-a114-f145ea7444ff</FlowId>
        <LeaveTime>1621910545105</LeaveTime>
        <NodeProperties>{"say":"您好。"}</NodeProperties>
        <Caller>133xxxx2315</Caller>
        <FlowName>测试IVR</FlowName>
        <NodeType>PLAY_OR_SAY</NodeType>
        <NodeId>e0bc19a3</NodeId>
        <NodeVariables>{"digits":"2"}</NodeVariables>
    </List>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "D2RB671A-3E24-4A04-81E6-6C4F5B39DF75",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": {
		"TotalCount": "4",
		"PageSize": "10",
		"PageNumber": "1",
		"List": [{
			"Callee": "053xxxx3128",
			"NodeName": "放音",
			"Instance": "ccc-test",
			"EnterTime": "1621910542876",
			"NodeExitCode": "Success",
			"ContactId": "job-109634426711871319",
			"ChannelId": "65cp2c15-92ac-4e67-98b2-073a3c541c5d",
			"ChannelVariables": "A=B;C=D",
			"FlowId": "abc99462-1058-47d0-a114-f145ea7444ff",
			"LeaveTime": "1621910545105",
			"NodeProperties": "{\"say\":\"您好。\"}",
			"Caller": "133xxxx2315",
			"FlowName": "测试IVR",
			"NodeType": "PLAY_OR_SAY",
			"NodeId": "e0bc19a3",
			"NodeVariables": "{\"digits\":\"2\"}"
		}]
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalService.Common|An internal service error occurred. %s|内部服务错误。|
|400|Parameter.Format|The format of parameter %s is invalid. %s|该参数的格式不合法。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

