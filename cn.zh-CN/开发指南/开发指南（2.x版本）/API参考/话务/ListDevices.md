# ListDevices

调用ListDevices获取设备列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListDevices&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListDevices|系统规定参数。取值：ListDevices。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|UserId|String|是|user-test@ccc-test|呼叫中心实例的用户ID，实例内唯一。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Array of Device| |数据。 |
|CallId|String|d7b818c3-8d3a-732f-bc9e-1782wa16e455|设备注册信令的Call ID。 |
|Contact|String|sip:80326034@33.89.9.338:64189;transport=tcp;registering\_acc=18\_134\_23\_4|设备地址信息。 |
|DeviceId|String|ACC-YUNBS-1.0.10-b18bp53c1736c2914176a801ei90|如果座席注册了SIP话机，则此参数是SIP话机设备的设备ID，否则为空。 |
|Expires|Long|1609118499750|过期时间。 |
|Extension|String|80326034|分机号码。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|UserId|String|user-test@ccc-test|呼叫中心实例的用户ID。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|响应参数。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListDevices
&InstanceId=ccc-test
&UserId=user-test@ccc-test
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
    <Extension>80326034</Extension>
    <InstanceId>ccc-test</InstanceId>
    <UserId>user-test@ccc-test</UserId>
    <DeviceId>BS-2020-09-01-11:11:11.888-192_168_12_123</DeviceId>
    <CallId>561d53be3fa11c4700a40ce8592ef880@0:0:0:0:0:0:0:0</CallId>
    <Expires>1609118499750</Expires>
    <Contact>sip:80326034@33.89.9.338:64189;transport=tcp;registering_acc=18_134_23_4</Contact>
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
		"Extension": "80326034",
		"InstanceId": "ccc-test",
		"UserId": "user-test@ccc-test",
		"DeviceId": "BS-2020-09-01-11:11:11.888-192_168_12_123",
		"CallId": "561d53be3fa11c4700a40ce8592ef880@0:0:0:0:0:0:0:0",
		"Expires": "1609118499750",
		"Contact": "sip:80326034@33.89.9.338:64189;transport=tcp;registering_acc=18_134_23_4"
	}],
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

