# ListRealtimeAgentStates

调用接口ListRealtimeAgentStates获取指定坐席当前状态。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListRealtimeAgentStates&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListRealtimeAgentStates|系统规定参数。取值：ListRealtimeAgentStates。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|10|分页大小，范围1-100。 |
|SkillGroupId|String|是|skg-default@ccc-test|技能组ID。 |
|AgentIdList|String|否|\["user-test@ccc-test", "user-test2@ccc-test"\]|坐席ID列表，最多20个。 |
|StateList|String|否|\["ACW", "Dialing"\]|想要查询的状态列表，为空查询全部。取值：

 -   ACW 话后处理
-   Ringing 振铃
-   Break 小休
-   Dialing 拨号
-   Talking 通话
-   Ready 空闲
-   Offline 离线 |
|AgentName|String|否|云呼测试坐席|坐席名字，模糊匹配。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of AgentState| |坐席状态列表。 |
|AgentId|String|user-test@ccc-test|坐席ID。 |
|AgentName|String|云呼测试坐席|坐席姓名。 |
|CounterParty|String|user-admin@ccc-test|监听场景指监听和被监听的对方。 |
|Extension|String|80317391|坐席分机号。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|SkillGroupIdList|List|\["skg-default@ccc-test"\]|签入的技能组ID列表。 |
|State|String|ACW|坐席状态。 |
|StateCode|String|Monitored|针对监听场景，

 -   监听状态：State=Talking，StateCode=Monitoring。
-   被监听状态：State=Talking，StateCode=Monitored。 |
|StateTime|Long|8|状态持续时长，单位秒。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|10|分页大小。 |
|TotalCount|Integer|1|总条目数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListRealtimeAgentStates
&InstanceId=ccc-test
&PageNumber=1
&PageSize=10
&SkillGroupId=skg-default@ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <TotalCount>1</TotalCount>
    <PageSize>10</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <Extension>80317391</Extension>
        <CounterParty>user-admin@ccc-test</CounterParty>
        <StateTime>8</StateTime>
        <InstanceId>ccc-test</InstanceId>
        <State>ACW</State>
        <StateCode>Monitored</StateCode>
        <AgentName>云呼测试坐席</AgentName>
        <AgentId>user-test@ccc-test</AgentId>
    </List>
    <List>
        <SkillGroupIdList>["skg-default@ccc-test"]</SkillGroupIdList>
    </List>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": {
		"TotalCount": "1",
		"PageSize": "10",
		"PageNumber": "1",
		"List": [{
			"Extension": "80317391",
			"CounterParty": "user-admin@ccc-test",
			"StateTime": "8",
			"InstanceId": "ccc-test",
			"State": "ACW",
			"StateCode": "Monitored",
			"AgentName": "云呼测试坐席",
			"AgentId": "user-test@ccc-test"
		}, {
			"SkillGroupIdList": "[\"skg-default@ccc-test\"]"
		}]
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalService.Common|An internal service error occurred. %s|内部服务错误。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

