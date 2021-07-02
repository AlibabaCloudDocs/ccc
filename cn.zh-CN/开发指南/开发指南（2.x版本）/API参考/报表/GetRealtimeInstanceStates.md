# GetRealtimeInstanceStates

调用GetRealtimeInstanceStates获取呼叫中心实例的实时状态。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=GetRealtimeInstanceStates&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetRealtimeInstanceStates|系统规定参数。取值：GetRealtimeInstanceStates。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|BreakingAgents|Long|0|处于小休状态的坐席数量。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|InteractiveCalls|Long|0|IVR中交互的电话个数。 |
|LoggedInAgents|Long|0|在线坐席数量（包括就绪，小休，通话等非下线状态的坐席）。 |
|LongestWaitingTime|Long|0|当前排队来电的最大等待时长。 |
|ReadyAgents|Long|0|处于就绪状态的坐席数量。 |
|TalkingAgents|Long|0|处于通话状态的坐席数量。 |
|TotalAgents|Long|0|总坐席数。 |
|WaitingCalls|Long|0|当前排队来电的个数。 |
|WorkingAgents|Long|0|处于话后处理状态的坐席数量。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|943D8EF3-3321-471F-A104-51C96FCA94D6|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetRealtimeInstanceStates
&InstanceId=ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>943D8EF3-3321-471F-A104-51C96FCA94D6</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <BreakingAgents>0</BreakingAgents>
    <TalkingAgents>0</TalkingAgents>
    <InstanceId>ccc-test</InstanceId>
    <LoggedInAgents>0</LoggedInAgents>
    <ReadyAgents>0</ReadyAgents>
    <WaitingCalls>0</WaitingCalls>
    <LongestCall>0</LongestCall>
    <TotalAgents>0</TotalAgents>
    <InteractiveCalls>0</InteractiveCalls>
    <WorkingAgents>0</WorkingAgents>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "943D8EF3-3321-471F-A104-51C96FCA94D6",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": {
		"BreakingAgents": "0",
		"TalkingAgents": "0",
		"InstanceId": "ccc-test",
		"LoggedInAgents": "0",
		"ReadyAgents": "0",
		"WaitingCalls": "0",
		"LongestCall": "0",
		"TotalAgents": "0",
		"InteractiveCalls": "0",
		"WorkingAgents": "0"
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

