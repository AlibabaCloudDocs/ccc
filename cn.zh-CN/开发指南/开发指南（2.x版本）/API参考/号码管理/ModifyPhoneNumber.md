# ModifyPhoneNumber

调用ModifyPhoneNumber修改号码信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ModifyPhoneNumber&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyPhoneNumber|系统规定参数。取值：ModifyPhoneNumber。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|Number|String|是|010xxxx2134|待修改的呼叫中心号码。 |
|Usage|String|是|Bidirection|号码用途：

 -   Inbound（仅用于呼入）
-   Outbound（仅用于呼出）
-   Bidirection（用于呼入和呼出） |
|ContactFlowId|String|否|78128960-bb00-4ddc-8a82-923a8c5bd22d|号码待绑定的IVR流程ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ModifyPhoneNumber
&InstanceId=ccc-test
&Number=010xxxx2134
&Usage=Bidirection
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
	"Message": "无",
	"HttpStatusCode": "200",
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|404|NotExists.Number|The specified number %s does not exist in instance %s.|呼叫中心实例中不存在指定的号码。|
|400|Parameter.Enumeration|The parameter %s must be one of the value of enumeration %s.|该参数必须为系统限定的枚举值之一。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

