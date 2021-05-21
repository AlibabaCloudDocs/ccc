# ListIntervalSkillGroupReport

调用ListIntervalSkillGroupReport获取技能组的分段汇总报表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListIntervalSkillGroupReport&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListIntervalSkillGroupReport|系统规定参数。取值：ListIntervalSkillGroupReport。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|SkillGroupId|String|是|skg-default@ccc-test|技能组ID。 |
|StartTime|Long|否|1604639129000|开始时间戳，默认是当天开始时间，最早为当前时间往前180天。 |
|EndTime|Long|否|1604725528000|截止时间戳，默认是当前时间，如果Interval为Daily，StartTime和EndTime最大间隔是180天。如果Interval为Hourly，最大间隔时间为10天。 |
|Interval|String|否|Hourly|分段汇总类型：Daily（按天汇总）/ Hourly（按小时汇总）默认是Daily。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Array of Data| |数据。 |
|Inbound|Struct| |呼入指标。 |
|AbandonRate|Float|0|放弃率，单位是%，等于（队列放弃量

 -   振铃放弃量） / 进入队列的电话数。 |
|AverageAbandonTime|Float|0|平均放弃时长，单位秒。 |
|AverageAbandonedInQueueTime|Float|0|平均排队放弃时长，单位秒。 |
|AverageAbandonedInRingTime|Float|0|平均响铃放弃时长，单位秒。 |
|AverageRingTime|Float|11|平均振铃时长，单位秒。 |
|AverageTalkTime|Float|5|平均通话时长，单位秒。 |
|AverageWaitTime|Float|11|平均等待时长，平均每通电话的坐席接起时等待时长。 |
|AverageWorkTime|Float|8|平均话后处理时长，单位秒。 |
|CallsAbandoned|Long|0|放弃量。 |
|CallsAbandonedInQueue|Long|0|队列放弃量，即电话进入技能组之后在排队环节放弃的数量。 |
|CallsAbandonedInRinging|Long|1|振铃放弃量。 |
|CallsConsulted|Long|0|发起咨询的电话数量，如果一通电话中发起多次咨询，算一次。 |
|CallsHandled|Long|2|座席应答电话数。一通电话分给多个座席，算一通。如果电话出现转接，但是转接的时候电话挂断了，此时不算入CallsAbandoned。 |
|CallsHold|Long|0|通话保持的电话数量。一通电话hold多次算一次，多次hold时长的总和算本次通话的保持时长。 |
|CallsOffered|Long|3|电话呼入数。 |
|CallsQueued|Long|3|进入队列的电话数，如果一次呼入多次进队列，算一通。 |
|CallsRinged|Long|3|座席振铃的电话数，一通电话分给多个座席，算一通。 |
|CallsTransferred|Long|0|被转接的电话数量，包括咨询转和盲转。 |
|HandleRate|Float|0.6666666666666666|应答率，单位%，等于 座席应答电话数 / 进入队列的电话数。 |
|MaxAbandonTime|Long|0|最大放弃时长，单位秒。 |
|MaxAbandonedInQueueTime|Long|0|最大排队放弃时长，单位秒。 |
|MaxAbandonedInRingTime|Long|0|最大振铃放弃时长，单位秒。 |
|MaxRingTime|Long|18|最大振铃时长，单位秒。 |
|MaxTalkTime|Long|6|最大通话时长，单位秒。 |
|MaxWaitTime|Long|18|最大等待时长，单位秒。 |
|MaxWorkTime|Long|19|最大话后处理时长，单位秒。 |
|SatisfactionIndex|Float|0|满意度指数，即满意度平均值。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|ServiceLevel20|Float|0|20S服务水平，单位%。电话从开始排队到接听时间少于20秒的电话数量/CallsQueued。 |
|TotalAbandonTime|Long|0|总放弃时长，单位秒。 |
|TotalAbandonedInQueueTime|Long|0|总排队放弃时长，单位秒。 |
|TotalAbandonedInRingTime|Long|0|总振铃放弃时长，单位秒。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalRingTime|Long|33|总振铃时长，单位秒。 |
|TotalTalkTime|Long|9|总通话时长，单位秒。 |
|TotalWaitTime|Long|33|总等待时长，单位秒。 |
|TotalWorkTime|Long|23|总话后处理时长，单位秒。 |
|Outbound|Struct| |呼出指标。 |
|AnswerRate|Float|0|接通率，单位%。 |
|AverageDialingTime|Float|30|平均拨号时长，单位秒。 |
|AverageTalkTime|Float|5|平均通话时长，单位秒。 |
|AverageWorkTime|Float|3|平均话后处理时长，单位秒。 |
|CallsAnswered|Long|1|电话接通量。 |
|CallsDialed|Long|2|电话拨号量。 |
|MaxDialingTime|Long|49|最大拨号时长，单位秒。 |
|MaxTalkTime|Long|5|最大通话时长，单位秒。 |
|MaxWorkTime|Long|4|最大话后处理时长，单位秒。 |
|SatisfactionIndex|Float|0|满意度指数，即满意度平均值。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalDialingTime|Long|60|总拨号时长，单位秒。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalTalkTime|Long|5|总通话时长，单位秒。 |
|TotalWorkTime|Long|5|总话后处理时长，单位秒。 |
|Overall|Struct| |整体指标。 |
|AverageBreakTime|Float|0|平均小休时长，单位秒。 |
|AverageReadyTime|Float|0|平均就绪时长，单位秒。 |
|AverageTalkTime|Float|0|平均通话时长，单位秒。 |
|AverageWorkTime|Float|6|平均话后处理时长，单位秒。 |
|MaxBreakTime|Long|1|最大小休时长，单位秒。 |
|MaxReadyTime|Long|4927|最大就绪时长，单位秒。 |
|MaxTalkTime|Long|6|最大通话时长，单位秒。 |
|MaxWorkTime|Long|19|最大话后处理时长，单位秒。 |
|OccupancyRate|Float|0.00422315148470254|座席利用率，单位%。 |
|SatisfactionIndex|Float|0|满意度指数，即满意度平均值。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalBreakTime|Long|5|总小休时长，单位为秒。 |
|TotalCalls|Long|5|总电话接待量。包括应答的呼入电话和接通的呼出电话。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalLoggedInTime|Long|9236|总登录时长，单位秒。 |
|TotalReadyTime|Long|9106|总就绪时长，单位为秒。 |
|TotalTalkTime|Long|13|总通话时长，单位秒。 |
|TotalWorkTime|Long|27|总话后处理时长，单位秒。 |
|StatsTime|Long|1604639129000|时间戳，时间段开始时间。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|943D8EF3-3321-471F-A104-51C96FCA94D6|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListIntervalSkillGroupReport
&InstanceId=ccc-test
&SkillGroupId=skg-default@ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>943D8EF3-3321-471F-A104-51C96FCA94D6</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <StatsTime>1604639129000</StatsTime>
    <Inbound>
        <ServiceLevel20>0</ServiceLevel20>
        <CallsAbandonedInQueue>0</CallsAbandonedInQueue>
        <TotalWorkTime>23</TotalWorkTime>
        <TotalHoldTime>0</TotalHoldTime>
        <CallsRinged>3</CallsRinged>
        <MaxRingTime>18</MaxRingTime>
        <CallsOffered>3</CallsOffered>
        <CallsAbandoned>0</CallsAbandoned>
        <SatisfactionIndex>0</SatisfactionIndex>
        <CallsHold>0</CallsHold>
        <MaxAbandonedInRingTime>0</MaxAbandonedInRingTime>
        <TotalRingTime>33</TotalRingTime>
        <HandleRate>0.6666666666666666</HandleRate>
        <CallsAbandonedInRinging>1</CallsAbandonedInRinging>
        <AverageAbandonedInQueueTime>0</AverageAbandonedInQueueTime>
        <TotalTalkTime>9</TotalTalkTime>
        <AverageWaitTime>11</AverageWaitTime>
        <TotalAbandonedInRingTime>0</TotalAbandonedInRingTime>
        <CallsQueued>3</CallsQueued>
        <MaxTalkTime>6</MaxTalkTime>
        <TotalAbandonTime>0</TotalAbandonTime>
        <AverageTalkTime>5</AverageTalkTime>
        <CallsConsulted>0</CallsConsulted>
        <MaxAbandonedInQueueTime>0</MaxAbandonedInQueueTime>
        <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
        <CallsHandled>2</CallsHandled>
        <MaxWaitTime>18</MaxWaitTime>
        <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
        <CallsTransferred>0</CallsTransferred>
        <MaxAbandonTime>0</MaxAbandonTime>
        <AverageRingTime>11</AverageRingTime>
        <TotalWaitTime>33</TotalWaitTime>
        <AverageAbandonTime>0</AverageAbandonTime>
        <AverageAbandonedInRingTime>0</AverageAbandonedInRingTime>
        <TotalAbandonedInQueueTime>0</TotalAbandonedInQueueTime>
        <AverageWorkTime>8</AverageWorkTime>
        <MaxWorkTime>19</MaxWorkTime>
        <AbandonRate>0</AbandonRate>
    </Inbound>
    <Outbound>
        <TotalDialingTime>60</TotalDialingTime>
        <TotalWorkTime>5</TotalWorkTime>
        <TotalHoldTime>0</TotalHoldTime>
        <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
        <SatisfactionIndex>0</SatisfactionIndex>
        <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
        <AverageDialingTime>30</AverageDialingTime>
        <CallsAnswered>1</CallsAnswered>
        <TotalTalkTime>5</TotalTalkTime>
        <CallsDialed>2</CallsDialed>
        <MaxDialingTime>49</MaxDialingTime>
        <MaxTalkTime>5</MaxTalkTime>
        <AverageWorkTime>3</AverageWorkTime>
        <MaxWorkTime>4</MaxWorkTime>
        <AverageTalkTime>5</AverageTalkTime>
        <AnswerRate>0</AnswerRate>
    </Outbound>
    <Overall>
        <TotalReadyTime>9106</TotalReadyTime>
        <TotalCalls>5</TotalCalls>
        <TotalBreakTime>5</TotalBreakTime>
        <TotalWorkTime>27</TotalWorkTime>
        <TotalHoldTime>0</TotalHoldTime>
        <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
        <SatisfactionIndex>0</SatisfactionIndex>
        <AverageBreakTime>0</AverageBreakTime>
        <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
        <TotalTalkTime>13</TotalTalkTime>
        <AverageReadyTime>0</AverageReadyTime>
        <TotalLoggedInTime>9236</TotalLoggedInTime>
        <MaxTalkTime>6</MaxTalkTime>
        <MaxReadyTime>4927</MaxReadyTime>
        <AverageWorkTime>6</AverageWorkTime>
        <MaxWorkTime>19</MaxWorkTime>
        <MaxBreakTime>1</MaxBreakTime>
        <OccupancyRate>0.00422315148470254</OccupancyRate>
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
		"StatsTime": "1604639129000",
		"Inbound": {
			"ServiceLevel20": "0",
			"CallsAbandonedInQueue": "0",
			"TotalWorkTime": "23",
			"TotalHoldTime": "0",
			"CallsRinged": "3",
			"MaxRingTime": "18",
			"CallsOffered": "3",
			"CallsAbandoned": "0",
			"SatisfactionIndex": "0",
			"CallsHold": "0",
			"MaxAbandonedInRingTime": "0",
			"TotalRingTime": "33",
			"HandleRate": "0.6666666666666666",
			"CallsAbandonedInRinging": "1",
			"AverageAbandonedInQueueTime": "0",
			"TotalTalkTime": "9",
			"AverageWaitTime": "11",
			"TotalAbandonedInRingTime": "0",
			"CallsQueued": "3",
			"MaxTalkTime": "6",
			"TotalAbandonTime": "0",
			"AverageTalkTime": "5",
			"CallsConsulted": "0",
			"MaxAbandonedInQueueTime": "0",
			"SatisfactionSurveysOffered": "0",
			"CallsHandled": "2",
			"MaxWaitTime": "18",
			"SatisfactionSurveysResponded": "0",
			"CallsTransferred": "0",
			"MaxAbandonTime": "0",
			"AverageRingTime": "11",
			"TotalWaitTime": "33",
			"AverageAbandonTime": "0",
			"AverageAbandonedInRingTime": "0",
			"TotalAbandonedInQueueTime": "0",
			"AverageWorkTime": "8",
			"MaxWorkTime": "19",
			"AbandonRate": "0"
		},
		"Outbound": {
			"TotalDialingTime": "60",
			"TotalWorkTime": "5",
			"TotalHoldTime": "0",
			"SatisfactionSurveysOffered": "0",
			"SatisfactionIndex": "0",
			"SatisfactionSurveysResponded": "0",
			"AverageDialingTime": "30",
			"CallsAnswered": "1",
			"TotalTalkTime": "5",
			"CallsDialed": "2",
			"MaxDialingTime": "49",
			"MaxTalkTime": "5",
			"AverageWorkTime": "3",
			"MaxWorkTime": "4",
			"AverageTalkTime": "5",
			"AnswerRate": "0"
		},
		"Overall": {
			"TotalReadyTime": "9106",
			"TotalCalls": "5",
			"TotalBreakTime": "5",
			"TotalWorkTime": "27",
			"TotalHoldTime": "0",
			"SatisfactionSurveysOffered": "0",
			"SatisfactionIndex": "0",
			"AverageBreakTime": "0",
			"SatisfactionSurveysResponded": "0",
			"TotalTalkTime": "13",
			"AverageReadyTime": "0",
			"TotalLoggedInTime": "9236",
			"MaxTalkTime": "6",
			"MaxReadyTime": "4927",
			"AverageWorkTime": "6",
			"MaxWorkTime": "19",
			"MaxBreakTime": "1",
			"OccupancyRate": "0.00422315148470254",
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

