# ListSkillGroupSummaryReports

调用接口：ListSkillGroupSummaryReports获取技能组汇总报表

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListSkillGroupSummaryReports&type=RPC&version=2017-07-05)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListSkillGroupSummaryReports|系统规定参数。取值：**ListSkillGroupSummaryReports**。 |
|EndTime|String|是|2018-01-10 00:00:00|终止日期，格式yyyy-MM-dd HH:mm:ss；需要注意目前仅支持按天维度的查询，参数设置请参考案例。 |
|InstanceId|String|是|b0eb2742-f37e-4c67-82d4-25c651c1c450|呼叫中心实例ID |
|StartTime|String|是|2018-01-10 00:00:00|起始日期，格式yyyy-MM-dd HH:mm:ss，；需要注意目前仅支持按天维度的查询，参数设置请参考案例，同时不得早于6个月前的时间点。 |
|SkillGroupIds|String|否|8fb654c6-17c6-4501-ba57-f5ddeb919814|技能组ID列表，使用“,”隔开，最多50个；不传查询全部. |
|PageNumber|Integer|否|1|分页序号，默认值为1。 |
|PageSize|Integer|否|2|分页大小，默认值为10，最大是100。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码 |
|HttpStatusCode|Integer|200|HTTP状态码 |
|Message|String|无|响应信息 |
|PagedSkillGroupSummaryReport|Struct| |报表 |
|List|Array of SkillGroupSummaryReport| |列表 |
|SkillGroupSummaryReport| | | |
|Inbound|Struct| |呼入指标 |
|AbandonedInQueueOfQueueCount|Long|0|技能组排队放弃次数。 |
|AnsweredByAgentOfQueueCount|Long|0|技能组人工接起次数。 |
|AnsweredByAgentOfQueueMaxWaitTimeDuration|Long|0|坐席接起时队列最大等待时间。 |
|AnsweredByAgentOfQueueWaitTimeDuration|Long|0|坐席接起时队列等待时间。 |
|AverageRingTime|Long|0|平均振铃时长，单位秒。 |
|AverageTalkTime|Long|0|平均通话时长，单位秒。 |
|AverageWorkTime|Long|0|平均话后处理时长，单位秒。 |
|CallsHandled|Long|0|电话应答数。 |
|CallsOffered|Long|0|电话呼入数。 |
|GiveUpByAgentOfQueueCount|Long|0|技能组振铃放弃次数。 |
|HandleRate|Float|0|应答率，单位%。 |
|InComingQueueOfQueueCount|Long|0|技能组呼入次数。 |
|MaxRingTime|Long|0|最大振铃时长，单位秒。 |
|MaxTalkTime|String|0|总通话时长，单位秒。 |
|MaxWorkTime|Long|0|总话后处理时长，单位秒。 |
|OverFlowInQueueOfQueueCount|Long|0|技能组排队超时次数。 |
|QueueMaxWaitTimeDuration|Long|0|队列最大等待时间。 |
|QueueWaitTimeDuration|Long|0|队列等待时间。 |
|SatisfactionIndex|Float|0|满意度指数，单位%。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|ServiceLevel20|Float|0|服务水平即20s应答率，单位%。 |
|TotalRingTime|Long|0|总振铃时长，单位秒。 |
|TotalTalkTime|Long|0|总通话时长，单位秒。 |
|TotalWorkTime|Long|0|总话后处理时长，单位秒。 |
|InstanceId|String|b0eb2742-f37e-4c67-82d4-25c651c1c450|呼叫中心实例ID |
|Outbound|Struct| |呼出指标 |
|AnswerRate|Float|0.5|接通率，单位%。 |
|AverageDialingTime|Long|14|平均拨号时长，单位秒。 |
|AverageTalkTime|Long|2|平均通话时长，单位秒。 |
|AverageWorkTime|Long|1|平均话后处理时长，单位秒。 |
|CallsAnswered|Long|0|电话接通量。 |
|CallsDialed|Long|2|电话拨号量。 |
|MaxDialingTime|Long|14|最大拨号时长，单位秒。 |
|MaxTalkTime|Long|2|最大通话时长，单位秒。 |
|MaxWorkTime|Long|1|总话后处理时长，单位秒。 |
|SatisfactionIndex|Float|0|满意度指数，单位%。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalDialingTime|Long|28|总拨号时长，单位秒。 |
|TotalTalkTime|Long|2|总通话时长，单位秒。 |
|TotalWorkTime|Long|1|总话后处理时长，单位秒。 |
|Overall|Struct| |整体指标 |
|AverageReadyTime|Long|225|平均就绪时长，单位为秒。 |
|AverageTalkTime|Long|2|平均通话时长，单位秒。 |
|AverageWorkTime|Long|1|平均话后处理时长，单位秒。 |
|MaxReadyTime|Long|480|最大就绪时长，单位为秒。 |
|MaxTalkTime|Long|2|最大通话时长，单位秒。 |
|MaxWorkTime|Long|1|总话后处理时长，单位秒。 |
|OccupancyRate|Float|0.0025906735099852085|座席利用率，单位%。 |
|SatisfactionIndex|Float|0|满意度指数，单位%。 |
|SatisfactionSurveysOffered|Long|0|满意度调查发送次数。 |
|SatisfactionSurveysResponded|Long|0|满意度调查响应次数。 |
|TotalBreakTime|Long|1|总小休时长，单位为秒。 |
|TotalCalls|Long|1|总电话接待量。包括应答的呼入电话和接通的呼出电话。 |
|TotalLoggedInTime|Long|1158|总登录时长，单位秒。 |
|TotalReadyTime|Long|1126|总就绪时长，单位为秒。 |
|TotalTalkTime|Long|2|总通话时长，单位秒。 |
|TotalWorkTime|Long|1|总话后处理时长，单位秒。 |
|SkillGroupId|String|8fb654c6-17c6-4501-ba57-f5ddeb919814|技能组ID |
|SkillGroupName|String|其他服务|技能组名称 |
|PageNumber|Integer|1|分页序号 |
|PageSize|Integer|2|分页大小 |
|TotalCount|Integer|2|总个数 |
|RequestId|String|11C37A88-C5D4-4538-A768-AFFFC2397896|请求ID |
|Success|Boolean|true|是否成功 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListSkillGroupSummaryReports
&EndTime=2018-01-10  00:00:00
&InstanceId=b0eb2742-f37e-4c67-82d4-25c651c1c450
&StartTime=2018-01-10  00:00:00
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListSkillGroupSummaryReportsResponse>
      <pagedSkillGroupSummaryReport>
            <pageNumber>1</pageNumber>
            <pageSize>10</pageSize>
            <totalCount>1</totalCount>
            <list>
                  <instanceId>b0eb2742-f37e-4c67-82d4-25c651c1c450</instanceId>
                  <inbound>
                        <queueWaitTimeDuration>0</queueWaitTimeDuration>
                        <maxWorkTime>0</maxWorkTime>
                        <maxTalkTime>0</maxTalkTime>
                        <queueMaxWaitTimeDuration>0</queueMaxWaitTimeDuration>
                        <serviceLevel20>0</serviceLevel20>
                        <totalTalkTime>0</totalTalkTime>
                        <giveUpByAgentOfQueueCount>0</giveUpByAgentOfQueueCount>
                        <averageRingTime>0</averageRingTime>
                        <maxRingTime>0</maxRingTime>
                        <satisfactionSurveysResponded>0</satisfactionSurveysResponded>
                        <totalWorkTime>0</totalWorkTime>
                        <totalRingTime>0</totalRingTime>
                        <inComingQueueOfQueueCount>0</inComingQueueOfQueueCount>
                        <handleRate>0</handleRate>
                        <answeredByAgentOfQueueWaitTimeDuration>0</answeredByAgentOfQueueWaitTimeDuration>
                        <overFlowInQueueOfQueueCount>0</overFlowInQueueOfQueueCount>
                        <satisfactionSurveysOffered>0</satisfactionSurveysOffered>
                        <averageTalkTime>0</averageTalkTime>
                        <callsOffered>0</callsOffered>
                        <averageWorkTime>0</averageWorkTime>
                        <callsHandled>0</callsHandled>
                        <answeredByAgentOfQueueCount>0</answeredByAgentOfQueueCount>
                        <satisfactionIndex>0</satisfactionIndex>
                        <abandonedInQueueOfQueueCount>0</abandonedInQueueOfQueueCount>
                        <answeredByAgentOfQueueMaxWaitTimeDuration>0</answeredByAgentOfQueueMaxWaitTimeDuration>
                  </inbound>
                  <outbound>
                        <maxTalkTime>2</maxTalkTime>
                        <averageTalkTime>2</averageTalkTime>
                        <totalWorkTime>1</totalWorkTime>
                        <maxDialingTime>14</maxDialingTime>
                        <callsDialed>2</callsDialed>
                        <averageDialingTime>14</averageDialingTime>
                        <satisfactionSurveysResponded>0</satisfactionSurveysResponded>
                        <satisfactionIndex>0</satisfactionIndex>
                        <totalDialingTime>28</totalDialingTime>
                        <answerRate>0.5</answerRate>
                        <callsAnswered>1</callsAnswered>
                        <totalTalkTime>2</totalTalkTime>
                        <maxWorkTime>1</maxWorkTime>
                        <averageWorkTime>1</averageWorkTime>
                        <satisfactionSurveysOffered>0</satisfactionSurveysOffered>
                  </outbound>
                  <overall>
                        <maxReadyTime>480</maxReadyTime>
                        <maxTalkTime>2</maxTalkTime>
                        <averageTalkTime>2</averageTalkTime>
                        <totalWorkTime>1</totalWorkTime>
                        <totalLoggedInTime>1158</totalLoggedInTime>
                        <totalReadyTime>1126</totalReadyTime>
                        <totalBreakTime>1</totalBreakTime>
                        <satisfactionSurveysResponded>0</satisfactionSurveysResponded>
                        <satisfactionIndex>0</satisfactionIndex>
                        <totalCalls>1</totalCalls>
                        <averageReadyTime>225</averageReadyTime>
                        <totalTalkTime>2</totalTalkTime>
                        <maxWorkTime>1</maxWorkTime>
                        <averageWorkTime>1</averageWorkTime>
                        <occupancyRate>0.0025906735099852085</occupancyRate>
                        <satisfactionSurveysOffered>0</satisfactionSurveysOffered>
                  </overall>
                  <skillGroupName>其他服务</skillGroupName>
                  <skillGroupId>8fb654c6-17c6-4501-ba57-f5ddeb919814</skillGroupId>
            </list>
      </pagedSkillGroupSummaryReport>
      <code>OK</code>
      <requestId>11C37A88-C5D4-4538-A768-AFFFC2397896</requestId>
      <success>true</success>
      <httpStatusCode>200</httpStatusCode>
