# ListUsers

调用ListUsers获取呼叫中心实例下的用户。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListUsers&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListUsers|系统规定参数。取值：ListUsers。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|10|分页大小，范围1-100。 |
|SearchPattern|String|否|测试|根据用户的登录名（用户名）或展示名（姓名）模糊查询。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of UserDetail| |用户列表。 |
|DisplayName|String|测试用户|用户的展示名（姓名）。 |
|Email|String|18866668888@163.com|电子邮件地址。 |
|LoginName|String|user-test|用户的登陆名（用户名）。 |
|Mobile|String|138xxxx2114|用户电话号码。 |
|PersonalOutboundNumberList|Array of PhoneNumber| |个人外呼号码列表。 |
|Active|Boolean|true|是否可用。 |
|City|String|乐山|号码归属地市。 |
|Number|String|083xxxx0011|号码。 |
|Province|String|四川|号码归属地省。 |
|Usage|String|Bidirection|号码用途。 |
|RoleId|String|Admin@ccc-test|用户的角色ID。 |
|RoleName|String|Admin|角色名称。 |
|SkillLevelList|Array of UserSkillLevel| |坐席关联的技能组列表。 |
|SkillGroupId|String|skg-test@ccc-test|技能组ID。 |
|SkillGroupName|String|skg-test|技能组名称。 |
|SkillLevel|Integer|5|技能等级。 |
|UserId|String|user-test@ccc-test|用户ID。 |
|WorkMode|String|ON\_SITE|工作模式。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|10|分页大小。 |
|TotalCount|Integer|1|总条目数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|响应参数。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListUsers
&InstanceId=ccc-test
&PageNumber=1
&PageSize=10
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
    <TotalCount>1</TotalCount>
    <PageSize>10</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <LoginName>user-test</LoginName>
        <RoleName>Admin</RoleName>
        <Email>18866668888@163.com</Email>
        <UserId>user-test@ccc-test</UserId>
        <DisplayName>测试用户</DisplayName>
        <RoleId>Admin@ccc-test</RoleId>
        <Mobile>138xxxx2114</Mobile>
        <WorkMode>ON_SITE</WorkMode>
        <PersonalOutboundNumberList>
            <Usage>Bidirection</Usage>
            <Active>true</Active>
            <Number>083xxxx0011</Number>
            <City>乐山</City>
            <Province>四川</Province>
        </PersonalOutboundNumberList>
        <SkillLevelList>
            <SkillLevel>5</SkillLevel>
            <SkillGroupName>skg-test</SkillGroupName>
            <SkillGroupId>skg-test@ccc-test</SkillGroupId>
        </SkillLevelList>
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
	"Params": "无",
	"Data": {
		"TotalCount": "1",
		"PageSize": "10",
		"PageNumber": "1",
		"List": [{
			"LoginName": "user-test",
			"RoleName": "Admin",
			"Email": "18866668888@163.com",
			"UserId": "user-test@ccc-test",
			"DisplayName": "测试用户",
			"RoleId": "Admin@ccc-test",
			"Mobile": "138xxxx2114",
			"WorkMode": "ON_SITE",
			"PersonalOutboundNumberList": [{
				"Usage": "Bidirection",
				"Active": "true",
				"Number": "083xxxx0011",
				"City": "乐山",
				"Province": "四川"
			}],
			"SkillLevelList": [{
				"SkillLevel": "5",
				"SkillGroupName": "skg-test",
				"SkillGroupId": "skg-test@ccc-test"
			}]
		}]
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Parameter.Maximum|The parameter %s must be less than or equal to %s.|参数必须小于或等于系统规定的最大值。|
|400|Parameter.Minimum|The parameter %s must be greater than or equal to %s.|参数必须大于或等于系统规定的最小值。|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|Parameter.Null|The parameter %s may not be null.|该参数不能为null值.|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

