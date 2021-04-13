# GetNumberLocation

调用接口GetNumberLocation 获取号码归属地信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=GetNumberLocation&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetNumberLocation|系统规定参数。取值：GetNumberLocation。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|Number|String|是|13121210000|待查询号码。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|City|String|北京|号码归属地市。 |
|Number|String|13121210000|电话号码。 |
|Province|String|北京|号码归属地省。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|57BD0C70-1E91-4655-A1B1-31E5D2DAA4BD|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetNumberLocation
&InstanceId=ccc-test
&Number=13121210000
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>57BD0C70-1E91-4655-A1B1-31E5D2DAA4BD</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <Number>13121210000</Number>
    <City>北京</City>
    <Province>北京</Province>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "57BD0C70-1E91-4655-A1B1-31E5D2DAA4BD",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": {
		"Number": "13121210000",
		"City": "北京",
		"Province": "北京"
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

