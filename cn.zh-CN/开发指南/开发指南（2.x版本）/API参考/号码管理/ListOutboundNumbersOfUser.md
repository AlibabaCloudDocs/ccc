# ListOutboundNumbersOfUser

调用ListOutboundNumbersOfUser获取坐席可用外呼号码。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListOutboundNumbersOfUser&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListOutboundNumbersOfUser|系统规定参数。取值：ListOutboundNumbersOfUser。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号。 |
|PageSize|Integer|是|10|分页大小。 |
|UserId|String|是|user-test@ccc-test|呼叫中心实例的用户ID，实例内唯一。 |
|SkillGroupIdList|String|否|\["skg-default@ccc-test","skg-default2@ccc-test"\]|签入技能组ID列表，如果为空，则查询用户归属的所有技能组的外呼号码。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of PhoneNumber| |号码列表。 |
|City|String|乐山|归属市。 |
|Number|String|083xxxx0019|号码。 |
|Province|String|四川|归属省。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|10|分页大小。 |
|TotalCount|Integer|1|总数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListOutboundNumbersOfUser
&InstanceId=ccc-test
&PageNumber=1
&PageSize=10
&UserId=user-test@ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<TotalCount>1</TotalCount>
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<PageSize>10</PageSize>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <TotalCount>1</TotalCount>
    <PageSize>10</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <City>乐山</City>
        <Number>083xxxx0019</Number>
        <Province>四川</Province>
    </List>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"TotalCount": "1",
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
	"PageSize": "10",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": {
		"TotalCount": "1",
		"PageSize": "10",
		"PageNumber": "1",
		"List": [{
			"City": "乐山",
			"Number": "083xxxx0019",
			"Province": "四川"
		}]
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|404|NotExists.UserId|The user %s does not exist in instance %s.|呼叫中心实例中不存在指定的用户。|
|400|Parameter.Minimum|The parameter %s must be greater than or equal to %s.|参数必须大于或等于系统规定的最小值。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

