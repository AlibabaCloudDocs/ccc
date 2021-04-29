# RemovePersonalNumbersFromUser

调用RemovePersonalNumbersFromUser移除用户的个人外呼号码。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=RemovePersonalNumbersFromUser&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemovePersonalNumbersFromUser|系统规定参数。取值：RemovePersonalNumbersFromUser。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|NumberList|String|是|\["0100xxxx008", "0100xxxx009"\]|待移除的个人外呼号码列表，通过调用 ListPersonalNumbersOfUser 时，isMember参数传入true来获取已绑定的号码。 |
|UserId|String|是|user-test@ccc-test|呼叫中心实例的用户ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|BA03159C-E808-4FF1-B27E-A61B6E888D7F|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=RemovePersonalNumbersFromUser
&InstanceId=ccc-test
&NumberList=["0100xxxx008", "0100xxxx009"]
&UserId=user-test@ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>BA03159C-E808-4FF1-B27E-A61B6E888D7F</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "BA03159C-E808-4FF1-B27E-A61B6E888D7F",
	"Message": "无",
	"HttpStatusCode": "200",
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|Parameter.Maximum|The parameter %s must be less than or equal to %s.|参数必须小于或等于系统规定的最大值。|
|400|Parameter.Minimum|The parameter %s must be greater than or equal to %s.|参数必须大于或等于系统规定的最小值。|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|
|400|Parameter.Empty|The parameter %s may not be null or empty.|该参数不能为null值或为空字符串。|
|400|Parameter.Null|The parameter %s may not be null.|该参数不能为null值.|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

