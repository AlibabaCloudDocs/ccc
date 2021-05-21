# ListIntervalAgentReport

调用ListIntervalAgentReport获取坐席的分段汇总报表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListIntervalAgentReport&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListIntervalAgentReport|系统规定参数。取值：ListIntervalAgentReport。 |
|AgentId|String|是|user-test@ccc-test|坐席ID，也叫呼叫中心UserId。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|StartTime|Long|否|1620230400000|开始时间戳，默认是当天开始时间，最早为当前时间往前180天。 |
|EndTime|Long|否|1620316799000|截止时间戳，默认是当前时间，如果Interval为Daily，StartTime和EndTime最大间隔是180天。如果Interval为Hourly，最大间隔时间为10天。 |
|Interval|String|否|Hourly|分段汇总类型：Daily（按天汇总）/ Hourly（按小时汇总）默认是Daily。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Array of Data| |数据。 |
|Inbound|Struct| |呼入指标。 |
|AverageRingTime|Float|0|平均振铃时长，单位秒。 |
|AverageTalkTime|Float|0|平均通话时长，单位秒。 |
|AverageWorkTime|Float|0|平均话后处理时长，单位秒。 |
|CallsConsulted|Long|0|发起咨询的电话数量，如果一通电话中发起多次咨询，算一次。 |
|CallsHandled|Long|0|座席应答电话数。一通电话分给多个座席，算一通。如果电话出现转接，但是转接的时候电话挂断了，此时不算入CallsAbandoned。 |
|CallsHold|Long|0|通话保持的电话数量。一通电话hold多次算一次，多次hold时长的总和算本次通话的保持时长。 |
|CallsOffered|Long|0|电话呼入数。 |
|CallsTransferred|Long|0|被转接的电话数量，包括咨询转和盲转。 |
|HandleRate|Float|0|应答率，单位%，等于 座席应答电话数 / 进入队列的电话数。 |
|MaxRingTime|Long|0|最大振铃时长，单位秒。 |
|MaxTalkTime|Long|0|最大通话时长，单位秒。 |
|MaxWorkTime|Long|0|最大话后处理时长，单位秒。 |
|SatisfactionIndex|Float|0|满意度指数，即满意度平均值。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalRingTime|Long|0|总振铃时长，单位秒。 |
|TotalTalkTime|Long|0|总通话时长，单位秒。 |
|TotalWorkTime|Long|0|总话后处理时长，单位秒。 |
|Outbound|Struct| |呼出指标。 |
|AnswerRate|Float|0|接通率，单位%。 |
|AverageDialingTime|Float|30|平均拨号时长，单位秒。 |
|AverageTalkTime|Float|0|平均通话时长，单位秒。 |
|AverageWorkTime|Float|1|平均话后处理时长，单位秒。 |
|CallsAnswered|Long|0|电话接通量。 |
|CallsDialed|Long|5|电话拨号量。 |
|MaxDialingTime|Long|60|最大拨号时长，单位秒。 |
|MaxTalkTime|Long|0|最大通话时长，单位秒。 |
|MaxWorkTime|Long|2|最大话后处理时长，单位秒。 |
|SatisfactionIndex|Float|0|满意度指数，即满意度平均值。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalDialingTime|Long|148|总拨号时长，单位秒。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalTalkTime|Long|0|总通话时长，单位秒。 |
|TotalWorkTime|Long|4|总话后处理时长，单位秒。 |
|Overall|Struct| |整体指标。 |
|AverageBreakTime|Float|0|平均小休时长，单位秒。 |
|AverageReadyTime|Float|0|平均就绪时长，单位秒。 |
|AverageTalkTime|Float|0|平均通话时长，单位秒。 |
|AverageWorkTime|Float|1|平均话后处理时长，单位秒。 |
|FirstCheckInTime|Long|0|入参Interval为Daily才有值，当天的首次上线时间。 |
|LastCheckoutTime|Long|0|入参Interval为Daily才有值，当天的最后下线时间。 |
|MaxBreakTime|Long|1|最大小休时长，单位秒。 |
|MaxReadyTime|Long|435|最大就绪时长，单位秒。 |
|MaxTalkTime|Long|0|最大通话时长，单位秒。 |
|MaxWorkTime|Long|2|最大话后处理时长，单位秒。 |
|OccupancyRate|Float|0|座席利用率，单位%。 |
|SatisfactionIndex|Float|0|满意度指数，即满意度平均值。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalBreakTime|Long|1|总小休时长，单位为秒。 |
|TotalCalls|Long|5|总电话接待量。包括应答的呼入电话和接通的呼出电话。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalLoggedInTime|Long|914|总登录时长，单位秒。 |
|TotalReadyTime|Long|763|总就绪时长，单位为秒。 |
|TotalTalkTime|Long|0|总通话时长，单位秒。 |
|TotalWorkTime|Long|4|总话后处理时长，单位秒。 |
|StatsTime|Long|1620291600000|时间戳，时间段开始时间。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|943D8EF3-3321-471F-A104-51C96FCA94D6|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListIntervalAgentReport
&AgentId=user-test@ccc-test
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
    <StatsTime>1620291600000</StatsTime>
    <Inbound>
        <CallsConsulted>0</CallsConsulted>
        <TotalWorkTime>0</TotalWorkTime>
        <TotalHoldTime>0</TotalHoldTime>
        <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
        <MaxRingTime>0</MaxRingTime>
        <CallsOffered>0</CallsOffered>
        <SatisfactionIndex>0</SatisfactionIndex>
        <CallsHold>0</CallsHold>
        <CallsHandled>0</CallsHandled>
        <TotalRingTime>0</TotalRingTime>
        <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
        <HandleRate>0</HandleRate>
        <CallsTransferred>0</CallsTransferred>
        <TotalTalkTime>0</TotalTalkTime>
        <AverageRingTime>0</AverageRingTime>
        <MaxTalkTime>0</MaxTalkTime>
        <AverageWorkTime>0</AverageWorkTime>
        <MaxWorkTime>0</MaxWorkTime>
        <AverageTalkTime>0</AverageTalkTime>
    </Inbound>
    <Outbound>
        <TotalDialingTime>148</TotalDialingTime>
        <TotalWorkTime>4</TotalWorkTime>
        <TotalHoldTime>0</TotalHoldTime>
        <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
        <SatisfactionIndex>0</SatisfactionIndex>
        <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
        <AverageDialingTime>30</AverageDialingTime>
        <CallsAnswered>0</CallsAnswered>
        <TotalTalkTime>0</TotalTalkTime>
        <CallsDialed>5</CallsDialed>
        <MaxDialingTime>60</MaxDialingTime>
        <MaxTalkTime>0</MaxTalkTime>
        <AverageWorkTime>1</AverageWorkTime>
        <MaxWorkTime>2</MaxWorkTime>
        <AverageTalkTime>0</AverageTalkTime>
        <AnswerRate>0</AnswerRate>
    </Outbound>
    <Overall>
        <TotalReadyTime>763</TotalReadyTime>
        <TotalCalls>5</TotalCalls>
        <TotalBreakTime>1</TotalBreakTime>
        <LastCheckoutTime>0</LastCheckoutTime>
        <TotalWorkTime>4</TotalWorkTime>
        <TotalHoldTime>0</TotalHoldTime>
        <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
        <SatisfactionIndex>0</SatisfactionIndex>
        <AverageBreakTime>0</AverageBreakTime>
        <FirstCheckInTime>0</FirstCheckInTime>
        <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
        <TotalTalkTime>0</TotalTalkTime>
        <AverageReadyTime>0</AverageReadyTime>
        <TotalLoggedInTime>914</TotalLoggedInTime>
        <MaxTalkTime>0</MaxTalkTime>
        <MaxReadyTime>435</MaxReadyTime>
        <AverageWorkTime>1</AverageWorkTime>
        <MaxWorkTime>2</MaxWorkTime>
        <MaxBreakTime>1</MaxBreakTime>
        <OccupancyRate>0</OccupancyRate>
        <AverageTalkTime>0</AverageTalkTime>
    </Overall>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "943D8EF3-3321-471F-A104-51C96FCA94D6",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": [{
		"StatsTime": "1620291600000",
		"Inbound": {
			"CallsConsulted": "0",
			"TotalWorkTime": "0",
			"TotalHoldTime": "0",
			"SatisfactionSurveysOffered": "0",
			"MaxRingTime": "0",
			"CallsOffered": "0",
			"SatisfactionIndex": "0",
			"CallsHold": "0",
			"CallsHandled": "0",
			"TotalRingTime": "0",
			"SatisfactionSurveysResponded": "0",
			"HandleRate": "0",
			"CallsTransferred": "0",
			"TotalTalkTime": "0",
			"AverageRingTime": "0",
			"MaxTalkTime": "0",
			"AverageWorkTime": "0",
			"MaxWorkTime": "0",
			"AverageTalkTime": "0"
		},
		"Outbound": {
			"TotalDialingTime": "148",
			"TotalWorkTime": "4",
			"TotalHoldTime": "0",
			"SatisfactionSurveysOffered": "0",
			"SatisfactionIndex": "0",
			"SatisfactionSurveysResponded": "0",
			"AverageDialingTime": "30",
			"CallsAnswered": "0",
			"TotalTalkTime": "0",
			"CallsDialed": "5",
			"MaxDialingTime": "60",
			"MaxTalkTime": "0",
			"AverageWorkTime": "1",
			"MaxWorkTime": "2",
			"AverageTalkTime": "0",
			"AnswerRate": "0"
		},
		"Overall": {
			"TotalReadyTime": "763",
			"TotalCalls": "5",
			"TotalBreakTime": "1",
			"LastCheckoutTime": "0",
			"TotalWorkTime": "4",
			"TotalHoldTime": "0",
			"SatisfactionSurveysOffered": "0",
			"SatisfactionIndex": "0",
			"AverageBreakTime": "0",
			"FirstCheckInTime": "0",
			"SatisfactionSurveysResponded": "0",
			"TotalTalkTime": "0",
			"AverageReadyTime": "0",
			"TotalLoggedInTime": "914",
			"MaxTalkTime": "0",
			"MaxReadyTime": "435",
			"AverageWorkTime": "1",
			"MaxWorkTime": "2",
			"MaxBreakTime": "1",
			"OccupancyRate": "0",
			"AverageTalkTime": "0"
		}
	}],
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Parameter.Format|The format of parameter %s is invalid. %s|该参数的格式不合法。|
|500|InternalService.Common|An internal service error occurred. %s|内部服务错误。|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

