# AddSkillGroupsToUser

调用AddSkillGroupsToUser绑定一个用户与多个技能组。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=AddSkillGroupsToUser&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddSkillGroupsToUser|系统规定参数。取值：AddSkillGroupsToUser。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|SkillLevelList|String|是|\[\{"skillGroupId":"test1@ccc-test","skillLevel":5\},\{"skillGroupId":"test2@ccc-test","skillLevel":5\}\]|技能组ID和技能等级列表。 |
|UserId|String|是|user-test@ccc-test|解绑的用户ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|响应参数。 |
|RequestId|String|BA7F9545-8312-4190-9BD0-63144B3F1ACC|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=AddSkillGroupsToUser
&InstanceId=ccc-test
&SkillLevelList=[{"skillGroupId":"test1@ccc-test","skillLevel":5},{"skillGroupId":"test2@ccc-test","skillLevel":5}]
&UserId=user-test@ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>BA7F9545-8312-4190-9BD0-63144B3F1ACC</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Params>无</Params>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "BA7F9545-8312-4190-9BD0-63144B3F1ACC",
	"Message": "无",
	"HttpStatusCode": "200",
	"Params": "无",
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|Parameter.Maximum|The parameter %s must be less than or equal to %s.|参数必须小于或等于系统规定的最大值。|
|400|Parameter.Minimum|The parameter %s must be greater than or equal to %s.|参数必须大于或等于系统规定的最小值。|
|404|NotExists.SkillGroupId|The skill group ID %s does not exist in instance %s.|呼叫中心实例中不存在指定的技能组ID。|
|404|NotExists.UserId|The user %s does not exist in instance %s.|呼叫中心实例中不存在指定的用户。|
|403|Permission.SkillGroup|You have no permission to access skill group\(s\) %s.|您无权访问这些技能组。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

