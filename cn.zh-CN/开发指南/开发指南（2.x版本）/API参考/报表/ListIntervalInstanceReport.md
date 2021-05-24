# ListIntervalInstanceReport

调用ListIntervalInstanceReport获取呼叫中心实例的分段汇总报表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListIntervalInstanceReport&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListIntervalInstanceReport|系统规定参数。取值：ListIntervalInstanceReport。 |
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
|AbandonedRate|Float|0|放弃率，单位是%，等于（队列放弃量

 -   振铃放弃量） / 进入队列的电话数。 |
|AverageAbandonTime|Float|0|平均放弃时长，单位秒。 |
|AverageAbandonedInIVRTime|Float|0|平均IVR放弃时长，单位秒。 |
|AverageAbandonedInQueueTime|Float|0|平均排队放弃时长，单位秒。 |
|AverageAbandonedInRingTime|Float|0|平均响铃放弃时长，单位秒。 |
|AverageHoldTime|Float|0|平均通话保持时长，单位秒。 |
|AverageRingTime|Float|5|平均振铃时长，单位秒。 |
|AverageTalkTime|Float|64|平均通话时长，单位秒。 |
|AverageWaitTime|Float|5|平均等待时长，平均每通电话的坐席接起时等待时长。 |
|AverageWorkTime|Float|13|平均话后处理时长，单位秒。 |
|CallsAbandoned|Long|0|放弃量。 |
|CallsAbandonedInIVR|Long|0|IVR放弃量，即电话进入IVR流程之后在IVR环节放弃。 |
|CallsAbandonedInQueue|Long|0|队列放弃量，即电话进入技能组之后在排队环节放弃的数量。 |
|CallsAbandonedInRinging|Long|0|振铃放弃量。 |
|CallsConsulted|Long|0|发起咨询的电话数量，如果一通电话中发起多次咨询，算一次。 |
|CallsHandled|Long|7|座席应答电话数。一通电话分给多个座席，算一通。如果电话出现转接，但是转接的时候电话挂断了，此时不算入CallsAbandoned。 |
|CallsHold|Long|0|通话保持的电话数量。一通电话hold多次算一次，多次hold时长的总和算本次通话的保持时长。 |
|CallsOffered|Long|7|电话呼入数。 |
|CallsQueued|Long|7|进入队列的电话数，如果一次呼入多次进队列，算一通。 |
|CallsRinged|Long|7|座席振铃的电话数，一通电话分给多个座席，算一通。 |
|CallsTransferred|Long|0|被转接的电话数量，包括咨询转和盲转。 |
|HandleRate|Float|1|应答率，单位%，等于 座席应答电话数 / 进入队列的电话数。 |
|MaxAbandonTime|Long|0|最大放弃时长，单位秒。 |
|MaxAbandonedInIVRTime|Long|0|最大IVR放弃时长，单位秒。 |
|MaxAbandonedInQueueTime|Long|0|最大排队放弃时长，单位秒。 |
|MaxAbandonedInRingTime|Long|0|最大响铃放弃时长，单位秒。 |
|MaxHoldTime|Long|0|最大通话保持时长，单位秒。 |
|MaxRingTime|Long|12|最大振铃时长，单位秒。 |
|MaxTalkTime|Long|219|最大通话时长，单位秒。 |
|MaxWaitTime|Long|13|最大等待时长，单位秒。 |
|MaxWorkTime|Long|17|最大话后处理时长，单位秒。 |
|SatisfactionIndex|Float|0|满意度指数，即满意度平均值。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|ServiceLevel20|Float|1|20S服务水平，单位%。电话从开始排队到接听时间少于20秒的电话数量/CallsQueued。 |
|TotalAbandonTime|Long|0|总放弃时长，单位秒。 |
|TotalAbandonedInIVRTime|Long|0|总IVR放弃时长，单位秒。 |
|TotalAbandonedInQueueTime|Long|0|总排队放弃时长，单位秒。 |
|TotalAbandonedInRingTime|Long|0|总振铃放弃时长，单位秒。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalRingTime|Long|32|总振铃时长，单位秒。 |
|TotalTalkTime|Long|447|总通话时长，单位秒。 |
|TotalWaitTime|Long|34|总等待时长，单位秒。 |
|TotalWorkTime|Long|85|总话后处理时长，单位秒。 |
|Outbound|Struct| |呼出指标。 |
|AnswerRate|Float|0|接通率，单位%。 |
|AverageDialingTime|Float|0|平均拨号时长，单位秒 |
|AverageTalkTime|Float|0|平均通话时长，单位秒。 |
|AverageWorkTime|Float|0|平均话后处理时长，单位秒。 |
|CallsAnswered|Long|0|电话接通量。 |
|CallsDialed|Long|0|电话拨号量。 |
|CallsDialedSuccess|Long|0|电话拨号成功量。 |
|MaxDialingTime|Long|0|最大拨号时长，单位秒。 |
|MaxTalkTime|Long|0|最大通话时长，单位秒。 |
|MaxWorkTime|Long|0|最大话后处理时长，单位秒。 |
|SatisfactionIndex|Float|0|满意度指数，即满意度平均值。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalDialingTime|Long|0|总拨号时长，单位秒。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalTalkTime|Long|0|总通话时长，单位秒。 |
|TotalWorkTime|Long|0|总话后处理时长，单位秒。 |
|Overall|Struct| |整体指标。 |
|AverageBreakTime|Float|0|平均小休时长，单位秒。 |
|AverageHoldTime|Float|0|平均通话保持时长，单位秒。 |
|AverageReadyTime|Float|0|平均就绪时长，单位秒。 |
|AverageTalkTime|Float|0|平均通话时长，单位秒。 |
|AverageWorkTime|Float|0|平均话后处理时长，单位秒。 |
|MaxBreakTime|Long|0|最大小休时长，单位秒。 |
|MaxHoldTime|Long|0|最大通话保持时长，单位秒。 |
|MaxReadyTime|Long|0|最大就绪时长，单位秒。 |
|MaxTalkTime|Long|0|最大通话时长，单位秒。 |
|MaxWorkTime|Long|0|最大话后处理时长，单位秒。 |
|OccupancyRate|Float|0|座席利用率，单位%。 |
|SatisfactionIndex|Float|0|满意度指数，即满意度平均值。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalBreakTime|Long|0|总小休时长，单位为秒。 |
|TotalCalls|Long|0|总电话接待量。包括应答的呼入电话和接通的呼出电话。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalLoggedInTime|Long|0|总登录时长，单位秒。 |
|TotalReadyTime|Long|0|总就绪时长，单位为秒。 |
|TotalTalkTime|Long|0|总通话时长，单位秒。 |
|TotalWorkTime|Long|0|总话后处理时长，单位秒。 |
|StatsTime|Long|1620291600000|时间戳，时间段开始时间。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|943D8EF3-3321-471F-A104-51C96FCA94D6|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListIntervalInstanceReport
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
        <ServiceLevel20>1</ServiceLevel20>
        <CallsAbandonedInQueue>0</CallsAbandonedInQueue>
        <TotalWorkTime>85</TotalWorkTime>
        <TotalHoldTime>0</TotalHoldTime>
        <CallsRinged>7</CallsRinged>
        <MaxAbandonedInIVRTime>0</MaxAbandonedInIVRTime>
        <AverageHoldTime>0</AverageHoldTime>
        <MaxRingTime>12</MaxRingTime>
        <CallsOffered>7</CallsOffered>
        <CallsAbandoned>0</CallsAbandoned>
        <SatisfactionIndex>0</SatisfactionIndex>
        <CallsHold>0</CallsHold>
        <MaxAbandonedInRingTime>0</MaxAbandonedInRingTime>
        <TotalRingTime>32</TotalRingTime>
        <HandleRate>1</HandleRate>
        <TotalAbandonedInIVRTime>0</TotalAbandonedInIVRTime>
        <CallsAbandonedInRinging>0</CallsAbandonedInRinging>
        <AverageAbandonedInQueueTime>0</AverageAbandonedInQueueTime>
        <TotalTalkTime>447</TotalTalkTime>
        <AverageWaitTime>5</AverageWaitTime>
        <TotalAbandonedInRingTime>0</TotalAbandonedInRingTime>
        <CallsQueued>7</CallsQueued>
        <MaxTalkTime>219</MaxTalkTime>
        <AverageAbandonedInIVRTime>0</AverageAbandonedInIVRTime>
        <TotalAbandonTime>0</TotalAbandonTime>
        <MaxHoldTime>0</MaxHoldTime>
        <AverageTalkTime>64</AverageTalkTime>
        <CallsAbandonedInIVR>0</CallsAbandonedInIVR>
        <CallsConsulted>0</CallsConsulted>
        <MaxAbandonedInQueueTime>0</MaxAbandonedInQueueTime>
        <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
        <CallsHandled>7</CallsHandled>
        <MaxWaitTime>13</MaxWaitTime>
        <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
        <CallsTransferred>0</CallsTransferred>
        <MaxAbandonTime>0</MaxAbandonTime>
        <AverageRingTime>5</AverageRingTime>
        <TotalWaitTime>34</TotalWaitTime>
        <AverageAbandonTime>0</AverageAbandonTime>
        <AverageAbandonedInRingTime>0</AverageAbandonedInRingTime>
        <TotalAbandonedInQueueTime>0</TotalAbandonedInQueueTime>
        <AverageWorkTime>13</AverageWorkTime>
        <AbandonedRate>0</AbandonedRate>
        <MaxWorkTime>17</MaxWorkTime>
    </Inbound>
    <Outbound>
        <TotalDialingTime>0</TotalDialingTime>
        <TotalWorkTime>0</TotalWorkTime>
        <TotalHoldTime>0</TotalHoldTime>
        <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
        <CallsDialedSuccess>0</CallsDialedSuccess>
        <SatisfactionIndex>0</SatisfactionIndex>
        <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
        <AverageDialingTime>0</AverageDialingTime>
        <CallsAnswered>0</CallsAnswered>
        <TotalTalkTime>0</TotalTalkTime>
        <CallsDialed>0</CallsDialed>
        <MaxDialingTime>0</MaxDialingTime>
        <MaxTalkTime>0</MaxTalkTime>
        <AverageWorkTime>0</AverageWorkTime>
        <MaxWorkTime>0</MaxWorkTime>
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
        <AverageHoldTime>0</AverageHoldTime>
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
        <MaxHoldTime>0</MaxHoldTime>
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
			"ServiceLevel20": "1",
			"CallsAbandonedInQueue": "0",
			"TotalWorkTime": "85",
			"TotalHoldTime": "0",
			"CallsRinged": "7",
			"MaxAbandonedInIVRTime": "0",
			"AverageHoldTime": "0",
			"MaxRingTime": "12",
			"CallsOffered": "7",
			"CallsAbandoned": "0",
			"SatisfactionIndex": "0",
			"CallsHold": "0",
			"MaxAbandonedInRingTime": "0",
			"TotalRingTime": "32",
			"HandleRate": "1",
			"TotalAbandonedInIVRTime": "0",
			"CallsAbandonedInRinging": "0",
			"AverageAbandonedInQueueTime": "0",
			"TotalTalkTime": "447",
			"AverageWaitTime": "5",
			"TotalAbandonedInRingTime": "0",
			"CallsQueued": "7",
			"MaxTalkTime": "219",
			"AverageAbandonedInIVRTime": "0",
			"TotalAbandonTime": "0",
			"MaxHoldTime": "0",
			"AverageTalkTime": "64",
			"CallsAbandonedInIVR": "0",
			"CallsConsulted": "0",
			"MaxAbandonedInQueueTime": "0",
			"SatisfactionSurveysOffered": "0",
			"CallsHandled": "7",
			"MaxWaitTime": "13",
			"SatisfactionSurveysResponded": "0",
			"CallsTransferred": "0",
			"MaxAbandonTime": "0",
			"AverageRingTime": "5",
			"TotalWaitTime": "34",
			"AverageAbandonTime": "0",
			"AverageAbandonedInRingTime": "0",
			"TotalAbandonedInQueueTime": "0",
			"AverageWorkTime": "13",
			"AbandonedRate": "0",
			"MaxWorkTime": "17"
		},
		"Outbound": {
			"TotalDialingTime": "0",
			"TotalWorkTime": "0",
			"TotalHoldTime": "0",
			"SatisfactionSurveysOffered": "0",
			"CallsDialedSuccess": "0",
			"SatisfactionIndex": "0",
			"SatisfactionSurveysResponded": "0",
			"AverageDialingTime": "0",
			"CallsAnswered": "0",
			"TotalTalkTime": "0",
			"CallsDialed": "0",
			"MaxDialingTime": "0",
			"MaxTalkTime": "0",
			"AverageWorkTime": "0",
			"MaxWorkTime": "0",
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
			"AverageHoldTime": "0",
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
			"MaxHoldTime": "0",
			"AverageTalkTime": "0"
		}
	}],
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