</ListSkillGroupSummaryReportsResponse>
```

`JSON` 格式

```
{
    "pagedSkillGroupSummaryReport": {
        "pageNumber": 1,
        "pageSize": 10,
        "totalCount": 1,
        "list": [
            {
                "instanceId": "b0eb2742-f37e-4c67-82d4-25c651c1c450",
                "inbound":{
                        "queueWaitTimeDuration":0,
                        "maxWorkTime":0,
                        "maxTalkTime":0,
                        "queueMaxWaitTimeDuration":0,
                        "serviceLevel20":0,
                        "totalTalkTime":0,
                        "giveUpByAgentOfQueueCount":0,
                        "averageRingTime":0,
                        "maxRingTime":0,
                        "satisfactionSurveysResponded":0,
                        "totalWorkTime":0,
                        "totalRingTime":0,
                        "inComingQueueOfQueueCount":0,
                        "handleRate":0,
                        "answeredByAgentOfQueueWaitTimeDuration":0,
                        "overFlowInQueueOfQueueCount":0,
                        "satisfactionSurveysOffered":0,
                        "averageTalkTime":0,
                        "callsOffered":0,
                        "averageWorkTime":0,
                        "callsHandled":0,
                        "answeredByAgentOfQueueCount":0,
                        "satisfactionIndex":0,
                        "abandonedInQueueOfQueueCount":0,
                        "answeredByAgentOfQueueMaxWaitTimeDuration":0
                    },
                "outbound": {
                    "maxTalkTime": 2,
                    "averageTalkTime": 2,
                    "totalWorkTime": 1,
                    "maxDialingTime": 14,
                    "callsDialed": 2,
                    "averageDialingTime": 14,
                    "satisfactionSurveysResponded": 0,
                    "satisfactionIndex": 0,
                    "totalDialingTime": 28,
                    "answerRate": 0.5,
                    "callsAnswered": 1,
                    "totalTalkTime": 2,
                    "maxWorkTime": 1,
                    "averageWorkTime": 1,
                    "satisfactionSurveysOffered": 0
                },
                "overall": {
                    "maxReadyTime": 480,
                    "maxTalkTime": 2,
                    "averageTalkTime": 2,
                    "totalWorkTime": 1,
                    "totalLoggedInTime": 1158,
                    "totalReadyTime": 1126,
                    "totalBreakTime": 1,
                    "satisfactionSurveysResponded": 0,
                    "satisfactionIndex": 0,
                    "totalCalls": 1,
                    "averageReadyTime": 225,
                    "totalTalkTime": 2,
                    "maxWorkTime": 1,
                    "averageWorkTime": 1,
                    "occupancyRate": 0.0025906735099852085,
                    "satisfactionSurveysOffered": 0
                },
                "skillGroupName": "其他服务",
                "skillGroupId": "8fb654c6-17c6-4501-ba57-f5ddeb919814"
            }
        ]
    },
    "code": "OK",
    "requestId": "11C37A88-C5D4-4538-A768-AFFFC2397896",
    "success": true,
    "httpStatusCode": 200
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

