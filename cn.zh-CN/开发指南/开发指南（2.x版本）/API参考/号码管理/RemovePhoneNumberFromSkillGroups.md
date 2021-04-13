# RemovePhoneNumberFromSkillGroups

调用RemovePhoneNumberFromSkillGroups解绑一个号码与多个技能组。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=RemovePhoneNumberFromSkillGroups&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemovePhoneNumberFromSkillGroups|系统规定参数。取值：RemovePhoneNumberFromSkillGroups。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|Number|String|是|010xxxx3008|解绑号码。 |
|SkillGroupIdList|String|是|\["test1@ccc-test","test2@ccc-test"\]|解绑技能组ID列表。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=RemovePhoneNumberFromSkillGroups
&InstanceId=ccc-test
&Number=0100xxxx008
&SkillGroupIdList=["test1@ccc-test","test2@ccc-test"]
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
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
|400|Parameter.Format|The format of parameter %s is invalid. %s|该参数的格式不合法。|
|400|Parameter.Invalid|The parameter %s is invalid. %s.|该参数无效。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

