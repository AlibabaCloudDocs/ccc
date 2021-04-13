# ListSkillGroups

调用ListSkillGroups获取呼叫中心实例的技能组。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListSkillGroups&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListSkillGroups|系统规定参数。取值：ListSkillGroups。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|10|分页大小，范围1-100。 |
|SearchPattern|String|是|测试技能组|根据技能组名称或展示名模糊查询。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of SkillGroup| |技能组列表。 |
|Description|String|测试|描述。 |
|DisplayName|String|测试技能组|技能组展示名。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|PhoneNumberCount|Integer|1|技能组关联的号码数量。 |
|SkillGroupId|String|test@ccc-test|技能组ID。 |
|SkillGroupName|String|test|技能组名称。 |
|UserCount|Integer|2|技能组关联的坐席数量。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|10|分页大小。 |
|TotalCount|Integer|1|总条目数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|BA03159C-E808-4FF1-B27E-A61B6E888D7F|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListSkillGroups
&InstanceId=ccc-test
&PageNumber=1
&PageSize=10
&SearchPattern=defalut
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>BA03159C-E808-4FF1-B27E-A61B6E888D7F</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <TotalCount>1</TotalCount>
    <PageSize>10</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <SkillGroupName>test</SkillGroupName>
        <Description>测试</Description>
        <PhoneNumberCount>1</PhoneNumberCount>
        <InstanceId>ccc-test</InstanceId>
        <UserCount>2</UserCount>
        <DisplayName>测试技能组</DisplayName>
        <SkillGroupId>test@ccc-test</SkillGroupId>
    </List>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "BA03159C-E808-4FF1-B27E-A61B6E888D7F",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": {
		"TotalCount": "1",
		"PageSize": "10",
		"PageNumber": "1",
		"List": [{
			"SkillGroupName": "test",
			"Description": "测试",
			"PhoneNumberCount": "1",
			"InstanceId": "ccc-test",
			"UserCount": "2",
			"DisplayName": "测试技能组",
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
|400|Parameter.Maximum|The parameter %s must be less than or equal to %s.|参数必须小于或等于系统规定的最大值。|
|400|Parameter.Minimum|The parameter %s must be greater than or equal to %s.|参数必须大于或等于系统规定的最小值。|
|400|Parameter.Null|The parameter %s may not be null.|该参数不能为null值.|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

