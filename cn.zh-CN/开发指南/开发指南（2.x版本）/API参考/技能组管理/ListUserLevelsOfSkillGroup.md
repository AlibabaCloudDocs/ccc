# ListUserLevelsOfSkillGroup

调用ListUserLevelsOfSkillGroup查看指定技能组所绑定的用户及技能等级列表。也可反向查看不属于该技能组的用户信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListUserLevelsOfSkillGroup&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListUserLevelsOfSkillGroup|系统规定参数。取值：ListUserLevelsOfSkillGroup。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|IsMember|Boolean|是|true|待查询用户是否与该技能组绑定。若为false，则查看未与该技能组绑定的用户信息。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|10|分页大小，范围1-100。 |
|SkillGroupId|String|是|skg-default@ccc-test|技能组ID。 |
|SearchPattern|String|否|测试坐席|根据坐席的用户名或姓名模糊查询。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of UserSkillLevel| |用户列表。 |
|DisplayName|String|测试坐席|用户姓名。 |
|LoginName|String|user-test|用户登录名。 |
|RoleId|String|Admin@ccc-test|用户的角色ID。 |
|RoleName|String|Admin|角色名称。

 -   管理员（Admin）
-   技能组组长（Manager）
-   坐席（Agent） |
|SkillGroupId|String|skg-default@ccc-test|技能组ID。 |
|SkillGroupName|String|Default|技能组名称。 |
|SkillLevel|Integer|5|用户技能等级。 |
|UserId|String|user-test@ccc-test|用户ID。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|10|分页大小。 |
|TotalCount|Integer|1|用户总数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListUserLevelsOfSkillGroup
&InstanceId=ccc-test
&IsMember=true
&PageNumber=1
&PageSize=10
&SkillGroupId=skg-default@ccc-test
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
        <LoginName>user-test</LoginName>
        <RoleName>Admin</RoleName>
        <SkillLevel>5</SkillLevel>
        <SkillGroupName>Default</SkillGroupName>
        <UserId>user-test@ccc-test</UserId>
        <DisplayName>测试坐席</DisplayName>
        <SkillGroupId>skg-default@ccc-test</SkillGroupId>
        <RoleId>Admin@ccc-test</RoleId>
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
			"LoginName": "user-test",
			"RoleName": "Admin",
			"SkillLevel": "5",
			"SkillGroupName": "Default",
			"UserId": "user-test@ccc-test",
			"DisplayName": "测试坐席",
			"SkillGroupId": "skg-default@ccc-test",
			"RoleId": "Admin@ccc-test"
		}]
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|404|NotExists.SkillGroupId|The skill group ID %s does not exist in instance %s.|呼叫中心实例中不存在指定的技能组ID。|
|400|Parameter.Maximum|The parameter %s must be less than or equal to %s.|参数必须小于或等于系统规定的最大值。|
|400|Parameter.Minimum|The parameter %s must be greater than or equal to %s.|参数必须大于或等于系统规定的最小值。|
|400|Parameter.Empty|The parameter %s may not be null or empty.|该参数不能为null值或为空字符串。|
|400|Parameter.Null|The parameter %s may not be null.|该参数不能为null值.|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

