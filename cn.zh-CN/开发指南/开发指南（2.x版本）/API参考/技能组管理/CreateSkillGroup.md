# CreateSkillGroup

调用CreateSkillGroup创建技能组。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=CreateSkillGroup&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateSkillGroup|系统规定参数。取值：CreateSkillGroup。 |
|DisplayName|String|是|测试技能组|技能组名称，可以为中文。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|Name|String|是|test|技能组Name：SkillGroupId的组成部分，可以包含数字、字母、下划线（\_）、短划线（-），必须以字母开头，长度1-32。SkillGroupId格式：skg-技能组Name@InstanceId 。 |
|Description|String|否|测试|技能组描述。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|Description|String|测试|技能组描述。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|Name|String|test|技能组Name。 |
|SkillGroupId|String|skg-test@ccc-test|技能组ID。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateSkillGroup
&DisplayName=测试技能组
&InstanceId=ccc-test
&Name=test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <Description>测试</Description>
    <InstanceId>ccc-test</InstanceId>
    <SkillGroupId>skg-test@ccc-test</SkillGroupId>
    <Name>test</Name>
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
		"Description": "测试",
		"InstanceId": "ccc-test",
		"SkillGroupId": "skg-test@ccc-test",
		"Name": "test"
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|
|400|Parameter.Format|The format of parameter %s is invalid. %s|该参数的格式不合法。|
|409|AlreadyExists.SkillGroupId|Skill group %s already exists in instance %s.|呼叫中心实例中已经存在指定的技能组。|
|500|InternalService.DB|An internal DB service error occurred. %s|内部数据服务错误。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

