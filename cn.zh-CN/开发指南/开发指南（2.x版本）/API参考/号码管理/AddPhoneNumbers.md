# AddPhoneNumbers

调用AddPhoneNumber新增号码。

将从云呼控制台购买的电话号码绑定到呼叫中心实例中，并且可以和IVR流程进行绑定。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=AddPhoneNumbers&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddPhoneNumbers|系统规定参数。取值：AddPhoneNumbers。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|Usage|String|是|Bidirection|该电话号码的用途。取值：

 -   呼入（Inbound）
-   呼出（Outbound）
-   同时用于呼入和呼出（Bidirection）

 **说明：** 如果传入号码为400号码，该值只能传入Inbound |
|ContactFlowId|String|否|dDMD\_0mif4hv|和电话号码绑定的联系流ID。 |
|NumberList|String|否|\["0100xxxx008", "0100xxxx009"\]|号码列表。 |
|NumberGroupId|String|否|2cb77c29-5f60-4b90-b21e-9d2ba9833f14|号码分组ID。通过ListCorpNumberGroups获取。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|List|无|数据。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=AddPhoneNumbers
&ContactFlowId=dDMD_0mif4hv
&InstanceId=ccc-test
&NumberGroupId=2cb77c29-5f60-4b90-b21e-9d2ba9833f14
&NumberList=["0100xxxx008", "0100xxxx009"]
&Usage=Bidirection
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>无</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": "无",
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|Parameter.Enumeration|The parameter %s must be one of the value of enumeration %s.|该参数必须为系统限定的枚举值之一。|
|400|Parameter.Maximum|The parameter %s must be less than or equal to %s.|参数必须小于或等于系统规定的最大值。|
|400|Parameter.Minimum|The parameter %s must be greater than or equal to %s.|参数必须大于或等于系统规定的最小值。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

