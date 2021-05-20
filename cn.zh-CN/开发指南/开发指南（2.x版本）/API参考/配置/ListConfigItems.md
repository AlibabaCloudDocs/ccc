# ListConfigItems

调用接口ListConfigItems获取配置信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListConfigItems&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListConfigItems|系统规定参数。取值：ListConfigItems。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|ObjectId|String|是|ccc-test|配置项信息从属的对象。如果此参数为空则表示处理当前用户相关的配置项，只包括用户这一级的内容。 |
|ObjectType|String|是|INSTANCE|对象的类型。

 -   主账号级别的配置：ALIYUN\_UID
-   实例级别的配置项：INSTANCE
-   技能组级别的配置项：SKILL\_GROUP
-   座席自己的配置项：USER |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Array of ConfigItem| |数据。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|Name|String|test-item|配置项名称。 |
|ObjectId|String|ccc-test|配置项所归属的对象ID。 |
|ObjectType|String|INSTANCE|配置项所归属的配置类型。 |
|Value|String|1|配置项的值。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|参数信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListConfigItems
&InstanceId=ccc-test
&ObjectId=ccc-test
&ObjectType=INSTANCE
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
    <Value>1</Value>
    <ObjectType>INSTANCE</ObjectType>
    <ObjectId>ccc-test</ObjectId>
    <InstanceId>ccc-test</InstanceId>
    <Name>test-item</Name>
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
	"Data": [{
		"Value": "1",
		"ObjectType": "INSTANCE",
		"ObjectId": "ccc-test",
		"InstanceId": "ccc-test",
		"Name": "test-item"
	}],
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|Parameter.Enumeration|The parameter %s must be one of the value of enumeration %s.|该参数必须为系统限定的枚举值之一。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

