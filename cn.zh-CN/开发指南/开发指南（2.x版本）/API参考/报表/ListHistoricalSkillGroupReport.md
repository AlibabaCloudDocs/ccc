# ListHistoricalSkillGroupReport

调用ListHistoricalSkillGroupReport获取技能组历史数据报表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListHistoricalSkillGroupReport&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListHistoricalSkillGroupReport|系统规定参数。取值：ListHistoricalSkillGroupReport。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|100|分页大小，范围1-100。 |
|SkillGroupIdList|String|否|\["skg-test1@ccc-test", "skg-test2@ccc-test2"\]|待查询数据的技能组ID列表。如果不传，查询当前分页下的所有技能组。 |
|StartTime|Long|否|1604639129000|开始时间戳，默认是当天开始时间，最早为当前时间往前180天。 |
|EndTime|Long|否|1604725528000|截止时间戳，默认是当前时间。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of Items| |技能组报表列表 |
|Inbound|Struct| |呼入指标。 |
|AbandonRate|Float|0|放弃率，单位是%，等于（队列放弃量

 -   振铃放弃量） / 进入队列的电话数。 |
|AverageAbandonTime|Float|0|平均放弃时长，单位秒。 |
|AverageAbandonedInQueueTime|Float|0|平均排队放弃时长，单位秒。 |
|AverageAbandonedInRingTime|Float|0|平均响铃放弃时长，单位秒。 |
|AverageRingTime|Float|5|平均振铃时长，单位秒。 |
|AverageTalkTime|Float|64|平均通话时长，单位秒。 |
|AverageWaitTime|Float|5|平均等待时长，平均每通电话的坐席接起时等待时长。 |
|AverageWorkTime|Float|13|平均话后处理时长，单位秒。 |
|CallsAbandoned|Long|0|电话放弃量。 |
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
|MaxAbandonedInQueueTime|Long|0|最大排队放弃时长，单位秒。 |
|MaxAbandonedInRingTime|Long|0|最大振铃放弃时长，单位秒。 |
|MaxRingTime|Long|12|最大振铃时长，单位秒。 |
|MaxTalkTime|Long|0|最大通话时长，单位秒。 |
|MaxWaitTime|Long|13|最大等待时长，单位秒。 |
|MaxWorkTime|Long|12|最大话后处理时长，单位秒。 |
|SatisfactionIndex|Float|0|满意度指数，即满意度平均值。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|ServiceLevel20|Float|0|20S服务水平，单位%。电话从开始排队到接听时间少于20秒的电话数量/CallsQueued。 |
|TotalAbandonTime|Long|0|总放弃时长，单位秒。 |
|TotalAbandonedInQueueTime|Long|0|总排队放弃时长，单位秒。 |
|TotalAbandonedInRingTime|Long|0|总振铃放弃时长，单位秒。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalRingTime|Long|32|总振铃时长，单位秒。 |
|TotalTalkTime|Long|447|总通话时长，单位秒。 |
|TotalWaitTime|Long|34|总等待时长，单位秒。 |
|TotalWorkTime|Long|85|总话后处理时长，单位秒。 |
|Outbound|Struct| |呼出指标。 |
|AnswerRate|Float|0|接通率，单位%。 |
|AverageDialingTime|Float|37|平均拨号时长，单位秒。 |
|AverageTalkTime|Float|3|平均通话时长，单位秒。 |
|AverageWorkTime|Float|2|平均话后处理时长，单位秒。 |
|CallsAnswered|Long|1|电话接通量。 |
|CallsDialed|Long|6|电话拨号量。 |
|MaxDialingTime|Long|12|最大拨号时长，单位秒。 |
|MaxTalkTime|Long|0|最大通话时长，单位秒。 |
|MaxWorkTime|Long|0|最大话后处理时长，单位秒。 |
|SatisfactionIndex|Float|0|满意度指数，即满意度平均值。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalDialingTime|Long|218|总拨号时长，单位秒。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalTalkTime|Long|3|总通话时长，单位秒。 |
|TotalWorkTime|Long|9|总话后处理时长，单位秒。 |
|Overall|Struct| |整体指标。 |
|AverageBreakTime|Float|0|平均小休时长，单位秒。 |
|AverageReadyTime|Float|0|平均就绪时长，单位秒。 |
|AverageTalkTime|Float|0|平均通话时长，单位秒。 |
|AverageWorkTime|Float|8|平均话后处理时长，单位秒。 |
|MaxBreakTime|Long|1|最大小休时长，单位秒。 |
|MaxReadyTime|Long|19328|最大就绪时长，单位秒。 |
|MaxTalkTime|Long|0|最大通话时长，单位秒。 |
|MaxWorkTime|Long|12|最大话后处理时长，单位秒。 |
|OccupancyRate|Float|0.02332222293912065|座席利用率，单位%。 |
|SatisfactionIndex|Float|0|满意度指数，即满意度平均值。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalBreakTime|Long|3|总小休时长，单位为秒。 |
|TotalCalls|Long|13|总电话接待量。包括应答的呼入电话和接通的呼出电话。 |
|TotalHoldTime|Long|0|总通话保持时长，单位秒。 |
|TotalLoggedInTime|Long|23218|总登录时长，单位秒。 |
|TotalReadyTime|Long|22428|总就绪时长，单位为秒。 |
|TotalTalkTime|Long|449|总通话时长，单位秒。 |
|TotalWorkTime|Long|94|总话后处理时长，单位秒。 |
|SkillGroupId|String|skg-test1@ccc-test|技能组ID。 |
|SkillGroupName|String|test1|技能组名称。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|100|分页大小。 |
|TotalCount|Integer|4|总条目数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|26A34338-5CD9-4C95-A7A6-5BDCE76C6B94|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListHistoricalSkillGroupReport
&InstanceId=ccc-test
&PageNumber=1
&PageSize=100
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>26A34338-5CD9-4C95-A7A6-5BDCE76C6B94</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <TotalCount>4</TotalCount>
    <PageSize>100</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <SkillGroupName>test1</SkillGroupName>
        <SkillGroupId>skg-test1@ccc-test</SkillGroupId>
        <Inbound>
            <ServiceLevel20>0</ServiceLevel20>
            <CallsAbandonedInQueue>0</CallsAbandonedInQueue>
            <TotalWorkTime>85</TotalWorkTime>
            <TotalHoldTime>0</TotalHoldTime>
            <CallsRinged>7</CallsRinged>
            <MaxRingTime>12</MaxRingTime>
            <CallsOffered>7</CallsOffered>
            <CallsAbandoned>0</CallsAbandoned>
            <SatisfactionIndex>0</SatisfactionIndex>
            <CallsHold>0</CallsHold>
            <MaxAbandonedInRingTime>0</MaxAbandonedInRingTime>
            <TotalRingTime>32</TotalRingTime>
            <HandleRate>1</HandleRate>
            <CallsAbandonedInRinging>0</CallsAbandonedInRinging>
            <AverageAbandonedInQueueTime>0</AverageAbandonedInQueueTime>
            <TotalTalkTime>447</TotalTalkTime>
            <AverageWaitTime>5</AverageWaitTime>
            <TotalAbandonedInRingTime>0</TotalAbandonedInRingTime>
            <CallsQueued>7</CallsQueued>
            <MaxTalkTime>0</MaxTalkTime>
            <TotalAbandonTime>0</TotalAbandonTime>
            <AverageTalkTime>64</AverageTalkTime>
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
            <MaxWorkTime>12</MaxWorkTime>
            <AbandonRate>0</AbandonRate>
        </Inbound>
        <Outbound>
            <TotalDialingTime>218</TotalDialingTime>
            <TotalWorkTime>9</TotalWorkTime>
            <TotalHoldTime>0</TotalHoldTime>
            <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
            <SatisfactionIndex>0</SatisfactionIndex>
            <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
            <AverageDialingTime>37</AverageDialingTime>
            <CallsAnswered>1</CallsAnswered>
            <TotalTalkTime>3</TotalTalkTime>
            <CallsDialed>6</CallsDialed>
            <MaxDialingTime>12</MaxDialingTime>
            <MaxTalkTime>0</MaxTalkTime>
            <AverageWorkTime>2</AverageWorkTime>
            <MaxWorkTime>0</MaxWorkTime>
            <AverageTalkTime>3</AverageTalkTime>
            <AnswerRate>0</AnswerRate>
        </Outbound>
        <Overall>
            <TotalReadyTime>22428</TotalReadyTime>
            <TotalCalls>13</TotalCalls>
            <TotalBreakTime>3</TotalBreakTime>
            <TotalWorkTime>94</TotalWorkTime>
            <TotalHoldTime>0</TotalHoldTime>
            <SatisfactionSurveysOffered>0</SatisfactionSurveysOffered>
            <SatisfactionIndex>0</SatisfactionIndex>
            <AverageBreakTime>0</AverageBreakTime>
            <SatisfactionSurveysResponded>0</SatisfactionSurveysResponded>
            <TotalTalkTime>449</TotalTalkTime>
            <AverageReadyTime>0</AverageReadyTime>
            <TotalLoggedInTime>23218</TotalLoggedInTime>
            <MaxTalkTime>0</MaxTalkTime>
            <MaxReadyTime>19328</MaxReadyTime>
            <AverageWorkTime>8</AverageWorkTime>
            <MaxWorkTime>12</MaxWorkTime>
            <MaxBreakTime>1</MaxBreakTime>
            <OccupancyRate>0.02332222293912065</OccupancyRate>
            <AverageTalkTime>0</AverageTalkTime>
        </Overall>
    </List>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "26A34338-5CD9-4C95-A7A6-5BDCE76C6B94",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": {
		"TotalCount": "4",
		"PageSize": "100",
		"PageNumber": "1",
		"List": [{
			"SkillGroupName": "test1",
			"SkillGroupId": "skg-test1@ccc-test",
			"Inbound": {
				"ServiceLevel20": "0",
				"CallsAbandonedInQueue": "0",
				"TotalWorkTime": "85",
				"TotalHoldTime": "0",
				"CallsRinged": "7",
				"MaxRingTime": "12",
				"CallsOffered": "7",
				"CallsAbandoned": "0",
				"SatisfactionIndex": "0",
				"CallsHold": "0",
				"MaxAbandonedInRingTime": "0",
				"TotalRingTime": "32",
				"HandleRate": "1",
				"CallsAbandonedInRinging": "0",
				"AverageAbandonedInQueueTime": "0",
				"TotalTalkTime": "447",
				"AverageWaitTime": "5",
				"TotalAbandonedInRingTime": "0",
				"CallsQueued": "7",
				"MaxTalkTime": "0",
				"TotalAbandonTime": "0",
				"AverageTalkTime": "64",
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
				"MaxWorkTime": "12",
				"AbandonRate": "0"
			},
			"Outbound": {
				"TotalDialingTime": "218",
				"TotalWorkTime": "9",
				"TotalHoldTime": "0",
				"SatisfactionSurveysOffered": "0",
				"SatisfactionIndex": "0",
				"SatisfactionSurveysResponded": "0",
				"AverageDialingTime": "37",
				"CallsAnswered": "1",
				"TotalTalkTime": "3",
				"CallsDialed": "6",
				"MaxDialingTime": "12",
				"MaxTalkTime": "0",
				"AverageWorkTime": "2",
				"MaxWorkTime": "0",
				"AverageTalkTime": "3",
				"AnswerRate": "0"
			},
			"Overall": {
				"TotalReadyTime": "22428",
				"TotalCalls": "13",
				"TotalBreakTime": "3",
				"TotalWorkTime": "94",
				"TotalHoldTime": "0",
				"SatisfactionSurveysOffered": "0",
				"SatisfactionIndex": "0",
				"AverageBreakTime": "0",
				"SatisfactionSurveysResponded": "0",
				"TotalTalkTime": "449",
				"AverageReadyTime": "0",
				"TotalLoggedInTime": "23218",
				"MaxTalkTime": "0",
				"MaxReadyTime": "19328",
				"AverageWorkTime": "8",
				"MaxWorkTime": "12",
				"MaxBreakTime": "1",
				"OccupancyRate": "0.02332222293912065",
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
|400|Parameter.Format|The format of parameter %s is invalid. %s|该参数的格式不合法。|
|500|InternalService.Common|An internal service error occurred. %s|内部服务错误。|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

