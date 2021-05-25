# ListRecentCallDetailRecords

调用ListRecentCallDetailRecords获取呼叫中心当前坐席的最近通话记录。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListRecentCallDetailRecords&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListRecentCallDetailRecords|系统规定参数。取值：ListRecentCallDetailRecords。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|页码，范围1-100。 |
|PageSize|Integer|是|10|每页大小，范围1-100。 |
|StartTime|Long|否|1604638129000|开始时间戳，默认是当天开始时间， 最早为当前时间往前180天。 |
|EndTime|Long|否|1604639129000|截止时间戳，默认是当前时间。 |
|Criteria|String|否|\{"phoneNumber":"139xxxx1234"\}|搜索条件。JSON格式：

 \{

 "phoneNumber": "xxxx", // 主叫或被叫

 "callingNumber": "xxxx", // 主叫

 "calledNumber": "xxx" // 被叫

 \} |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of CallDetailRecord| |通话记录列表。 |
|AgentIds|String|user-test@ccc-test|坐席ID列表，多个值用逗号分隔。 |
|CallDuration|String|16|通话时长，单位秒 |
|CalledNumber|String|133xxxx2315|被叫号码。 |
|CallingNumber|String|053xxxx3128|主叫号码。 |
|ContactDisposition|String|Success|电话结束原因。

 Success\(正常\)，NoAnswer\(未接通\)，AbandonedInContactFlow\(IVR中放弃\)，AbandonedInQueue\(排队放弃\)，AbandonedRing\(振铃放弃\)，QueueOverflow\(排队超时\)，OneStepTransfer\(转外线\)。 |
|ContactId|String|job-76604722428454704|通话ID。 |
|ContactType|String|Outbound|通话类型。取值：INBOUND（呼入），OUTBOND（呼出）。 |
|Duration|Long|16|通话持续时间，单位为秒。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|SkillGroupIds|String|skg-default@ccc-test|参与通话的座席所属的技能组，多个技能组以逗号分隔。 |
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
http(s)://[Endpoint]/?Action=ListRecentCallDetailRecords
&InstanceId=ccc-test
&PageNumber=1
&PageSize=10
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
        <AgentIds>user-test@ccc-test</AgentIds>
        <Duration>16</Duration>
        <ContactId>job-76604722428454704</ContactId>
        <CallDuration>16</CallDuration>
        <CallingNumber>053xxxx3128</CallingNumber>
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
			"AgentIds": "user-test@ccc-test",
			"Duration": "16",
			"ContactId": "job-76604722428454704",
			"CallDuration": "16",
			"CallingNumber": "053xxxx3128"
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

