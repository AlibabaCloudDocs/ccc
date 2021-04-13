# ListCallDetailRecords

调用ListCallDetailRecords获取呼叫中心中的通话详单数据。

**注意**：为了保证查询效率，返回数据中的 TotalCount 字段，只会在查询第一页时赋值。查询其他页时返回0。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListCallDetailRecords&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListCallDetailRecords|系统规定参数。取值：ListCallDetailRecords。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|100|分页大小，范围1-100。 |
|CalledNumber|String|否|132xxxx0523|被叫号码。 |
|CallingNumber|String|否|073xxxx7539|主叫号码。 |
|StartTime|Long|否|1532448000000|获取的历史数据的起始时间，默认为当天的0时。 |
|EndTime|Long|否|1532707199000|获取的历史数据的终止时间，默认为当前时间。 |
|ContactType|String|否|Outbound|按呼叫类型筛选。取值：

 -   Inbound（呼入）
-   Outbound（呼出）
-   Back2Back（双呼） |
|ContactDisposition|String|否|Success|按挂断类型筛选。取值：

 -   Success\(正常\)
-   NoAnswer\(未接通\)
-   AbandonedInContactFlow\(IVR中放弃\)
-   AbandonedInQueue\(排队放弃\)
-   AbandonedRing\(振铃放弃\)
-   QueueOverflow\(排队超时\)
-   OneStepTransfer\(转外线\) |
|ContactId|String|否|4321444829|通过指定的contactId来查询某一通电话的记录，contactId可以通过软电话SDK发生通话时获取到。 |
|AgentId|String|否|ccc-user@ccc-test|坐席ID。 |
|SkillGroupId|String|否|skg-default@ccc-test|通话涉及的技能组ID。 |
|SortOrder|String|否|ASC|如果OrderByField为空，默认按开始时间降序排列。取值: ASC/DESC。 |
|OrderByField|String|否|statTime|排序字段。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of CallDetailRecord| |通话记录列表。 |
|AgentIds|String|user-test@ccc-test|坐席ID列表，多个值用逗号分隔。 |
|AgentNames|String|云呼测试坐席|坐席名称列表。 |
|CallDuration|String|30|通话时长，单位秒。 |
|CalledNumber|String|133xxxx2315|被叫号码。 |
|CallingNumber|String|053xxxx3128|主叫号码。 |
|ContactDisposition|String|Success|电话结束原因。 Success\(正常\)，NoAnswer\(未接通\)，AbandonedInContactFlow\(IVR中放弃\)，AbandonedInQueue\(排队放弃\)，AbandonedRing\(振铃放弃\)，QueueOverflow\(排队超时\)，OneStepTransfer\(转外线\)。 |
|ContactId|String|job-76604722428454704|通话ID。 |
|ContactType|String|Outbound|通话类型。取值：INBOUND（呼入），OUTBOND（呼出）。 |
|EstablishedTime|Long|1532448000000|通话建立的时间，如果通话没有建立，此值为空。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|RecordingReady|Boolean|true|录音是否已经生成。若通话没有建立，则返回false。 |
|SkillGroupIds|String|skg-default@ccc-test|参与通话的座席所属的技能组ID，多个技能组以逗号分隔。 |
|SkillGroupNames|String|默认技能组|参与通话的座席所属的技能组名称，多个技能组以逗号分隔。 |
|StartTime|Long|1532448000000|通话开始时间，内呼从进入IVR开始，外呼从开始接通计算。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|10|分页大小。 |
|TotalCount|Integer|11|总条目数，只有PageNumber为1才会返回，其他都是0。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListCallDetailRecords
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
    <TotalCount>11</TotalCount>
    <PageSize>10</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <SkillGroupIds>skg-default@ccc-test</SkillGroupIds>
        <CalledNumber>133xxxx2315</CalledNumber>
        <ContactType>Outbound</ContactType>
        <InstanceId>ccc-test</InstanceId>
        <ContactDisposition>Success</ContactDisposition>
        <StartTime>1532448000000</StartTime>
        <ContactId>job-76604722428454704</ContactId>
        <CallDuration>30</CallDuration>
        <CallingNumber>053xxxx3128</CallingNumber>
        <SkillGroupNames>默认技能组</SkillGroupNames>
        <AgentIds>user-test@ccc-test</AgentIds>
        <EstablishedTime>1532448000000</EstablishedTime>
        <AgentNames>云呼测试坐席</AgentNames>
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
		"TotalCount": "11",
		"PageSize": "10",
		"PageNumber": "1",
		"List": [{
			"SkillGroupIds": "skg-default@ccc-test",
			"CalledNumber": "133xxxx2315",
			"ContactType": "Outbound",
			"InstanceId": "ccc-test",
			"ContactDisposition": "Success",
			"StartTime": "1532448000000",
			"ContactId": "job-76604722428454704",
			"CallDuration": "30",
			"CallingNumber": "053xxxx3128",
			"SkillGroupNames": "默认技能组",
			"AgentIds": "user-test@ccc-test",
			"EstablishedTime": "1532448000000",
			"AgentNames": "云呼测试坐席"
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

