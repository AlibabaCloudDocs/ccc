# AssignUsers

调用AssignUsers将RAM中的一组用户添加到一个呼叫中心实例中。

查看RAM用户：https://ram.console.aliyun.com/users

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=AssignUsers&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AssignUsers|系统规定参数。取值：AssignUsers。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|RamIdList|String|是|\["280364111234567890","292343011234567890"\]|待添加到呼叫中心实例的RAM用户ID。 |
|RoleId|String|是|Manager@ccc-test|分配的角色ID。 |
|WorkMode|String|是|ON\_SITE|工作模式：

 -   场内模式，用户在职场办公，通过软电话或者SIP话机接入，也称为正常模式（ON\_SITE）
-   场外模式，用户不在职场办公，通过手机或者其他PSTN话机接听客户来电（OFF\_SITE） |
|SkillLevelList|String|否|\[\{"skillGroupId":"default@ccc-test","skillLevel":5\}\]|待导入用户所归属的技能组ID以及技能等级。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|String|1ca2b084-6f0a-454b-9851-29768a9a5832|数据，内容同WorkflowId。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |
|Sync|String|无|废弃。 |
|WorkflowId|String|1ca2b084-6f0a-454b-9851-29768a9a5832|工作流ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=AssignUsers
&InstanceId=ccc-test
&RamIdList=["280364111234567890","292343011234567890"]
&RoleId=Manager@ccc-test
&WorkMode=ON_SITE
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>1ca2b084-6f0a-454b-9851-29768a9a5832</Data>
<WorkflowId>1ca2b084-6f0a-454b-9851-29768a9a5832</WorkflowId>
<Sync>无</Sync>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": "1ca2b084-6f0a-454b-9851-29768a9a5832",
	"WorkflowId": "1ca2b084-6f0a-454b-9851-29768a9a5832",
	"Sync": "无",
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Parameter.Enumeration|The parameter %s must be one of the value of enumeration %s.|该参数必须为系统限定的枚举值之一。|
|400|Parameter.Maximum|The parameter %s must be less than or equal to %s.|参数必须小于或等于系统规定的最大值。|
|400|Parameter.Minimum|The parameter %s must be greater than or equal to %s.|参数必须大于或等于系统规定的最小值。|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|
|400|Parameter.Empty|The parameter %s may not be null or empty.|该参数不能为null值或为空字符串。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

