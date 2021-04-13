# CreateUser

调用CreateUser创建用户。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=CreateUser&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateUser|系统规定参数。取值：CreateUser。 |
|DisplayName|String|是|云呼测试1|用户的姓名。 |
|Email|String|是|18866668888@163.com|用户电子邮件地址。

 新建成功后会发送邮件，邮件中包含呼叫中心登录地址，以及用户名密码。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|LoginName|String|是|user-test-1|用户登陆名，即RAM用户@符号前的名称。长度在4-32之间，可包含英文字母、数字、英文句点 "."、下划线 "\_"或短划线 "-"。 |
|RoleId|String|是|Agent@ccc-test|用户的角色ID。 |
|WorkMode|String|是|ON\_SITE|工作模式

 -   场内模式，用户在职场办公，通过软电话或者SIP话机接入，也称为正常模式（ON\_SITE）
-   场外模式，用户不在职场办公，通过手机或者其他PSTN话机接听客户来电（OFF\_SITE） |
|Mobile|String|否|138xxxx2114|用户电话号码。 |
|SkillLevelList|String|否|\[\{"skillGroupId":"default@ccc-test","skillLevel":5\}\]|待创建用户所归属的技能组ID以及技能等级。 |
|ResetPassword|Boolean|否|false|是否需要重置密码，默认为false。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|DisplayName|String|云呼测试1|用户的姓名。 |
|Email|String|18866668888@163.com|用户电子邮件地址。 |
|Extension|String|80326034|分机号码。 |
|LoginName|String|user-test-1|用户登陆名。 |
|Mobile|String|138xxxx2114|用户电话号码。 |
|UserId|String|user-test-1@ccc-test|用户ID。 |
|WorkMode|String|ON\_SITE|工作模式。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|响应参数。 |
|RequestId|String|BA03159C-E808-4FF1-B27E-A61B6E888D7F|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateUser
&DisplayName=云呼测试1
&Email=18866668888@163.com
&InstanceId=ccc-test
&LoginName=user-test-1
&RoleId=Agent@ccc-test
&WorkMode=ON_SITE
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>BA03159C-E808-4FF1-B27E-A61B6E888D7F</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Params>无</Params>
<Data>
    <Extension>80326034</Extension>
    <LoginName>user-test-1</LoginName>
    <Email>18866668888@163.com</Email>
    <UserId>user-test-1@ccc-test</UserId>
    <DisplayName>云呼测试1</DisplayName>
    <Mobile>138xxxx2114</Mobile>
    <WorkMode>ON_SITE</WorkMode>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "BA03159C-E808-4FF1-B27E-A61B6E888D7F",
	"Message": "无",
	"HttpStatusCode": "200",
	"Params": "无",
	"Data": {
		"Extension": "80326034",
		"LoginName": "user-test-1",
		"Email": "18866668888@163.com",
		"UserId": "user-test-1@ccc-test",
		"DisplayName": "云呼测试1",
		"Mobile": "138xxxx2114",
		"WorkMode": "ON_SITE"
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|
|400|Parameter.Enumeration|The parameter %s must be one of the value of enumeration %s.|该参数必须为系统限定的枚举值之一。|
|400|Parameter.Maximum|The parameter %s must be less than or equal to %s.|参数必须小于或等于系统规定的最大值。|
|403|Permission.StsToken|You have no permission to access sts token %s.|您无权访问STS Token。|
|404|NotExists.RoleId|Role %s does not exist.|指定的角色不存在。|
|409|AlreadyExists.User|User %s already exists in instance %s.|呼叫中心实例下已存在指定的用户。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

