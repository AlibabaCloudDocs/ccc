# ListHistoricalAgentReport

调用ListHistoricalAgentReport获取坐席历史数据报表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListHistoricalAgentReport&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListHistoricalAgentReport|系统规定参数。取值：ListHistoricalAgentReport。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|100|分页大小，范围1-100。 |
|AgentIdList|String|否|\["user-test@ccc-test", "user-test2@ccc-test"\]|坐席ID列表。 |
|StartTime|Long|否|1532448000000|获取的历史数据的起始时间，默认为当天的0时。 |
|StopTime|Long|否|1532707199000|获取的历史数据的终止时间，默认为当前时间。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of Items| |坐席报表列表。 |
|AgentId|String|user-test@ccc-test|座席ID，等同于userId。 |
|AgentName|String|云呼测试坐席|坐席姓名。 |
|Inbound|Struct| |呼入指标。 |
|AverageHoldTime|Float|0|平均通话保持时长，单位秒。 |
|AverageRingTime|Float|0|平均振铃时长，单位秒。 |
|AverageTalkTime|Float|0|平均通话时长，单位秒。 |
|AverageWorkTime|Float|0|平均话后处理时长，单位秒。 |
|CallsConsulted|Long|0|发起咨询的电话数量，如果一通电话中发起多次咨询，算一次。 |
|CallsHandled|Long|0|电话应答数。 |
|CallsHold|Long|0|被保持的电话数量。一通电话hold多次算一次，多次时间的和加起来算这次的保持时长。 |
|CallsOffered|Long|0|电话呼入数。 |
|CallsTransferred|Long|0|被转接的电话数量，包括咨询转和盲转。 |
|HandleRate|Float|0|应答率，单位%。CallsHandled / CallsQueued |
|MaxHoldTime|Long|0|最大通话保持时长，单位秒。 |
|MaxRingTime|Long|0|最大振铃时长，单位秒。 |
|MaxTalkTime|Long|0|最大通话时长，单位秒。 |
|MaxWorkTime|Long|0|最大话后处理时长，单位秒。 |
|SatisfactionIndex|Float|0|满意度指数，单位%。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalRingTime|Long|0|总振铃时长，单位秒。 |
|TotalTalkTime|Long|0|总通话时长，单位秒。 |
|TotalWorkTime|Long|0|总话后处理时长，单位秒。 |
|Outbound|Struct| |呼出指标。 |
|AnswerRate|Float|0|接通率，单位%。 |
|AverageDialingTime|Float|0|平均拨号时长，单位秒。 |
|AverageHoldTime|Float|0|平均通话保持时长，单位秒。 |
|AverageTalkTime|Float|0|平均通话时长，单位秒。 |
|AverageWorkTime|Float|0|平均话后处理时长，单位秒。 |
|CallsAnswered|Long|0|电话接通量。 |
|CallsDialed|Long|0|电话拨号量。 |
|CallsDialedSuccess|Long|0|电话拨号成功量。 |
|CallsHold|Long|0|通话保持的电话数量。一通电话hold多次算一次，多次hold时长的总和算本次通话的保持时长。 |
|MaxDialingTime|Long|0|最大拨号时长，单位秒。 |
|MaxHoldTime|Long|0|最大通话保持时长，单位秒。 |
|MaxTalkTime|Long|0|最大通话时长，单位秒。 |
|MaxWorkTime|Long|0|最大话后处理时长，单位秒。 |
|SatisfactionIndex|Float|0|满意度指数，单位%。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalDialingTime|Long|0|总拨号时长，单位秒。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalTalkTime|Long|0|总通话时长，单位秒。 |
|TotalWorkTime|Long|0|总话后处理时长，单位秒。 |
|Overall|Struct| |整体指标。 |
|AverageBreakTime|Float|0|平均小休时长，单位为秒。 |
|AverageReadyTime|Float|0|平均就绪时长，单位为秒。 |
|AverageTalkTime|Float|0|平均通话时长，单位秒。 |
|AverageWorkTime|Float|0|平均话后处理时长，单位秒。 |
|MaxBreakTime|Long|0|最大小休时长，单位为秒。 |
|MaxReadyTime|Long|0|最大就绪时长，单位为秒。 |
|MaxTalkTime|Long|0|最大通话时长，单位秒。 |
|MaxWorkTime|Long|0|最大话后处理时长，单位秒。 |
|OccupancyRate|Float|0|座席利用率，单位%。 |
|SatisfactionIndex|Float|0|满意度指数，单位%。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalBreakTime|Long|0|总小休时长，单位为秒。 |
|TotalCalls|Long|0|总电话接待量。包括应答的呼入电话和接通的呼出电话。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalLoggedInTime|Long|0|总登录时长，单位秒。 |
|TotalReadyTime|Long|0|总就绪时长，单位为秒。 |
|TotalTalkTime|Long|0|总通话时长，单位秒。 |
|TotalWorkTime|Long|0|总话后处理时长，单位秒。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|100|分页大小。 |
|TotalCount|Integer|10|总条目数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListHistoricalAgentReport
&AgentIdList=["ccc-user@ccc-test", "ccc-user2@ccc-test"]
&InstanceId=ccc-test
&PageNumber=1
&PageSize=100
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <TotalCount>10</TotalCount>
    <PageSize>100</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <AgentName>云呼测试坐席</AgentName>
        <AgentId>user-test@ccc-test</AgentId>
        <Inbound>
            <CallsConsulted>0</CallsConsulted>
            <TotalWorkTime>0</TotalWorkTime>
            <TotalHoldTime>0</TotalHoldTime>
            <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
            <AverageHoldTime>0</AverageHoldTime>
            <MaxRingTime>0</MaxRingTime>
            <CallsOffered>0</CallsOffered>
            <SatisfactionIndex>0</SatisfactionIndex>
            <CallsHold>0</CallsHold>
            <CallsHandled>0</CallsHandled>
            <TotalRingTime>0</TotalRingTime>
            <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
            <HandleRate>0</HandleRate>
            <TotalTalkTime>0</TotalTalkTime>
            <AverageRingTime>0</AverageRingTime>
            <CallsTransfered>0</CallsTransfered>
            <MaxTalkTime>0</MaxTalkTime>
            <AverageWorkTime>0</AverageWorkTime>
            <MaxWorkTime>0</MaxWorkTime>
            <MaxHoldTime>0</MaxHoldTime>
            <AverageTalkTime>0</AverageTalkTime>
        </Inbound>
        <Outbound>
            <TotalDialingTime>0</TotalDialingTime>
            <TotalWorkTime>0</TotalWorkTime>
            <TotalHoldTime>0</TotalHoldTime>
            <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
            <CallsDialedSuccess>0</CallsDialedSuccess>
            <AverageHoldTime>0</AverageHoldTime>
            <SatisfactionIndex>0</SatisfactionIndex>
            <CallsHold>0</CallsHold>
            <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
            <AverageDialingTime>0</AverageDialingTime>
            <CallsAnswered>0</CallsAnswered>
            <TotalTalkTime>0</TotalTalkTime>
            <CallsDialed>0</CallsDialed>
            <MaxDialingTime>0</MaxDialingTime>
            <MaxTalkTime>0</MaxTalkTime>
            <AverageWorkTime>0</AverageWorkTime>
            <MaxWorkTime>0</MaxWorkTime>
            <MaxHoldTime>0</MaxHoldTime>
            <AverageTalkTime>0</AverageTalkTime>
            <AnswerRate>0</AnswerRate>
        </Outbound>
        <Overall>
            <TotalReadyTime>0</TotalReadyTime>
            <TotalCalls>0</TotalCalls>
            <TotalBreakTime>0</TotalBreakTime>
            <TotalWorkTime>0</TotalWorkTime>
            <TotalHoldTime>0</TotalHoldTime>
            <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
            <SatisfactionIndex>0</SatisfactionIndex>
            <AverageBreakTime>0</AverageBreakTime>
            <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
            <TotalTalkTime>0</TotalTalkTime>
            <AverageReadyTime>0</AverageReadyTime>
            <TotalLoggedInTime>0</TotalLoggedInTime>
            <MaxTalkTime>0</MaxTalkTime>
            <MaxReadyTime>0</MaxReadyTime>
            <AverageWorkTime>0</AverageWorkTime>
            <MaxWorkTime>0</MaxWorkTime>
            <MaxBreakTime>0</MaxBreakTime>
            <OccupancyRate>0</OccupancyRate>
            <AverageTalkTime>0</AverageTalkTime>
        </Overall>
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
		"TotalCount": "10",
		"PageSize": "100",
		"PageNumber": "1",
		"List": [{
			"AgentName": "云呼测试坐席",
			"AgentId": "user-test@ccc-test",
			"Inbound": {
				"CallsConsulted": "0",
				"TotalWorkTime": "0",
				"TotalHoldTime": "0",
				"SatisfactionSurveysOffered": "0",
				"AverageHoldTime": "0",
				"MaxRingTime": "0",
				"CallsOffered": "0",
				"SatisfactionIndex": "0",
				"CallsHold": "0",
				"CallsHandled": "0",
				"TotalRingTime": "0",
				"SatisfactionSurveysResponded": "0",
				"HandleRate": "0",
				"TotalTalkTime": "0",
				"AverageRingTime": "0",
				"CallsTransfered": "0",
				"MaxTalkTime": "0",
				"AverageWorkTime": "0",
				"MaxWorkTime": "0",
				"MaxHoldTime": "0",
				"AverageTalkTime": "0"
			},
			"Outbound": {
				"TotalDialingTime": "0",
				"TotalWorkTime": "0",
				"TotalHoldTime": "0",
				"SatisfactionSurveysOffered": "0",
				"CallsDialedSuccess": "0",
				"AverageHoldTime": "0",
				"SatisfactionIndex": "0",
				"CallsHold": "0",
				"SatisfactionSurveysResponded": "0",
				"AverageDialingTime": "0",
				"CallsAnswered": "0",
				"TotalTalkTime": "0",
				"CallsDialed": "0",
				"MaxDialingTime": "0",
				"MaxTalkTime": "0",
				"AverageWorkTime": "0",
				"MaxWorkTime": "0",
				"MaxHoldTime": "0",
				"AverageTalkTime": "0",
				"AnswerRate": "0"
			},
			"Overall": {
				"TotalReadyTime": "0",
				"TotalCalls": "0",
				"TotalBreakTime": "0",
				"TotalWorkTime": "0",
				"TotalHoldTime": "0",
				"SatisfactionSurveysOffered": "0",
				"SatisfactionIndex": "0",
				"AverageBreakTime": "0",
				"SatisfactionSurveysResponded": "0",
				"TotalTalkTime": "0",
				"AverageReadyTime": "0",
				"TotalLoggedInTime": "0",
				"MaxTalkTime": "0",
				"MaxReadyTime": "0",
				"AverageWorkTime": "0",
				"MaxWorkTime": "0",
				"MaxBreakTime": "0",
				"OccupancyRate": "0",
				"AverageTalkTime": "0"
			}
		}]
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

