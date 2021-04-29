# ListSkillLevelsOfUser

调用ListSkillLevelsOfUser获取坐席所归属的技能组列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListSkillLevelsOfUser&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListSkillLevelsOfUser|系统规定参数。取值：ListSkillLevelsOfUser。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号。 |
|PageSize|Integer|是|10|分页大小，最大数量为100。 |
|UserId|String|是|user-test@ccc-test|呼叫中心实例的用户ID，实例内唯一。 |
|IsMember|Boolean|否|true|是否与用户关联，默认值为true。 |
|SearchPattern|String|否|skillgroup-test|查询匹配，可根据技能组名称进行查询 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of UserSkillLevel| |技能组列表。 |
|SkillGroupId|String|test@ccc-test|技能组ID。 |
|SkillGroupName|String|测试技能组|技能组名称。 |
|SkillLevel|String|5|技能等级。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|10|分页大小。 |
|TotalCount|Integer|1|总数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListSkillLevelsOfUser
&InstanceId=ccc-test
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
        <SkillLevel>5</SkillLevel>
        <SkillGroupName>测试技能组</SkillGroupName>
        <SkillGroupId>test@ccc-test</SkillGroupId>
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
			"SkillLevel": "5",
			"SkillGroupName": "测试技能组",
			"SkillGroupId": "test@ccc-test"
		}]
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|404|NotExists.UserId|The user %s does not exist in instance %s.|呼叫中心实例中不存在指定的用户。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

