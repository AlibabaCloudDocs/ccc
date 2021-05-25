# GetCallDetailRecord

调用GetCallDetailRecord根据通话ID获取通话的详细操作日志。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=GetCallDetailRecord&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetCallDetailRecord|系统规定参数。取值：GetCallDetailRecord。 |
|ContactId|String|是|job-109634426711871319|通过指定的contactId来查询某一通电话的记录，contactId可以通过软电话SDK发生通话时获取到，也可通过ListCallDetailRecords获取。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|AgentIds|String|user-test@ccc-test|坐席ID列表，多个值用逗号分隔。 |
|AgentNames|String|云呼测试坐席|坐席名称列表。 |
|CallDuration|Long|50|通话时长，单位秒。 |
|CalledNumber|String|133xxxx2315|被叫号码。 |
|CallingNumber|String|053xxxx3128|主叫号码。 |
|CdrAgentEvents|Array of CdrAgentEvents| |坐席事件列表。 |
|AgentId|String|user-test@ccc-test|坐席ID。 |
|AgentName|String|测试坐席|坐席名称。 |
|EventSequence|Array of EventSequence| |事件序列。 |
|Event|String|Dialing|事件名称。 |
|EventTime|Long|1604639129000|事件发生时间戳。 |
|SkillGroupId|String|skg-default@ccc-test|技能组ID。 |
|CdrIvrEvents|Array of CdrIvrEvents| |IVR事件列表。 |
|EventSequence|Array of EventSequence| |事件序列。 |
|Event|String|Route2IVR|事件名称。 |
|EventTime|Long|1604639129000|事件发生时间戳。 |
|FlowId|String|edaf2eaa-8f88-44ca-812e-41b3cd2b7a90|联系流ID。 |
|CdrQueueEvents|Array of CdrQueueEvents| |队列事件列表。 |
|EventSequence|Array of EventSequence| |事件序列。 |
|Event|String|Enqueue|事件名称。 |
|EventTime|Long|1604639129000|事件发生时间戳。 |
|FlowId|String|edaf2eaa-8f88-44ca-812e-41b3cd2b7a90|联系流ID。 |
|QueueId|String|skg-default@ccc-test|队列ID。 |
|QueueName|String|Defalut|队列名称。 |
|QueueType|Integer|1|队列类型，1为技能组，2为坐席。 |
|ContactDisposition|String|Success|电话结束原因。 Success\(正常\)，NoAnswer\(未接通\)，AbandonedInContactFlow\(IVR中放弃\)，AbandonedInQueue\(排队放弃\)，AbandonedRing\(振铃放弃\)，Reject\(客户拒接\)。 |
|ContactId|String|job-109634426711871319|通话ID。 |
|ContactType|String|Outbound|通话类型。取值：INBOUND（呼入），OUTBOND（呼出）。 |
|EstablishedTime|Long|1532458000000|通话建立的时间，如果通话没有建立，此值为空。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|RecordingReady|Boolean|true|录音是否已经生成。若通话没有建立，则返回false。 |
|ReleaseInitiator|String|customer|挂断方：agent 客服，customer 客户。 |
|ReleaseTime|Long|1532458000000|会话结束时间。 |
|Satisfaction|Integer|1|满意度。 |
|SatisfactionSurveyChannel|String|语音|满意度调查渠道：语音满意度，或者短信满意度。 |
|SatisfactionSurveyOffered|Boolean|true|是否发送了满意度。 |
|SkillGroupIds|String|skg-default@ccc-test|参与通话的座席所属的技能组ID，多个技能组以逗号分隔。 |
|SkillGroupNames|String|默认技能组|参与通话的座席所属的技能组名称，多个技能组以逗号分隔。 |
|StartTime|Long|1532458000000|通话开始时间，呼入从进入IVR开始，呼出从开始接通计算。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|7BEEA660-A45A-45E3-98CC-AFC65E715C23|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetCallDetailRecord
&ContactId=job-109634426711871319
&InstanceId=ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>7BEEA660-A45A-45E3-98CC-AFC65E715C23</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <SkillGroupIds>skg-default@ccc-test</SkillGroupIds>
    <CalledNumber>133xxxx2315</CalledNumber>
    <ContactType>Outbound</ContactType>
    <ReleaseInitiator>customer</ReleaseInitiator>
    <InstanceId>ccc-test</InstanceId>
    <ContactDisposition>Success</ContactDisposition>
    <Satisfaction>1</Satisfaction>
    <StartTime>1532458000000</StartTime>
    <ContactId>job-109634426711871319</ContactId>
    <CallDuration>50</CallDuration>
    <CallingNumber>053xxxx3128</CallingNumber>
    <RecordingReady>true</RecordingReady>
    <ReleaseTime>1532458000000</ReleaseTime>
    <SkillGroupNames>默认技能组</SkillGroupNames>
    <SatisfactionSurveyChannel>语音</SatisfactionSurveyChannel>
    <SatisfactionSurveyOffered>true</SatisfactionSurveyOffered>
    <AgentIds>user-test@ccc-test	</AgentIds>
    <EstablishedTime>1532458000000</EstablishedTime>
    <AgentNames>云呼测试坐席</AgentNames>
    <CdrAgentEvents>
        <SkillGroupId>skg-default@ccc-test</SkillGroupId>
        <AgentName>测试坐席</AgentName>
        <AgentId>user-test@ccc-test</AgentId>
        <EventSequence>
            <EventTime>1604639129000</EventTime>
            <Event>Dialing</Event>
        </EventSequence>
    </CdrAgentEvents>
    <CdrIvrEvents>
        <FlowId>edaf2eaa-8f88-44ca-812e-41b3cd2b7a90</FlowId>
        <EventSequence>
            <EventTime>1604639129000</EventTime>
            <Event>Route2IVR</Event>
        </EventSequence>
    </CdrIvrEvents>
    <CdrQueueEvents>
        <FlowId>edaf2eaa-8f88-44ca-812e-41b3cd2b7a90</FlowId>
        <QueueId>skg-default@ccc-test</QueueId>
        <QueueName>Defalut</QueueName>
        <QueueType>1</QueueType>
        <EventSequence>
            <EventTime>1604639129000</EventTime>
            <Event>Enqueue</Event>
        </EventSequence>
    </CdrQueueEvents>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "7BEEA660-A45A-45E3-98CC-AFC65E715C23",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": {
		"SkillGroupIds": "skg-default@ccc-test",
		"CalledNumber": "133xxxx2315",
		"ContactType": "Outbound",
		"ReleaseInitiator": "customer",
		"InstanceId": "ccc-test",
		"ContactDisposition": "Success",
		"Satisfaction": "1",
		"StartTime": "1532458000000",
		"ContactId": "job-109634426711871319",
		"CallDuration": "50",
		"CallingNumber": "053xxxx3128",
		"RecordingReady": "true",
		"ReleaseTime": "1532458000000",
		"SkillGroupNames": "默认技能组",
		"SatisfactionSurveyChannel": "语音",
		"SatisfactionSurveyOffered": "true",
		"AgentIds": "user-test@ccc-test\t",
		"EstablishedTime": "1532458000000",
		"AgentNames": "云呼测试坐席",
		"CdrAgentEvents": [{
			"SkillGroupId": "skg-default@ccc-test",
			"AgentName": "测试坐席",
			"AgentId": "user-test@ccc-test",
			"EventSequence": [{
				"EventTime": "1604639129000",
				"Event": "Dialing"
			}]
		}],
		"CdrIvrEvents": [{
			"FlowId": "edaf2eaa-8f88-44ca-812e-41b3cd2b7a90",
			"EventSequence": [{
				"EventTime": "1604639129000",
				"Event": "Route2IVR"
			}]
		}],
		"CdrQueueEvents": [{
			"FlowId": "edaf2eaa-8f88-44ca-812e-41b3cd2b7a90",
			"QueueId": "skg-default@ccc-test",
			"QueueName": "Defalut",
			"QueueType": "1",
			"EventSequence": [{
				"EventTime": "1604639129000",
				"Event": "Enqueue"
			}]
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

