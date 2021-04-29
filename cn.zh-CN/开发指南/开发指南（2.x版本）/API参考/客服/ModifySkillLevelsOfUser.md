# ModifySkillLevelsOfUser

调用ModifySkillLevelsOfUser修改坐席的技能等级。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ModifySkillLevelsOfUser&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifySkillLevelsOfUser|系统规定参数。取值：ModifySkillLevelsOfUser。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|SkillLevelList|String|是|\[\{"skillGroupId":"skg-test1@ccc-test","skillLevel":10\},\{"skillGroupId":"skg-test2@ccc-test","skillLevel":10\}\]|待修改技能组ID，技能等级JSON Array。 |
|UserId|String|是|user-test@ccc-test|呼叫中心实例的用户ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|响应参数。 |
|RequestId|String|E49D8B83-A3EC-44D4-A920-578BC3C698AD|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ModifySkillLevelsOfUser
&InstanceId=ccc-test
&SkillLevelList=[{"skillGroupId":"skg-test1@ccc-test","skillLevel":10},{"skillGroupId":"skg-test2@ccc-test","skillLevel":10}]
&UserId=user-test@ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>E49D8B83-A3EC-44D4-A920-578BC3C698AD</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Params>无</Params>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "E49D8B83-A3EC-44D4-A920-578BC3C698AD",
	"Message": "无",
	"HttpStatusCode": "200",
	"Params": "无",
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Parameter.Maximum|The parameter %s must be less than or equal to %s.|参数必须小于或等于系统规定的最大值。|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|
|400|Parameter.Null|The parameter %s may not be null.|该参数不能为null值.|
|403|Permission.User|You have no permission to access user\(s\) %s.|您无权访问这些用户。|
|403|Permission.SkillGroup|You have no permission to access skill group\(s\) %s.|您无权访问这些技能组。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

