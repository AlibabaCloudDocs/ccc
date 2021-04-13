# ListRoles

调用ListRoles获取实例下的角色列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListRoles&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListRoles|系统规定参数。取值：ListRoles。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Array of Role| |数据。 |
|Name|String|Admin|角色名称。包括：

 -   Agent（坐席）
-   Manager（技能组组长）
-   Admin（管理员） |
|RoleId|String|Admin@ccc-test|角色ID。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListRoles
&InstanceId=ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <RoleId>Admin@ccc-test</RoleId>
    <Name>Admin</Name>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": [{
		"RoleId": "Admin@ccc-test",
		"Name": "Admin"
	}],
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Parameter.Invalid|The parameter %s is invalid. %s.|该参数无效。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

