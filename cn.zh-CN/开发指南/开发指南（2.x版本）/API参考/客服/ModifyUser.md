# ModifyUser

调用ModifyUser修改用户信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ModifyUser&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyUser|系统规定参数。取值：ModifyUser。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|UserId|String|是|user-test@ccc-test|用户ID。 |
|WorkMode|String|是|ON\_SITE|工作模式。包括：

 -   ON\_SITE（场内模式，用户在职场办公，通过软电话或者SIP话机接入，也称为正常模式）
-   OFF\_SITE（场外模式，用户不在职场办公，通过手机或者其他PSTN话机接听客户来电） |
|Mobile|String|否|138xxxx2114|用户电话号码。 |
|RoleId|String|否|Admin@ccc-test|用户的角色ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|String|无|数据。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|响应参数。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ModifyUser
&InstanceId=ccc-test
&UserId=user-test@ccc-test
&WorkMode=ON_SITE
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Params>无</Params>
<Data>无</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
	"Message": "无",
	"HttpStatusCode": "200",
	"Params": "无",
	"Data": "无",
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Parameter.Enumeration|The parameter %s must be one of the value of enumeration %s.|该参数必须为系统限定的枚举值之一。|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|
|403|Permission.Common|You have no permission to access. %s|您无权进行访问。|
|403|Permission.SkillGroup|You have no permission to access skill group\(s\) %s.|您无权访问这些技能组。|
|404|NotExists.RoleId|Role %s does not exist.|指定的角色不存在。|
|500|InternalService.Common|An internal service error occurred. %s|内部服务错误。|
|500|InternalService.DB|An internal DB service error occurred. %s|内部数据服务错误。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

