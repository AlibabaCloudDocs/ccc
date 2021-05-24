# ListAgentStateLogs

调用ListAgentStateLogs获取呼叫中心实例中坐席的状态日志。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListAgentStateLogs&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListAgentStateLogs|系统规定参数。取值：ListAgentStateLogs。 |
|AgentId|String|是|user-test@ccc-test|坐席ID，也叫呼叫中心UserId。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|StartTime|Long|否|1620230400000|开始时间戳，默认是当天开始时间，最早为当前日期之前的180天。 |
|EndTime|Long|否|1620273600000|截止时间戳，默认是当前时间，EndTime和StartTime的时间差不能超过1天。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Array of Data| |数据。 |
|Duration|Long|5903871|状态持续时长，单位豪秒。 |
|StartTime|Long|1620259200000|状态开始时间，时间戳，单位毫秒。 |
|State|String|Break|状态码：

 -   ACW（话后处理）
-   Ringing（振铃）
-   Break（小休）
-   Offline（下线）
-   Dialing（拨号）
-   Talking（通话）
-   Ready（准备就绪） |
|StateCode|String|CHECK\_IN\_BREAK|子状态，状态码补充说明。某些坐席状态由State和StateCode共同标识，例如：

 -   监听：

State=Talking，StateCode=Monitoring |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|943D8EF3-3321-471F-A104-51C96FCA94D6|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListAgentStateLogs
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
    <State>Break</State>
    <StateCode>CHECK_IN_BREAK</StateCode>
    <StartTime>1620259200000</StartTime>
    <Duration>5903871</Duration>
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
		"State": "Break",
		"StateCode": "CHECK_IN_BREAK",
		"StartTime": "1620259200000",
		"Duration": "5903871"
	}],
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

