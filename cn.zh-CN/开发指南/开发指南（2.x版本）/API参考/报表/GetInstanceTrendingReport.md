# GetInstanceTrendingReport

调用GetInstanceTrendingReport获取实例趋势数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=GetInstanceTrendingReport&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetInstanceTrendingReport|系统规定参数。取值：GetInstanceTrendingReport。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|StartTime|Long|否|1604639129000|开始时间戳，默认是当天开始时间，最早为当前时间往前180天，开始和截止时间间隔不能超过7天。 |
|EndTime|Long|否|1604725528000|截止时间戳，默认是当前时间。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|Inbound|Array of Inbound| |呼入指标。 |
|CallsAbandonedInIVR|Long|0|IVR放弃量，即电话进入IVR流程之后在IVR环节放弃。 |
|CallsAbandonedInQueue|Long|0|队列放弃量，即电话进入技能组之后在排队环节放弃。 |
|CallsAbandonedInRinging|Long|0|振铃放弃量。 |
|CallsHandled|Long|0|座席应答电话数。一通电话分给多个座席，算一通。 |
|CallsQueued|Long|0|进入队列的电话数，如果一个电话多次进队列，算一通。 |
|StatsTime|Long|1604639129000|分段统计的开始时间点，时间戳形式。 |
|TotalCalls|Long|0|总进线量。 |
|Outbound|Array of Outbound| |呼出指标。 |
|CallsAnswered|Long|0|外呼接通量。 |
|StatsTime|Long|1604639129000|分段统计的开始时间点，时间戳形式。 |
|TotalCalls|Long|0|总外呼量。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|943D8EF3-3321-471F-A104-51C96FCA94D6|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetInstanceTrendingReport
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
    <Inbound>
        <CallsAbandonedInRinging>0</CallsAbandonedInRinging>
        <TotalCalls>0</TotalCalls>
        <CallsAbandonedInQueue>0</CallsAbandonedInQueue>
        <CallsQueued>0</CallsQueued>
        <CallsHandled>0</CallsHandled>
        <StatsTime>1604639129000</StatsTime>
        <CallsAbandonedInIVR>0</CallsAbandonedInIVR>
    </Inbound>
    <Outbound>
        <CallsAnswered>0</CallsAnswered>
        <TotalCalls>0</TotalCalls>
        <StatsTime>1604639129000</StatsTime>
    </Outbound>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "943D8EF3-3321-471F-A104-51C96FCA94D6",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": {
		"Inbound": [{
			"CallsAbandonedInRinging": "0",
			"TotalCalls": "0",
			"CallsAbandonedInQueue": "0",
			"CallsQueued": "0",
			"CallsHandled": "0",
			"StatsTime": "1604639129000",
			"CallsAbandonedInIVR": "0"
		}],
		"Outbound": [{
			"CallsAnswered": "0",
			"TotalCalls": "0",
			"StatsTime": "1604639129000"
		}]
	},
	"Code": "OK"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

