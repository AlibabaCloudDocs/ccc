# GetUser

调用GetUser根据用户ID或坐席分机号获取用户信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=GetUser&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetUser|系统规定参数。取值：GetUser。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|UserId|String|否|user-test@ccc-test|呼叫中心实例的用户ID。作为入参与Extension坐席分机号二选一。 |
|Extension|String|否|80035691|坐席分机号。作为入参与UserId二选一。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|DisplayName|String|测试用户|姓名。 |
|Email|String|user-test@aliyun-cc.com|电子邮件地址。 |
|Extension|String|80035691|坐席分机号。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|LoginName|String|user-test|用户名。 |
|Mobile|String|139xxxx1234|手机号码。 |
|RoleId|String|Admin@ccc-test|角色ID。 |
|RoleName|String|Admin|角色名称。 |
|UserId|String|user-test@ccc-test|用户ID。 |
|WorkMode|String|ON\_SITE|工作模式。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|响应参数。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetUser
&InstanceId=ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Params>无</Params>
<Data>
    <Extension>80035691</Extension>
    <LoginName>user-test</LoginName>
    <RoleName>Admin</RoleName>
    <Email>user-test@aliyun-cc.com</Email>
    <InstanceId>ccc-test</InstanceId>
    <UserId>user-test@ccc-test</UserId>
    <DisplayName>测试用户</DisplayName>
    <RoleId>Admin@ccc-test</RoleId>
    <Mobile>139xxxx1234</Mobile>
    <WorkMode>ON_SITE</WorkMode>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
	"Message": "无",
	"HttpStatusCode": "200",
	"Params": "无",
	"Data": {
		"Extension": "80035691",
		"LoginName": "user-test",
		"RoleName": "Admin",
		"Email": "user-test@aliyun-cc.com",
		"InstanceId": "ccc-test",
		"UserId": "user-test@ccc-test",
		"DisplayName": "测试用户",
		"RoleId": "Admin@ccc-test",
		"Mobile": "139xxxx1234",
		"WorkMode": "ON_SITE"
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

