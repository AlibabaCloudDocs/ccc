# ListPersonalNumbersOfUser

调用ListPersonalNumbersOfUser查看用户的个人外呼号码，也可反向查看可作为个人外呼号码的号码列表。

注意：如果号码已绑定了技能组，则不会出现在可作为个人外呼号码的号码列表中。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListPersonalNumbersOfUser&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListPersonalNumbersOfUser|系统规定参数。取值：ListPersonalNumbersOfUser。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|IsMember|Boolean|是|true|是否和坐席关联。若为false，则查看可作为外呼号码的号码列表，作为 AddPersonalNumbersToUser 的号码来源。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|10|分页大小，范围1-100。 |
|UserId|String|是|user-test@ccc-test|呼叫中心实例的用户ID。 |
|SearchPattern|String|否|083|号码查找pattern，可以基于此参数模糊查找。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of PhoneNumber| |号码列表。 |
|Active|Boolean|true|号码是否可用。 |
|City|String|乐山|号码归属地市。 |
|ContactFlowId|String|a3fb6c62-9b49-4942-ae5b-cf2abd4123ek|该电话号码所关联的联系流IVR ID。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|Number|String|083xxxx0011|号码。 |
|Province|String|四川|号码归属地省。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|10|分页大小。 |
|TotalCount|Integer|1|总条目数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListPersonalNumbersOfUser
&InstanceId=ccc-test
&IsMember=true
&PageNumber=1
&PageSize=10
&UserId=user-test@ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <TotalCount>1</TotalCount>
    <PageSize>10</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <Active>true</Active>
        <Number>083xxxx0011</Number>
        <InstanceId>ccc-test</InstanceId>
        <ContactFlowId>a3fb6c62-9b49-4942-ae5b-cf2abd4123ek</ContactFlowId>
        <City>乐山</City>
        <Province>四川</Province>
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
		"TotalCount": "1",
		"PageSize": "10",
		"PageNumber": "1",
		"List": [{
			"Active": "true",
			"Number": "083xxxx0011",
			"InstanceId": "ccc-test",
			"ContactFlowId": "a3fb6c62-9b49-4942-ae5b-cf2abd4123ek",
			"City": "乐山",
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
|400|Parameter.Maximum|The parameter %s must be less than or equal to %s.|参数必须小于或等于系统规定的最大值。|
|400|Parameter.Minimum|The parameter %s must be greater than or equal to %s.|参数必须大于或等于系统规定的最小值。|
|400|Parameter.Empty|The parameter %s may not be null or empty.|该参数不能为null值或为空字符串。|
|400|Parameter.Null|The parameter %s may not be null.|该参数不能为null值.|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

